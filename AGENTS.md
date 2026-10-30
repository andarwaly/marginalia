# marginalia

Skills that help the user articulate their own thinking about a source. `ingest` discusses
one source with the user; the notes it drafts keep the user's wording.

## Where things live

- Terms: read `CONTEXT.md` before editing a skill, and use its terms exactly.
- Decisions and their reasons: `docs/adr/`. Add an ADR when a change is hard to reverse,
  surprising without context, and a real trade-off.
- Laptop test script: `TESTING.md`.
- `DECISIONS.md` predates the redesign. `CONTEXT.md` and `docs/adr/` win where they differ.

## Editing skills

- Write every SKILL.md, reference file and this file with `writing-for-agents`.
- Skill text says "the user". Only repo-internal files say "the owner".
- Each skill's `evals/` follow its behavior: change a rule, change its eval in the same commit.
- A mode calls a technique by name. Edit the technique once; the modes do not restate it.
- Skills install without the repo root. A skill's `references/terms.md` carries the terms it
  uses; edit `CONTEXT.md` first, then the copy.
