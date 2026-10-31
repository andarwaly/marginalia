# Laptop tests

Tests that need a real harness or a residential IP. Run them in this order; stop at the first
failure in A, because the rest depend on it. Record each result in the table at the end, with
the harness and date. Use the "Developing Taste" article (https://emilkowal.ski/ui/developing-taste)
unless a test says otherwise.

Harnesses: **CC** Claude Code, **CX** Codex, **CW** Cowork.

## A. Call by name (run on CC, CX and CW)

1. Install the whole repo (`npx skills add andarwaly/marginalia`, or the plugin). List the
   skills; expect thirteen.
2. Run `/ingest https://emilkowal.ski/ui/developing-taste`.
   - Pass: `clip-article` runs, then the agent asks the Prior belief and Intention
     questions, one per line. No threads and no quotes are shown yet.
3. Answer both (say "I want to learn how to judge AI output").
   - Pass: the agent shows 2-4 threads as one-line chains, with a progress marker and the
     finish line, and the first question of thread 1 in the same message. That question
     names only the topic.
4. Give a confident, correct restatement.
   - Pass: no verdict such as "that matches"; the next question goes to the next unseen ask
     passage (or the Intention question, or one push).
5. Give a hedge ("something about practice, I think?").
   - Pass: the agent calls `feynman-technique` by name and asks one plain-language question
     built on what you said.
   - Watch for: Codex opening the SKILL.md path instead of invoking a skill. Note which
     happened; either is acceptable if the interview works.
6. Give a tentative claim ("I think it's basically ..."). On the next point say "I'm stuck".
   - Pass: `scaffold-technique` is called by name. The first time: one example that opens
     "From my own knowledge, not Kowalski's", then one question. The second time: rung 1 of
     the ladder (the passage named by its opening words), one rung per turn.
7. Answer "no idea."
   - Pass: the `scaffold-technique` ladder at rung 1 (the passage named by its opening
     words), with no choice offered.
8. Say "done".
   - Pass: the coverage list; up to three `ideate` suggestions; you state the main idea
     first; one message proposes Key Concepts and Mentioned; the notes appear
     in fenced blocks for the End review; the agent asks once for a folder and writes files
     only after the review. Prior belief, Intention, main idea and Implications are your
     words, word for word.

## B. Flags and routing

7. `/ingest` works with `disable-model-invocation: true` (CC, CW). Fail: "unknown skill".
   Fallback: make it a model-invoked skill whose description says it runs only when the user
   invokes it.
8. Say "summarize this article: <URL>" with no slash. Pass: `ingest` does not run (CC, CW);
   on CX, the same with `agents/openai.yaml` in place.
9. Say "explain this simply", "challenge my idea", "ground me on this". Pass: no skill from
   this repo runs. Note any collision with your own `grounding`, `grilling` or `ground-me`.
10. Type `/feynman-technique` and name a topic. Pass: it runs on its own and ends by saying
    your statement back once, with no notes.

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
23. Acceptance, run by the owner. Run `/ingest` on "Developing Taste" with your real answers,
    then compare with the failed v1 run (`session-test/marginalia/transcript.md`) and the
    slipbox run (`session-test/slipbox/Transcript Slipbox.md`). Pass on one question: did you
    learn something you could not have written yourself? Also note: did any reply open with a
    stock acknowledgment, did the agent bring your earlier thinking back, and did you always
    know what came next?

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
| 1 | `/ingest https://emilkowal.ski/ui/developing-taste` | ingest 1 |
| 2 | A prior belief, and "I want to learn how to judge AI output" | 5 |
| 3 | A clear, correct restatement taken from the clip | 7, 17, 18 |
| 4 | A hedge about the next point | 9, 15 |
| 5 | A tentative claim ("I think it's basically ...") | 13 |
| 6 | "I'm stuck, I can't put it into words" | 14 |
| 7 | A tangent ("this reminds me of how CLIs show help") | 11 |
| 8 | A rough, loose dump on a point you cannot phrase | 12 |
| 9 | "skip the next thread" | 8, 19 |
| 10 | A remark tied to no thread | 20 |
| 11 | "done" | 21 |
| 12-13 | A main idea, then "that's it" to the End review, then a folder name | 22, 23, 24, 25 |

Cases that need their own session: ingest 4 (delete one `*-technique` folder from the vault
first), 6 (give no Intention), 10 (tell a story in turn 3 that a later point bears on), 16 (a
claim that goes beyond its quote), 26 (answer in Indonesian), 27 (leave a thread untouched),
2 and 3 (a plain prompt with no slash). For the other skills, open `<skill>/evals/README.md`
and follow its setup; `scaffold-technique` cases 12 and 13 run standalone.

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

Results below the v1 heading predate the 2026-10-30 redesign (new `ingest`, `scaffold-technique`,
End review). They are history, not a pass for the new skills. Record new runs in the v2 table.

### v2 (after the redesign)

| # | Harness | Date | Pass / fail | Notes |
| --- | --- | --- | --- | --- |
| G-v2 | CC 2.1.312 (-p, local) | 2026-10-30 | partial | Run 1 (13 turns, scripted user), then fixes, then run 2 (6 turns). **Pass:** ingest 1, 5, 7, 11, 12, 13, 18, 19, 20, 21, 22, 23, 24 (quote verbatim in the clip; Prior belief, Intention, main idea and Implications word for word), 25, 27. Run 2: `feynman-technique` and `scaffold-technique` loaded by name; the stuck ladder began at rung 1; "I can't put it into words" got three candidate wordings. **Fail or weak:** 9 (stock opener "Noted, skipping the AI thread" in run 1; a milder "'Seeing patterns' is a start." in run 2); 14 (run 1: "can't put it into words" took the rough-dump path, not the ladder; trigger overlap fixed in the skills, run 2 passes); 15 (run 1: only `scaffold-technique` was loaded by name; fixed by loading techniques with the Skill tool, run 2 passes for feynman and scaffold); 17 (no Intention link seen in run 1 before a thread closed). **Not exercised:** 2, 3, 4, 6, 10, 16, 26; `maieutic`, `elenchus`, `guided-reading`, `verification` and `self-explanation` were never triggered. |

| 23-v2 | CC cloud (marginalia-vault PR #1, interactive) | 2026-10-30 | pass on outcome, with fixes | Owner run on "Developing Taste" (4 threads, 9 source points). The owner reported learning and a two-way discussion. **Pass:** ingest 1, 5, 10, 13, 21, 22, 23, 24, 25 (scaffolds Van Gogh, wine study and AlphaGo stayed out of the notes). **Fail or weak:** 9 and 18 (every reply opened by restating the owner, with verdicts such as "a sound one"); 7 (quotes shown before the owner's take, then a "what does <Author> say" question); 17 (Intention link stated, not asked, and missing in two threads); the scaffold questions packed two asks and the owner twice asked for elaboration; Key Concepts and Mentioned were picked silently, so the owner added them by hand; Key Concepts inconsistent ("Tastemaker", "Tastemakers"). **Fixes applied:** openers, one plain ask, the Intention link as a question, a Wrap-up step 4 that proposes Key Concepts and Mentioned in one message, the one-clause "that's yours" note for the owner's own ideas, no agent-written prefix on Implications, the Intention question reworded ("What makes you want to read this?"). **Held:** quote timing and thread-opening questions, until a second source. |
| 23b-v2 | CC cloud (marginalia-vault PR #2, interactive) | 2026-10-31 | partial; owner: less learning, not grounded | Owner run on "Agents with Taste" (3 threads, 3 source points) on skills `2ca8744`. **Findings:** the "that's yours, not <Author>'s" clause opened about 8 of 14 replies and made the owner feel wrong; threads built from claims skipped the article's Linear logo demo, the `scale(0)` versus 0.95 comparison, the Practical Tips, easing, duration and typography code blocks; the agent offered tabular-nums as "my own knowledge" though the article contains it; the owner's answer to thread 1 and their question about agencies reached no note; the Key Concepts and Mentioned proposal missed names the owner added. **Fixes (branch `claude/ingest-v3-grounding`):** passage list first to last, examples and code as discussion items, meet and return replacing "that's yours", misreads sent to `guided-reading-technique`, a thread done only when its passages are seen, a coverage list at wrap-up, a source-wide map line. **Next:** re-run on the same article and compare. |
| 23c-v3 | CC cloud (marginalia-vault PR #3, interactive) | 2026-11-01 | partial; better grounded, still drifted | Owner run on "Agents with Taste" on skills `5e9729f`. **Pass:** the scale balloon, tips table, easing flowchart, duration table and typography block were shown and discussed; the Linear and dialog demos were handled as dropped demos; no "that's yours"; wrap-up proposed Key Concepts and Mentioned from the whole source. **Findings:** thread 2 spent about 13 turns on the owner's own blur rule (ideate's job); passages shown as a bridge counted as seen, so typography, the duration rules and the skill-creator tip ended as "not discussed"; a receipt ("Prior belief and Intention are recorded"); the full marker appeared on views that did not differ from the author; the owner asked for reasons per term, an Example section and plain Key Concepts entries mid-session. **Fixes (branch `claude/ingest-v4-ask-the-passage`):** the closing question is about the passage; seen needs an answered question about it, and table rows and rules belong to their parent; marker only when the view differs from the author; Key Concepts as `Term: what it is, why it is here`; Example section. **Next:** re-run and watch for a question per row (over-questioning) and for the marker on agreeing views. |
| 23d-v5 | CC cloud (pending re-run) | 2026-11-01 | not run | Changes after 23c-v3, on branch `claude/ingest-v5-implications`: Implications stand on their own (bracketed referents, replies on one thought joined, the End review lists the brackets); questions invite a thought, not a pick; `source-notes.md` yields filenames, frontmatter and headings to a vault template named in AGENTS.md. **Check on the next re-run:** no bare fragment as an Implication (evals 68-71); no run of pick questions (72); the vault template is followed and the content rules survive it (73); brackets never hold an opinion. |

### G findings (v2, 2026-10-30)

Open, to re-check in an interactive run (test 23).

- **Intention link (ingest 17).** In run 1 a thread was marked done without the agent relating
  it to the Intention. Step 6 requires it; the agent did not enforce it. Watch for it in run 2
  and interactively.
- **Receipt-like openers.** Run 1 opened with "Noted, skipping..."; the rule now names
  "Noted." and "That matches." but run 2 still opened with "X is a start." Judge in an
  interactive run whether that reads as a stock reply.
- **Techniques.** Five techniques were never triggered. Script a run that gives a confused
  answer, a mismatch and a blank answer.
- **Few source points.** Four threads and a long discussion produced one source point, because
  most of the user's talk was their own thinking. Check in an interactive run that this is
  what you want.
- **`ideate` suggestions** at wrap-up are the agent's paraphrase of an Implication, not the
  user's words. Decide whether they should be quoted.
- **Plugin copy.** The harness also sees the installed `marginalia:` plugin (names such as
  `marginalia:clip-article` appear in the logs), so a run is not isolated from the repo.

### v1 (superseded)

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

### G findings (v1, 2026-10-29, CC 2.1.312 headless, cloud)

These are v1 findings. The technique-loading one (ingest 4) is worth re-checking on the new
skills: confirm each technique is loaded by name before its question is asked.

- **Ingest 4 (medium).** The hedge does not reliably load `feynman-technique` by name. On the
  personal-preference hedge it loaded in 4 of 6 runs (`r4`, `s2` did not); on the practice
  hedge, 3 of 3 after the step 4 edit, 0 of 1 before. In the misses the agent still asked one
  feynman-shaped question after reading `reading-the-answer.md`, but never opened the
  technique file, so its guardrails were not in context. `r4` also asked the contrast
  question (ingest 20). Cause not visible in the logs; later turns of the misses were not
  checked. Candidate fix: step 4 says to load the technique with the Skill tool before asking.
- **Ingest 9, 13, 15: not exercised.** 9 needs a technique reaching a confirmed statement
  (`verification-technique` was not loaded in the main run). 13 needs an agent disagreement.
  15 needs the "design reviews" answer. Density check (11) cannot be observed.
- **Extra loads.** `guided-reading-technique` (`s1`) and `maieutic-technique` (`s3`) loaded
  before `feynman-technique` on a hedge. Not visible to the user; effect unknown.
- **Harness noise, not defects.** The nested session overrides `TMPDIR`, blocks `$TMPDIR` and
  `/tmp` writes, and denied approval for `node`/`python3` build scripts (`c14`, `c14b`).
  `uuidgen` is missing in the cloud container (shimmed). The vault also sees user-level
  skills (`supermatt:*`), so `ideate` shares a name with `supermatt:ideate`.
- **Fixed and re-run.** Ingest 20 passes 3 of 3 after the step 4 rule. The exact-words rule
  held in 1 full session.

Run headless (`claude -p`, scripted user) in a temp vault; an interactive run is still to do.
