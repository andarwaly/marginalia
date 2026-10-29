---
name: grounding
description: "The protocol for discussing something with the owner one question at a time until they have confirmed what they understand or think, held against a source or notes when present. Use when the owner asks to be grounded on a topic, or when ingest or ideate calls it. Not for summarizing."
---

# Grounding

Help the owner understand something, or confirm what they think, by asking one question at
a time until it is explicit, correct and confirmed. The words come from the owner; the agent
asks and never states the answer for them. Ask exactly one substantive question per turn,
because a batch lets the owner skim past the one that matters.

## Terms used here

- **Statement:** the one thing the session works toward, in the owner's words.
- **Fidelity direction:** what the conversation is held to: a source, the owner's notes, or
  nothing.
- **Reading:** how the owner's last answer landed: confident, hesitant, blank or confused.
- **Statement gate:** the rule below that fixes a statement.

## What the caller supplies

The calling mode states its fidelity direction and its opening question. A bare session (the
owner asks to be grounded on a topic) uses "neither" and opens with: "What are we working
through, and what do you want to understand?" After the opening, name no technique and
label no question.

- **Source-bound** (ingest): hold the owner to the source.
- **Notes-bound** (ideate): hold the agent to the owner's pasted notes. The owner's own
  experience and opinions are free, because they are the point.
- **Neither:** say so plainly and continue. An ungrounded hunch is a complete outcome.

## Fidelity

- **Source-bound.** When the owner's words drift from the source, find the nearest passage
  and ask: "The source says 'x' is 'y'. Is that what you said, or did you have something
  else in mind?" Quote only after the owner has answered the question about it, because an
  earlier quote hands over the answer. If no passage fits, read the source again before
  saying it does not cover the point, then ask whether it is the owner's own thought. The
  caller decides what a confirmed own read becomes.
- **The source contradicts itself:** show both places and ask which one the owner holds to.
- **Notes disagree with the source:** the source wins. Raise the disagreement once, after
  the statement gate.
- **Notes-bound.** Every question and reflection traces to what the pasted notes
  establish. When sharpening needs something no note contains, say so and supply nothing.
- **The agent's own view.** The agent does not fill gaps from general knowledge. When it
  disagrees with the source or adds to it, it says so after a point is settled, never
  mid-question, at most once per point, labeled "My own view, not the source's:". That view
  never enters the statement.

## Never finish it for them

The completion, the candidate, the connection and the counter-argument are the owner's to
supply. Name the gap, the tension or the opening, and leave it open. A question never splits
the source's structure into sub-questions the owner has not found yet. Ask wider first
("explain the argument in your own words"), and narrow to one part only if that stalls.

## Reading the answer

- **Confident:** clear, complete, no hedging.
- **Hesitant:** hedged, trailing off, or "I don't really get it".
- **Blank:** nothing substantive.
- **Confused:** something said, but garbled or circular. Distinct from blank.

Assume the owner has at least skimmed the source, and ask no reading-state question. After
a blank answer with a source present, offer once a choice: read it first, or work through
it together. A reading the owner volunteers is a soft prior; what is observed wins. A
hesitant, blank or confused reading gets one short acknowledgment on its own line, then the
question on the next line. Vary the wording, since a fixed phrase becomes a tell.

## Choosing a technique

Read the technique file before running it. The last column is the one-line version, used
when the file is not available.

| Reading | File in `references/` | One-line version |
| --- | --- | --- |
| Confident | `verification.md` | Check the restatement against the source passage; a match closes quickly, a mismatch is stated plainly. |
| Hesitant | `feynman.md` | Ask for a plain explanation; name the one gap that breaks it; the owner fills it. |
| Confused | `self-explanation.md` | Name the specific contradiction in what was said; the owner repairs it. |
| Blank, source, owner chooses to work through it | `guided-reading.md` | One move per turn on one passage (explain, clarify, compare, recall, predict); hints only when stuck. |
| Blank, no source | `maieutic.md` | Ask toward the forming idea; supply no candidates; test it once spoken. |
| Mismatch found by verification | `elenchus.md` | Press with one kind of question at a time; stop once it resolves. |

Compass, with `connect.md`, `challenge.md` and `distil.md`, decides what to ask next and sits
above this table: use whichever direction fits, and every answer still routes through the
table. Where `compass.md` mentions an evergreen backlog, a `derived-from` field or a
database, ignore it: the north direction is the notes the owner pasted or named, and a
branch not pursued is simply left.

## Statement gate

A statement is fixed only on the owner's explicit confirmation, and two things come first.

- **Probe before any draft.** Show a draft only after at least one open question-and-answer
  round has produced real content from the owner. A polished draft as the first thing shown
  fails the gate.
- **Keep the confirmation open.** Offer "here's what I have so far, from what you said. What
  is missing or wrong?" and never "does this capture it, yes or no?" A genuine "yes,
  exactly" still closes the gate.

For a claim with several parts, build it from the owner's own parts and show them first:

```
Here's what I've got from what you said:
- [part]
- [part]

Putting that together:
> [the compressed claim].

What's missing or off?
```

Vary the connector line. A bare "yes", a pause, a topic change or a settled feeling never
fixes a statement. Confirm that the owner produced the content or meaningfully revised
the wording, and probe once more if not. A vague answer is not raw material to polish into
coherence; flag the vagueness and ask again. A guided-reading session passes the gate once,
over its whole result.

## Done

Hand back the confirmed statement, verbatim, plus the agent's labeled view only if the
owner adopted it. Add no filename, format or note type; the calling mode owns those. A bare
session ends here, with the statement in chat and no notes.

## References

| File | Purpose | Use when |
| --- | --- | --- |
| `references/verification.md` | Checks a confident restatement against the source. | Reading is confident. |
| `references/elenchus.md` | Cross-examines a position with six kinds of question. | Only from verification, on a real mismatch. |
| `references/feynman.md` | Explain, find the break, patch that gap. | Reading is hesitant. |
| `references/self-explanation.md` | Repairs a model that does not hold together. | Reading is confused. |
| `references/guided-reading.md` | Works through a source together with calibrated support. | Blank, source present, owner chooses to work together. |
| `references/maieutic.md` | Draws a first statement out of nothing, then tests it. | Blank, no source. |
| `references/compass.md` | Orients a synthesis: north, west, south, east. | Building toward a position and choosing what to ask next. |
| `references/connect.md` | West: what else holds this shape. | Compass goes west. |
| `references/challenge.md` | East: the condition that would falsify the claim. | Compass goes east. |
| `references/distil.md` | Combines connect and challenge into one claim. | Both have produced something. |
