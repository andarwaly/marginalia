---
name: elenchus-technique
description: "Marginalia interview technique, only when a marginalia mode calls it or the user names it. Cross-examines a position the user has stated, one kind of question at a time, to expose where its own logic fails."
---

# Elenchus

## What it is

The refutative form of Socratic questioning: cross-examine a *stated*
position using six distinct question moves — clarification ("what do you
mean by that?"), probing assumptions, probing reasons and evidence,
exploring alternative viewpoints, probing implications and consequences, and
questioning the question itself. Historically adversarial by design — its
purpose is exposing where a claim's own logic doesn't hold, not building
consensus.

Needs a position the user has stated. If none is stated yet, ask for one
first, in the user's own words, then look for the weakness.

## Why this technique, for this job

A lighter check has already failed, or a weakness is already visible, and
something more thorough is warranted: not just "does this match the source"
but "does this claim actually hold together once pressed from several
angles." It's the heaviest tool in the set, so it needs a real trigger
rather than running by default.

**Reach for this when** a stated position has a located weakness: a mismatch
with the source that `verification-technique` found, a vague term, or an
unsupported leap. Never as an opening move on a position whose weakness
nobody has located. If there is no weakness, say so and stop.

**Don't use this** for a thin-but-accurate answer, or as a way to make an
already-correct restatement feel more rigorously tested — that's friction
without a real trigger behind it.

## Concept

Classical elenchus targets false confidence — a stated belief that feels
solid but hasn't been tested against its own logical consequences or against
a counter-view. This is a genuinely different failure mode from what
`verification-technique` alone catches: verification checks the claim
against the source; elenchus checks whether the claim, once granted,
actually survives its own implications and alternatives.

The six question types aren't a checklist to run through mechanically —
they're named options, reached for based on which kind of weakness was
actually exposed. A weakness about a vague term calls for a clarification
question; a weakness about an unsupported leap calls for a
reasons-and-evidence question.

## Conversational adoption

- **Name what triggered this.** "That doesn't quite match what the source
  says — let's press on it a bit" sets the frame honestly, rather than
  launching into interrogation with no stated reason.
- **One question type at a time**, picked to match the specific weakness
  just found — not a rapid-fire sequence through all six.
- **Firm, not hostile.** The historical risk with elenchus is it reading as
  an attempt to embarrass rather than sharpen — the tone should stay
  collaborative even while the questioning gets pointed.
- **Stop once it resolves.** The moment the claim either survives the
  pressure or gets revised to something that does, the escalation is over —
  go to the Ending, don't keep pressing for its own sake.

## Worked example

> **Agent:** The source actually argues linking changes a note's meaning
> over time, not just that it aids retrieval later — that's a stronger
> claim than what you said. What would have to be true for "just helps you
> find things" to be the whole story?
> **User:** I guess... if the note's content itself never changed after
> writing it, connecting it to other things wouldn't really do anything to
> its meaning.
> **Agent:** And does the source say notes stay fixed after they're
> written?
> **User:** No — it specifically argues they don't, that's the whole point
> of the paragraph I skipped.
> **Agent:** So does "helps you find things later" still hold as the full
> claim, or does it need the meaning-shifts-over-time part too?

## Guardrail

Elenchus can tip into a "guess what's in my head" dynamic if the agent
already has a specific correct answer in mind and is steering toward it
rather than genuinely testing the claim's logic. If a question only has one
acceptable answer the agent is fishing for, that's not elenchus anymore —
it's a quiz wearing elenchus's shape. The test should be genuinely open to
the claim surviving, not rigged to fail.

## Ending

- **Probe first.** Show no draft until at least one open question has drawn
  real content from the user.
- **Confirm openly.** Ask "here's what I have, from what you said. What's
  missing or wrong?" and never "yes or no?" A bare "yes", a pause or a topic
  change does not confirm it.
- **Hand it back.** Give the confirmed statement, verbatim. Called from a
  mode, return it to the mode, which continues at its next step. Run on its
  own, say the statement in chat and stop, with no notes.
- **Never finish it for them.** The answer, the candidate, the connection and
  the counter-argument are the user's to supply. Name the gap and leave it
  open.
