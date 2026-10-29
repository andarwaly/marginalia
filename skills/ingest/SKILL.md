---
name: ingest
description: "Interviews the user about one source and drafts source notes that keep the source's points apart from the user's implications. Use when the user runs /ingest with a URL or pasted text."
disable-model-invocation: true
---

# Ingest

Interview the user about one source until they can state its points in their own words,
then write source notes. The source is the only authority. The agent never states a point
for the user; the user's restatement is what the notes keep. The notes are a starting
draft the user copies and refines in their own words.

If a technique skill named below is missing, stop and tell the user to install the full
marginalia set.

## Terms

- **Point**: one standalone proposition the source makes, with one exact quote.
- **Frontier**: the agent's candidate points, kept in mind, never shown with quotes.
- **Intention**: what the user wants from the source, in their words; often it includes
  what they will do with it.
- **Reading state**: how the user's last answer landed (`references/reading-the-answer.md`).
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
3. **Open.** Show the topics as neutral labels, no quotes. Ask two separate
   questions, one per line: whether the user has other points, and "What do you want from
   this source?" (say article, video or post to fit). The second answer is the intention.
   Central points are the topics that answer it, interviewed in the order the user names,
   else the order the source presents them. If none fits, ask which topic they want first.
   Assume the user has at least skimmed the source; if they say they have not read it
   fully, run `guided-reading-technique`.
4. **Interview one point at a time.** Ask the user to explain the point in their own words,
   naming only its topic. Then read their answer's state and pick the technique; read
   `references/reading-the-answer.md` at the first answer. After every later answer, read
   the state again and switch technique.
   - Every question in the interview, including one a technique asks, has one question
     mark and no "and" that adds a second ask, and never states what the source says
     before the user has stated the point. Quote the source only after the user has
     answered, except the passage `guided-reading-technique` opens with.
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
   4. Ask once, in the user's language, recalling the intention verbatim, the same text
      that goes under `## Intention`: "you wanted <intention>. What do you make of this
      article against that?" (say video or post to fit). With no intention, ask what they think of the article. A decline ends the
      questions; the notes still follow.
7. **Notes.** Read `references/source-notes.md`. Write one map note and one note per picked
   point, each in its own fenced block with its filename on the line above, then the
   coverage list.
   Write files only when the user asks, into a folder they name.

## Hard rules

- No note before a statement is confirmed through the statement gate.
- Notes carry quotes only for points the user picked. Unpicked points leave no trace; a
  partial note is valid.
- Implications are the user's words, kept as `references/source-notes.md` says, never
  written by the agent. Anything the user says at step 6.4 is an Implication on its point,
  or on the map if it concerns the whole. The Intention section does not change after
  step 3.
- A user remark that fits no point: `references/reading-the-answer.md`.
- The agent's own disagreement or addition is allowed only in chat, after a point is
  settled, at most once per point, labeled "My own view, not the article's:". It enters a
  note only if the user adopts it as an Implication in their words.
- Applications come from the user. When they say how they would apply a point, it becomes
  an Implication on that point; a fuller idea goes to `ideate`.
- Never name reading states or techniques to the user. Show the question, not the routing.
- Reply in the user's language. Everything that names the source stays in the source's
  language (`references/source-notes.md`).
