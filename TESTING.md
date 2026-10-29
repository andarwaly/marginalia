# Laptop tests

Tests that need a real harness or a residential IP. Run them in this order; stop at the first
failure in A, because the rest depend on it. Record each result in the table at the end, with
the harness and date. Use the "Developing Taste" article (https://emilkowal.ski/ui/developing-taste)
unless a test says otherwise.

Harnesses: **CC** Claude Code, **CX** Codex, **CW** Cowork.

## A. Call by name (run on CC, CX and CW)

1. Install the whole repo (`npx skills add andarwaly/marginalia`, or the plugin). List the
   skills; expect twelve.
2. Run `/ingest https://emilkowal.ski/ui/developing-taste`.
   - Pass: `clip-article` runs, then the agent shows topic labels and asks the two opening
     questions. No quotes shown.
3. Answer one point with a hedge ("something about practice, I think?").
   - Pass: the agent calls `feynman-technique` by name and asks one plain-language question.
   - Watch for: Codex opening the SKILL.md path instead of invoking a skill. Note which
     happened; either is acceptable if the interview works.
4. Give a confident, correct restatement; then a blank answer ("no idea").
   - Pass: `verification-technique`, then `guided-reading-technique` with no choice offered.
5. Reach a confirmed statement.
   - Pass: the technique's standalone close ("say it in chat and stop") does not appear;
     ingest moves to the next point.
6. Say "done".
   - Pass: density check, main-idea question and closing question run once; the notes follow
     in fenced blocks; Implications hold only your words.

## B. Flags and routing

7. `/ingest` works with `disable-model-invocation: true` (CC, CW). Fail: "unknown skill".
   Fallback: make it a model-invoked skill whose description says it runs only when the user
   invokes it.
8. Say "summarize this article: <URL>" with no slash. Pass: `ingest` does not run (CC, CW);
   on CX, the same with `agents/openai.yaml` in place.
9. Say "explain this simply", "challenge my idea", "ground me on this". Pass: no skill from
   this repo runs. Note any collision with your own `grounding`, `grilling` or `ground-me`.
10. Type `/feynman-technique` and name a topic. Pass: it runs on its own and ends with the
    statement in chat and no notes.

## C. Install shapes

11. Install only `ingest` (one folder). Run `/ingest`. Pass: it stops and says to install the
    full marginalia set. Fail: it improvises an interview.
12. Confirm which skills folder each harness reads, and the file Codex reads for `policy`
    (`agents/openai.yaml`).
13. Confirm the plugin manifest paths load on CC and CX.

## D. Clips (residential IP)

14. `clip-youtube` on https://www.youtube.com/watch?v=CBQtlMcXPFI. Pass: the API route works;
    the file has timestamped lines; the header is right. Check `is_generated`, `start` and
    `text` against the real response and fix the skill if they differ.
15. `clip-article` on the Medium URL
    (https://uxdesign.cc/the-case-for-code-in-digital-product-design-4c3596b55f22).
    Note whether Defuddle works from your IP.
16. `clip-article` on the Substack URL
    (https://nathanacurtis.substack.com/p/code-only-props-in-figma). Pass: author, date
    `YYYY-MM-DD`.
17. With Firecrawl disabled, break the route on purpose. Pass: one-line failure and a request
    to paste from the browser clipper.
18. Note the temp folder each harness gives (`${TMPDIR:-/tmp}/marginalia/`).

## E. Cloud (CC cloud, CX cloud, CW)

19. Setup script installs `defuddle` and `youtube-transcript-api`; the network policy allows
    the hosts in the README. Run test 2.
20. Confirm whether the Firecrawl plugin is available in each cloud harness.
21. Confirm `youtube-transcript-api` is blocked from the cloud IP and the Firecrawl route
    covers it.

## F. End to end

22. Ingest "Developing Taste" to notes. `/ideate` a thought from it, with the notes pasted.
    Then `/define taste`. Pass: the notes pass the checks in each skill's `evals/README.md`.

## G. Running the evals (scripted user)

The cases live in each skill's `evals/README.md` and are judged by behavior. Run them as a
scripted conversation in a throwaway vault, where the skills are project-local (no install).

**Setup**

1. `mkdir -p w/vault/.obsidian w/vault/.claude/skills && cp -R skills/. w/vault/.claude/skills/`
2. `npm install -g defuddle` (0.14.0 or later). Headless runs may block writes to `/tmp`, so
   the driver points `TMPDIR` at a folder it is allowed to use.
3. Save this as `w/run.sh` and `chmod +x` it. `run.sh 1 "<prompt>"` starts a session,
   `run.sh N "<prompt>"` resumes it. Each turn leaves `logs/N.prompt` and `logs/N.jsonl`.

```bash
#!/bin/bash
W=$(cd "$(dirname "$0")" && pwd); cd "$W/vault"
export TMPDIR="$W/tmp"; mkdir -p "$TMPDIR" "$W/logs"
if [ "$1" = 1 ]; then uuidgen | tr A-Z a-z > "$W/sid.txt"; F="--session-id $(cat "$W/sid.txt")"
else F="--resume $(cat "$W/sid.txt")"; fi
echo "$2" > "$W/logs/$1.prompt"
claude -p "$2" $F --add-dir "$TMPDIR" \
  --allowedTools "Bash(command -v:*)" "Bash(mkdir:*)" "Bash(defuddle:*)" "Bash(wc:*)" "Bash(rm:*)" Write Read Skill \
  --output-format stream-json --verbose </dev/null > "$W/logs/$1.jsonl"
python3 - "$W/logs/$1.jsonl" <<'P'
import json, sys
for l in open(sys.argv[1]):
    d = json.loads(l)
    if d.get("type") == "assistant":
        for c in d["message"]["content"]:
            if c["type"] == "text": print("TEXT:", c["text"])
            elif c["type"] == "tool_use": print("TOOL:", c["name"], json.dumps(c["input"])[:160])
P
```

**Turn script** (one `run.sh` call per turn, answers adapted to what the agent asks; write them
in the language you want to test)

| Turn | User says | Evals it exercises |
| --- | --- | --- |
| 1 | `/ingest https://emilkowal.ski/ui/developing-taste` | ingest 1, 18 |
| 2 | No other points; why you are here and what you will do with it | 15, 16, 19 |
| 3 | A hedge about the first point | 4, 20 |
| 4 | A confident restatement taken from the clip | 21 |
| 5 | "Nothing, that's it." | 9 |
| 6 | "No idea." on the next point | 6 |
| 7 | "done" | 11 |
| 8-9 | A main idea, then "Nothing, that's it." | 10, 17 |
| 10 | A reaction to the article | 12, 13 |

Cases that need their own session: ingest 5 (confused answer), 7 (mismatch), 8 (reaction),
10 (answer "yes" to the open confirmation), 14 (delete one `*-technique` folder from the
vault first), 2 and 3 (a plain prompt with no slash). For the other skills, open
`<skill>/evals/README.md` and follow its setup.

**Judge**

- Skill calls per turn: `grep -o '"name":"Skill","input":{[^}]*}' logs/N.jsonl`. The skill
  must be called by name, not opened by path.
- Quotes: each quote in the notes must appear verbatim in the saved clip, inside one
  paragraph, ignoring `[^n]` markers, emphasis and curly quotes. Check with a script.
- Judge behavior, not wording. Mark each case pass, fail or not exercised, with the quoted
  turn. Ignore harness noise (blocked `/tmp` writes, denied tools); it is not a skill defect.
- Record the result in the table below, with the harness and date.

**Cloud**

- No residential IP: `clip-article` may fail on some sites. Paste the article text after
  `/ingest` instead, and mark ingest 1 "not exercised".
- Use a project-local install, as above. A cloud session needs the same folder layout.

## Results

| # | Harness | Date | Pass / fail | Notes |
| --- | --- | --- | --- | --- |
| A1 | CC 2.1.312 | 2026-10-29 | pass | 12/12 skills visible in a project-local install (temp vault). |
| A2 | CC 2.1.312 | 2026-10-29 | partial, re-run pending | `clip-article` via Skill tool; 5 topic labels, no quotes. Run 1: `defuddle` 0.14.0 rejects `-f`, so no frontmatter or saved file. Run 2 (after fix): clip saved with title and author; the two opening questions merged into one, fixed in `ingest` step 3, not re-run. |
| A3 | CC 2.1.312 | 2026-10-29 | pass | `feynman-technique` via Skill tool. Run 1: question had two parts. Run 2: one question. |
| A4 | CC 2.1.312 | 2026-10-29 | pass | Confident: verification behaviour, no new Skill call (loaded earlier). Blank: `guided-reading-technique` via Skill tool, no choice offered. |
| A5 | CC 2.1.312 | 2026-10-29 | pass | Standalone close did not appear after the confirmed statement. |
| A6 | CC 2.1.312 | 2026-10-29 | pass | Main-idea and closing questions ran once; notes in fenced blocks; density check not observable. |
| G1 | CC 2.1.312 (-p, cloud) | 2026-10-29 | partial | Ingest 1, 2, 3, 5, 6, 7, 8, 10, 11, 12, 14, 16-19, 21 pass. 4 fail (hedge made no Skill call in the main run; `feynman-technique` fired in a variant run). 20 fail (`feynman-technique` asked a contrast the source draws). 9, 13, 15 not exercised. Density check cannot confirm. Fixes: `ingest` step 4 and Hard rules, `feynman-technique` question shapes. Re-run (6 + 3 sessions): 20 pass 3/3 after the added step 4 rule; 4 still inconsistent (feynman called in 4 of 6 on the personal-preference hedge); exact-words rule held in 1 full session (Intention, main idea and both Implications kept verbatim; one session only). |
| G2 | CC 2.1.312 (-p, cloud) | 2026-10-29 | note | `defuddle` 0.19.6 fetched from the cloud, so ingest 1 is exercised. `uuidgen` missing (shimmed). User-level skills such as `supermatt:*` are visible to the vault. |

Run headless (`claude -p`, scripted user) in a temp vault; an interactive run is still to do.
