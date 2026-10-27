# marginalia: decisions

**Status: OPEN.** This is a discussion record, not a spec. Only a stub scaffold exists
(manifests and empty skill stubs). Items marked
Settled were answered explicitly by the owner. Items marked Provisional or Default may change.
Items under Open are the next session's frontier. Do not write skill bodies until the owner
confirms shared understanding.

Last updated: 2026-10-27

## Goal

New public repo, ported and simplified from slipbox (`andarwaly/slipbox`). Not over-engineered.

- Targets Claude Code and Codex.
- Skills must also work pasted into a plain chat (ChatGPT, Claude chat): no CLI, no file writes.
- Output is markdown in chat for the owner to copy.
- The owner keeps their own implications in the notes, which slipbox literature notes lack.

## Workflow

```
source  -> ingest                      -> note
notes   -> ideate / refine-idea        -> new idea note
concept + notes -> reference           -> Reference note
```

## Settled

- **Audience:** public from day one.
- **Harnesses:** Claude Code and Codex.
- **Distribution:** a `skills/` folder plus plugin manifests for both.
- **Cloud/chat:** skills must be usable in plain chat. No CLI dependency in the new skills.
- **Skill source:** port from slipbox (`../slipbox`, reference only, do not edit), refining as needed.
- **Interview depth:** adaptive. Interview on points central to the stated inquiry and on
  Implications. The agent drafts and source-verifies supporting points.
- **Implications:** one `## Implications` section per ingest note.
  - The owner's own words only, marked reader-owned.
  - Never inside a Source Point.
  - Elicited by interview. The agent never writes them.
  - Replaces slipbox's "parked take ideas" list.
- **Stage 2:** one skill covers `ideate` and `refine-idea`. Mode is inferred from input
  (no draft = new, draft pasted = revise). Both names go in the description as triggers.
  Keeps grounding, the Take purity check and the five sign-off criteria.
- **Reference notes:** stay a separate output, as their own skill. The owner names a concept and
  pastes the notes that mention it. Keeps the admission sequence and bounded lookup.
  No grounding interview.
- **Conventions:** the owner states them once per chat (frontmatter, prefixes, link style).
  No config file.
- **Inquiry:** asked per source. Standing interests may ride in the same once-per-chat message.
- **Dropped:** setup-slipbox, using-slipbox, write-checks, clip-resource (source is pasted),
  find-connections, ground-me (folds into grounding), the evergreen backlog.
- **Name and repo:** `marginalia`, at `andarwaly/marginalia` (created by the owner 2026-10-27).
  Flat layout, one plugin, no marketplace wrapper. A wrapper repo can come later if more skill
  families appear.

## Provisional

- **Ingest output shape:** one fenced markdown note with these sections: Core Idea, Source Points,
  Open Questions, Key Concepts, Mentioned, Implications. The owner is unsure about the single
  fenced block and said to keep it for now.

## Default (not explicitly confirmed)

- **No validator script** in the new repo. Proposed as the default and not objected to.
  Add one the first time manifest drift bites.

## Open

1. **Grounding in plain chat.** How does grounding reach ingest and ideate when there is no
   skill-to-skill call?
   - Inline in each skill.
   - A separate grounding file pasted too.
   - One combined file.
2. **Which grounding techniques stay.** Candidates: verification, feynman, guided-reading,
   maieutic, self-explanation, elenchus, compass with connect/challenge/distil.
   The technique reference files have not been read yet (`../slipbox/skills/grounding/references/`).
3. **Reference skill inputs.** What does it need pasted to apply the admission sequence without
   a vault scan? Recurrence evidence now comes from the pasted notes.
4. **Ingest block shape** (see Provisional).
5. **Reversal to guard.** Slipbox's glossary rejected a Take, and later a lighter Reaction field,
   in the literature note (2026-07-23), to keep source-owned content pure. This design reverses
   that on purpose through a separate, marked `## Implications` section. Confirm the guard
   (separate section, owner's words only, never inside a Source Point) holds when ported.

6. **Manifest paths unverified.** Whether Codex reads `.claude-plugin/marketplace.json` for this
   repo, and whether `npx skills add andarwaly/marginalia` finds `skills/`. Test on a laptop.

## Port notes (from reading slipbox)

- About 41% of slipbox SKILL.md lines are runtime plumbing (setup, using-slipbox, write-checks,
  clip-resource, find-connections) and do not port.
- Only `grounding` is fully CLI-free. The three note writers carry heavy plumbing to strip.
- The evergreen backlog was the only cross-session state. Its role is replaced by Implications
  (ingest) and pasted notes (stage 2).
- Reference admission needs two independent sources unless one is an authoritative standard, so a
  single-source ingest rarely admits a Reference note. Concepts get a one-line characterization
  and an admission verdict inside ingest's Key Concepts.
