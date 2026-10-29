---
name: ingest
description: "A mode for discussing and learning from one source with the user. It ends in source notes that keep the source's points apart from the user's implications."
disable-model-invocation: true
---

# Ingest

Interview the user about one source until they can state its points in their own words,
then write source notes. The source is the only authority. The agent never states a point
for the user; the user's restatement is what the notes keep.

If a technique skill named below is missing, stop and tell the user to install the full
marginalia set.

## Terms

- **Point**: one standalone proposition the source makes, with one exact quote.
- **Frontier**: the agent's candidate points, kept in mind, never shown with quotes.
- **Reading state**: how the user's last answer landed: confident, hesitant, confused or
  blank.
- **Statement gate**: a statement is fixed only on the user's open confirmation.
- **Done gate**: the closing questions that run before the notes.
- **Implications**: the user's own reactions, kept apart from the source's points.

Fuller definitions: `references/terms.md`.

## Steps

1. **Get the source.** A URL goes through `clip-article` or `clip-youtube`; pasted text is
   used as is. In plain chat, ask for the pasted text. Read all of it. If the clip says
   `captions: auto-generated`, warn once that quotes may carry transcription errors.
2. **Build the frontier.** List the points, each with one exact contiguous quote from the
   source body. Never quote frontmatter or an AI summary. A point from material the author
   quotes belongs to the quoted person.
3. **Open.** Show the topics as neutral labels, no quotes. Ask whether the user has other
   points and what brought them to the source. The answer decides which points are central.
   Assume the user has at least skimmed it; if they say they have not read it fully, run
   `guided-reading-technique`.
4. **Interview one point at a time.** Ask the user to explain the point in their own words,
   then start `verification-technique`. After every answer, read the reading state and
   switch technique; read `references/reading-the-answer.md` at the first answer.
   - Ask one question per turn. Quote the source only after the user has answered.
   - Interview a central point. For a supporting point, draft it from the source, check the
     quote, and show it for the user's correction.
   - Never fill a gap from general knowledge.
5. **Resume.** When a technique reaches a confirmed statement, ignore its standalone ending
   and go to the next point (step 4) or, when none is left, to step 6. Nothing is written
   yet. If the talk wanders, answer briefly and return to the step you were on.
6. **Done gate.** Start on the user's signal ("done", "that's everything", or a request for
   the notes). Otherwise, once every picked point is settled, ask once: "anything else on
   this source, or shall we wrap up?" Then, in this order (a done signal skips only the
   nudge and the offer):
   1. One nudge for points drafted but unconfirmed; one offer on untouched topics.
   2. Density check: points resting on the same reasoning merge; a list the source presents
      as a unit becomes one point.
   3. Ask the main idea: "having been through all of it, what do you think the main idea
      is?" Fix it through the statement gate (`references/statement-gate.md`).
   4. Ask once: "what do you think of this article?" (say video or post to fit). A decline
      ends the questions; the notes still follow.
7. **Notes.** Read `references/source-notes.md`. Write one map note and one note per picked
   point, each in its own fenced block labeled with its filename, then the coverage list.
   Write files only when the user asks, into a folder they name.

## Hard rules

- No note before a statement is confirmed through the statement gate. A bare "yes", a
  pause or a topic change does not confirm it.
- Notes carry quotes only for points the user picked. Unpicked points leave no trace; a
  partial note is valid.
- Implications are the user's words, lightly tidied for spelling and filler, never reworded
  and never written by the agent. They sit in their own section, apart from the point.
  Anything the user says at step 6.4 becomes an Implication on its point, or on the map if
  it concerns the whole.
- The user's remark that fits no point: find the nearest passage and ask, "The article says
  'x' is 'y'. Is that what you said, or did you have something else in mind?" A misreading
  returns to that point. The user's own read becomes an Implication. If no passage exists,
  re-check the source before saying so, then ask.
- The agent's own disagreement or addition is allowed only in chat, after a point is
  settled, at most once per point, labeled "My own view, not the article's:". It enters a
  note only if the user adopts it as an Implication in their words.
- Tangents never block. Note them and return.
