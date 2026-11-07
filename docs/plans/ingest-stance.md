# Plan: Stance in `ingest`

Status: approved by the owner (2026-11-08), not implemented. Implement on the branch that
carries this file, one commit, evals changed in the same commit.

## Problem

The note records the owner's replies word for word, but a reply only means something next to
the question that prompted it. "It makes sense to me because…" is unreadable on a later
visit. ADR 0004 patched this with bracketed referents; the owner rejected them, and 0006
dropped them, so the fragments returned. Both failed because the unit recorded was the
reply, not the thought.

The goal of ingesting: catch what the author stands by, and where the owner stands on it.

## Change

Each source point records two self-contained lines:

- **Claim line**: what the author stands by, in the owner's words. Exists today.
- **Stance** (new): where the owner stands on that claim and why, in one sentence that
  makes sense without the chat. Written by the owner, never by the agent.

### Stance check

Run once per thread, at thread close (SKILL.md step 6), before the marker moves. One batched
message, one line per source point discussed in the thread:

```
Before we move on, one sentence per point, readable without this chat:
1. <claim heading> — where do you stand, and why?
2. …
```

Rules:

- The Stance is the owner's reply word for word, spelling fixed. The agent adds nothing:
  no brackets, no tag, no rewording.
- When a reply leans on the question ("it", "b", "because of that"), ask once for a version
  that names its subject. Take the second reply as given.
- The owner may decline a point. That point has no Stance line.
- Implications stay for what fits no Stance: tangents, cross-domain links, doubts, life
  examples, questions the source does not answer.

### Note layout per point

```
## Claim heading
<Author> says <claim line>. [locator]

Stance: <the owner's sentence>

- Example: …
- Quoted: …
- <loose Implication: a tangent, doubt or question>
```

Unchanged: the interview rows, Intention and Prior belief (asked, not written), Quotes,
Key Concepts and Mentioned, the End review, the Draft framing.

## Files

- `CONTEXT.md`, then `skills/ingest/references/terms.md` (copy second): add **Stance**;
  redefine **Implications** as loose thoughts that fit no Stance; update **Source point**
  and **Wrap-up** if they list the note's parts.
- `skills/ingest/SKILL.md`: step 6 gets the Stance check; step 5's "Record per thread" and
  the Hard rules say Stance, not only Implications.
- `skills/ingest/references/source-notes.md`: layout, Stance rules, Implications rule,
  After the block (list points with no Stance).
- `skills/ingest/references/reading-the-answer.md`: rows 6 and 12 hold the owner's idea for
  the Stance check; nothing is recorded as a bare bullet that depends on the question.
- `skills/ingest/references/end-review.md`: show Stance lines for the owner to edit.
- `skills/ingest/evals/README.md`: new cases (Stance check at thread close; reply leaning on
  the question gets one re-ask; declined point has no Stance; Stance is word for word); update
  cases that expect Implications to carry the owner's take on a point.
- `docs/adr/0007-stance-is-written-by-the-user.md`: new. Supersedes the Implications part
  of 0006. Record why brackets (0004) and raw replies (0006) both failed, and the options
  rejected: agent drafts the Stance and the owner confirms (agent phrases the owner's
  opinion); keep replies and show the question beside each (the note still reads poorly).
  Risk: one extra batched turn per thread.
- `TESTING.md`: one pending re-run row (23g-v9). Check: no Stance depends on the question;
  no agent text inside a Stance; the interview otherwise behaves as in 23f-v8.

## Open choices, defaults taken

- Line name is `Stance:`. Alternatives: `I think:`, `My take:`.
- The check runs once per thread, not per point mid-discussion, to keep the interview flow.

## Verify

- Read `CONTEXT.md` terms against every edited file; `terms.md` matches the `CONTEXT.md`
  entries.
- Write each edited skill file with `writing-for-agents`.
- Re-run on a source after merge; see the TESTING.md row.
