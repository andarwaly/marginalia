---
name: ingest
description: "Discusses one source with the user to sharpen their thinking, then drafts a source note to refine: the source's points, the user's own words, the author's examples and quoted people, Key Concepts and Mentioned. Use when the user runs /ingest with a URL or pasted text."
disable-model-invocation: true
---

# Ingest

Discuss one source with the user until they have met each Spine item and said what they
think of it. The goal is the user's sharpened thinking and their grasp of what the author means.
Then draft the source note: a Draft the user refines into their own note. The user supplies
the thinking; the agent supplies the source's text, a discussion partner's questions, and
marked views and scaffolds.

If a technique skill named below is missing, stop and tell the user to install the full
marginalia set.

Terms (Draft, Spine, Thread, Passage, Passage tag, Seen, Intention, Prior belief, Source point,
Highlight, Example, Quoted, Quote, Locator, Reaction, Stance, Offshoot, Implications, Key
Concepts, Mentioned, Frame, Reading state, Meet and return, Rider, Scaffold, End review,
Wrap-up): `references/terms.md`.

## Steps

1. **Get the source.** A URL goes through `clip-article` or `clip-youtube`; pasted text is
   used as is. In plain chat, ask for the pasted text. Read all of it. If the clip says
   `captions: auto-generated`, warn once that quotes may carry transcription errors.
2. **List the passages, then draft the Spine.** Walk the source from the first sentence to
   the last and list every passage (paragraphs, examples, code blocks, tables, images,
   demos). Draft the Spine and tag each passage ask or mention (`references/passages.md`).
   Hold the draft until step 4. Each Spine item becomes one thread and carries one
   highlight, an exact run from the source body (never frontmatter or an AI summary); a
   claim from material the author quotes belongs to the quoted person. Keep a highlight
   unseen only for a topic question (frame 0 in `references/questions.md`); every other
   question shows it. Done when every passage sits under a Spine item or is skipped with a
   reason, and every structure the author names is a Spine item.
3. **Open.** Done when both questions are answered or declined. Ask two questions, one per
   line: what the user already thinks about the topic (the Prior belief), and "What makes
   you want to read this?" ("watch" for a video; the answer is the Intention). When the
   user gives no Intention, suggest one way the source could help and let them take it,
   change it or drop it.
4. **Set the Spine, then show the threads.** Ask frame 9. Compare the reply with your
   draft and show one list: the user's lines in their words, then each item they missed
   under "Also in the source:", named in the source's words with its locator. Merge lines
   that repeat an item. When the user has not read the source in full, show your draft
   marked as yours and run `guided-reading-technique`. The user may add, drop or merge
   items; the Spine is set after one reply. Then order the threads by the Intention, else
   by the source's order. Show them as one-line chains with a progress marker, the
   examples each thread holds (named by a short label, not their content) and the finish
   line, and put the first question of the first thread in the same message:

   ```
   Threads: ① … (the demo) [now]  ② …  ③ … (the table)
   Done when each thread has your take. Then: wrap-up, notes.
   ```

5. **Discuss a thread.**
   - An item the user named opens on its highlight with frame 2; their line from step 4 is
     a Reaction under that highlight. An item you added opens with a topic question
     (frame 0) that asks for the user's own view, naming only the topic.
   - Name the author in the third person and speak of your own views in the first person;
     never speak as the author. The marker for a view is in `reading-the-answer.md`; a
     scaffold always opens with its own full marker (`scaffold-technique`).
   - Every question is about a passage of the source. The user's own idea is connected to
     the source and recorded; working it out is `ideate`'s job.
   - Read each answer with `references/reading-the-answer.md`: take the first matching row
     and show the user only the question and the passage it asks about
     (`references/passages.md`).
   - Open each reply with the next question, or with something the user said in an earlier
     turn that bears on the point. Refer to their last message only by a short phrase
     quoted from it. A receipt ("Noted."), a verdict ("That matches.") or a restatement
     ("So you think X, why?") is not an opening.
   - Ask one question per turn, as one frame of `references/questions.md`: one question
     mark, and no "and" that adds a second ask. The second ask waits for the answer to the
     first. Ask for a reason ("Tell me why"), not a bare pick or yes/no. Rows 2 and 4 of
     the routing table offer picks; after a pick, ask for the idea behind it.
   - Relate the source to the Intention once per session, in the thread that bears most
     on it, with frame 8, a question that recalls the Intention in the user's words and
     names the content ("You want to '…'. What does the easing flowchart teach you about
     that?"), never as your statement of the link.
   - Record per thread, without announcing it: the item's highlight, the Examples and
     Quoted lines of the passages the user has seen, each Reaction under the passage the
     question named, an Offshoot when a reply brings in a context the source never mentions,
     and Implications (doubts and questions the source does not answer), all in the user's
     words. The answer to a thread's topic question becomes a Reaction under the thread's
     source point (`references/source-notes.md`).
6. **Move on.** A thread is done when each ask passage in it is seen, its highlight passed
   the check, row 11's offer has been made or the thread never reached it, and its source
   point has a Stance or a decline. Before moving the marker, check the thread's passages
   against the conversation and ask about any ask passage not seen, one at a time. Then
   take the Stance: when a reply in this thread already agrees or disagrees with the item,
   gives a reason and names its subject, that reply is the Stance and you ask nothing.
   Otherwise ask `<claim heading>: Do you agree? Tell me why in one sentence. Name the
   topic in your sentence.` The reply is the Stance, spelling fixed. A reply that leans on
   the question ("it", "this", "that" with no object named) gets one re-ask for a version
   that names its subject; the next reply is taken as given. A declined point has no
   Stance. Move the marker, show the thread's mention passages together, word for word,
   say what comes next, and ask the next thread's first question, all in one message. When
   the user asks to skip a thread, mark it untouched and move on.
7. **Wrap-up.** Start on the user's signal ("done", "that's everything", or a request for
   the notes), or once every thread is done. In order:
   1. Name the threads not discussed and the passages skipped. When the user asked for the
      notes without saying they are done, offer the threads once.
   2. List each Offshoot held, in the user's own short phrase, once. Ask in one message
      for each: write one sentence, keep it as they said it, or drop it.
   3. Read the Key Concepts and Mentioned definitions in `references/terms.md`. Propose
      them in one message, one line per source point you will write (Key Concepts |
      Mentioned), from that point's passages: propose a term only when the block quote or
      the user's words would lose meaning without it, at most about three per point; judge
      by the source's field and ask when it is unclear. Give each term a short reason for
      being there ("Term: why"). Add a last line for the whole source, from the passages
      not skipped, discussed or not: the vocabulary and proper names the source uses that
      no source point holds, at most about five. List each term once, at the
      point it fits most. The user chooses here, ahead of the End review: they add, drop
      or correct, and silence on a point accepts it. Done after one reply from the user, or
      a decline.
   4. Show the note for the End review (`references/end-review.md`).
   5. Ask once for a folder, then write the file. With no folder, leave the note in chat.
   6. Name up to three kept Offshoots that look worth refining in `ideate`, as a suggestion
      the user may ignore.
8. **Notes.** Read `references/source-notes.md` before drafting.

## Hard rules

- Write the author's stand as the highlight, a block quote that passed the highlight
  check, for each claim the user discussed. Add no claim the user did not discuss. A claim
  line appears only when the user asks for one at the End review, built from what they
  said and naming the author in the third person.
- Write each Reaction, Stance, Offshoot and Implication in the user's words, fixing only
  spelling: join replies on one thought and add nothing (`references/source-notes.md`).
  The Intention and the Prior belief are asked and not written.
- Keep scaffolds, candidate wordings and your own views in chat. They enter a note only
  when the user adopts them in their own words.
- Write a source point only for threads that were discussed. An undiscussed thread leaves
  no source point; only the terms the user accepts at Wrap-up step 3 reach the foot of the
  note. A Quote is written only when the user names the line; a block quote, an Example
  or a Quoted line is written only for a passage the user has seen, and these are the only
  source text the agent places on its own. A partial note is valid.
- Write the file only after the End review and a folder from the user.
- Reply in the user's language. Whatever names the source stays in the source's language
  (`references/source-notes.md`).
