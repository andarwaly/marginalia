---
name: verification-technique
description: "Marginalia interview technique, only when a marginalia mode calls it or the user names it. Checks a user's confident restatement of a source against the source's own passage."
---

# Verification

## What it is

The scientific method, applied to a single restatement instead of a lab
experiment: treat what the user just said as a hypothesis about what the
source means, then check it against the actual source text as evidence. If
the hypothesis and the evidence agree, it's confirmed. If they disagree,
that's data too — a real mismatch worth surfacing, not something to smooth
over.

Needs a source and a restatement in the user's own words. If the user has
not restated anything yet, ask for that first.

## Why this technique, for this job

Every other technique here checks internal logic — does the statement hold
together, does it survive scrutiny. Verification checks something different
and, for this job, more important: does the statement match what the source
*actually says*, which a perfectly coherent, confidently stated restatement
can still get wrong. A confident answer doesn't mean a correct one; this is
the one technique that anchors the check to the source text itself rather
than to how convincing the answer sounds.

**Reach for this when** the user's restatement is clear, complete and
unhedged. It's the cheap default for the common case, not a heavyweight
check.

If the check surfaces a genuine mismatch between the statement and the
source, press with `elenchus-technique`. A thin-but-accurate answer is not a
mismatch, and pressing is never the default opening move for a confident
answer.

If the answer is hesitant, blank or confused, there's no settled statement
yet to check against anything; the calling mode routes those to other
techniques.

## Concept

The failure mode this targets is overconfidence in an unverified claim —
distinct from elenchus's target (a claim that's internally inconsistent). A
restatement can be perfectly well-reasoned, logically defensible, and still
simply wrong about what the source says. Checking internal logic alone would
miss this entirely; the only real check is against the external evidence,
the source itself.

This borrows the *shape* of hypothesis-testing, not its full apparatus —
there's no control condition, no formal falsifiability criterion, just the
core move: state a claim, check it against evidence, revise if they
disagree. Kept deliberately lightweight because it's meant to run by
default, every time, not as a special heavyweight procedure reserved for
important claims.

## Conversational adoption

- **State the check, don't hide it.** "Let's see if that holds up against
  what the source actually says" is a legitimate thing to say out loud —
  this isn't a trap, it's a stated, expected step.
- **Point to the specific passage, and don't quote it yet.** The check is
  against actual text, not a vague sense of "does this feel right" — name
  where in the source the claim should be checkable. Quote the passage only
  after the user has answered; an earlier quote hands over the answer the
  question was meant to draw out.
- **A match closes the loop quickly.** If the restatement holds up, say so
  plainly and go to the Ending — don't manufacture doubt where the check
  passed clean, that would just be friction for its own sake.
- **A mismatch gets surfaced directly, not softened.** "The source actually
  says X, not Y — what do you make of that?" rather than easing into it
  obliquely.

## Worked example

> **Agent:** You said the author argues linking notes helps you "find things
> later." Let's check that against the text — look at the paragraph starting
> "a note gains meaning..." Does that match what it's actually claiming?
> **User:** Oh — no, it's saying something different, that the note's
> meaning itself changes over time as it gets linked to more things.
> **Agent:** Right — that's a stronger and different claim than "easier to
> find." Does the restatement need updating, or does this change anything
> else about what you said?

## Guardrail

The check can slide into rubber-stamping — accepting a restatement as
verified because it sounds plausible, without actually locating and
re-reading the specific passage it should match. If the exact sentence or
paragraph that would confirm or contradict the claim hasn't been pointed to
and read, the check hasn't actually happened yet, regardless of how
confident the exchange feels.

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
