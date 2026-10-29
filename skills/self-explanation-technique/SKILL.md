---
name: self-explanation-technique
description: "Marginalia interview technique, only when a marginalia mode calls it or the user names it. Points at the specific contradiction in a confused answer so the user repairs their own model."
---

# Self-explanation

## What it is

From Chi et al.'s research on generative learning: learners explaining
material to themselves while engaging with it, generating inferences and
repairing their own mental model when they notice a discrepancy between new
material and what they already believed. Distinct from asking a targeted
"why" question (that's elaborative interrogation) — this is open-ended,
unprompted sense-making, and the repair happens because the discrepancy was
*noticed*, not because it was corrected for the person.

Needs something the user has already said that doesn't hold together. Run
on its own, start by asking for their current understanding in their own
words, then listen for the inconsistency.

## Why this technique, for this job

A confused-but-not-blank answer is exactly a mental-model-repair situation —
something was said, it just doesn't hold together, meaning a discrepancy
exists somewhere between what was said and what the source (or the user's
own prior reasoning) actually supports. This technique's whole mechanism is
surfacing that discrepancy and letting the person notice and fix it
themselves, rather than the agent diagnosing and correcting it directly —
which matters here because correcting it outright would be exactly the
kind of "handing over the answer" this whole family exists to avoid.

**Reach for this when** the answer is confused — touched something, but
garbled or circular, distinct from hesitant (uncertain but coherent) and
blank (nothing substantive at all).

If the answer is merely hesitant — shaky but not self-contradictory —
`feynman-technique` fits better. Feynman's loop assumes a simplifiable idea
exists; this technique assumes a *specific internal inconsistency* to
surface, which a merely-hesitant answer may not have.

## Concept

Chi's own data shows the technique's benefit is highly contingent on how
well someone already self-explains — a "high self-explainer" and a "low
self-explainer" get very different results from the same open-ended
prompt, and the bare technique offers no built-in scaffolding for improving
a poor self-explainer's ability. That's exactly why this family's version
narrows the open-ended version down to something more targeted: rather than
"make sense of this however you can," surface the *specific* discrepancy
noticed in what was just said, pointed at directly, so even someone who
wouldn't self-explain well unprompted has something concrete to work from.

## Conversational adoption

- **Name the specific contradiction, not the general confusion.** "You said
  X, but a moment ago you said Y — how do those fit together?" is far more
  useful than "that doesn't quite make sense, try again."
- **Point at the discrepancy, don't resolve it.** The repair is the user's
  own; the agent's job stops at making the inconsistency visible. When
  several discrepancies show, name the one the others depend on. A pair of
  blurred terms is a distinction question ("how are A and B different
  here?"); a claim without its cause is a mechanism question.
- **Acknowledge, then ask.** Give one short, varied acknowledgment on its own
  line ("that's a fair place to get stuck"), and the question on the next
  line.
- **Let genuine confusion sit for a moment.** Don't rush to rephrase the
  question if the first attempt to surface the discrepancy doesn't land
  immediately — repair takes a beat, especially for material that was
  genuinely garbled.
- **Distinguish "still confused" from "newly confused."** If naming the
  discrepancy produces a different confusion than the original one, that's
  actually progress (a smaller, sharper gap) — don't treat it as a failed
  attempt.

## Worked example

> **User:** So notes get better the more you write, because linking them
> makes them clearer, but also each note is supposed to stand alone without
> needing the others?
> **Agent:** Those two things you just said seem to be in tension — notes
> get clearer *through* their links, but also need to make sense *without*
> them. How do you square those?
> **User:** Hm. Maybe... the note itself has to be complete on its own, but
> the links are what make it *more* valuable, not what make it
> understandable in the first place?
> **Agent:** That's a real distinction — completeness versus value added.
> Does that resolve the tension, or is there still a piece that doesn't
> fit?

## Guardrail

There's a temptation to soften the discrepancy into something gentler than
it actually is — hedging the contradiction so it doesn't feel like a
callout. That defeats the mechanism: the discrepancy has to be named
clearly enough to actually notice, not smoothed into something so vague
it's easy to wave past without genuinely reconciling it.

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
