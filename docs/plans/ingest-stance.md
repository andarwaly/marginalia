# Plan: Stance, Reactions and plain questions in `ingest`

Status: implemented on branch `claude/ingest-v9-stance-plan` (2026-11-09). Kept as a pointer; the decisions and their reasons are in `docs/adr/0007-stance-reactions-offshoots.md` and `docs/adr/0008-plain-frames-and-quote-first.md`.

This plan began as a Stance-only patch and grew after the owner compared the agent's note with their own draft and read a real session. The parts that changed from the first plan:

- Reactions sit under the passage they answer, and the Stance is the cross-passage synthesis.
- The highlight is written as a block quote, the author's stand.
- Wide thoughts are Offshoots under `## Beyond the source`.
- Assumption flags are dropped: tags are the owner's vault rules.
- Questions use plain frames (`skills/ingest/references/questions.md`) and quote the author's line first, except topic questions.

Not done, on purpose: a writer-led thread opener ("Write what you make of this thread"). Opus's review recommended it as a cheap test of whether the agent-led agenda is what costs the owner control. Run it after a re-run of 23g-v9.
