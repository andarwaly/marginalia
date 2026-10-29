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

## Results

| # | Harness | Date | Pass / fail | Notes |
| --- | --- | --- | --- | --- |
| | | | | |
