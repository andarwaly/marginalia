---
name: ingest
description: "Discusses one source with the user, then drafts source notes whose claims and Implications stay in the user's words. Use when the user runs /ingest with a URL or pasted text."
disable-model-invocation: true
---

# Ingest

Discuss one source with the user until they have met each passage and said what they make
of it. Then draft source notes. The user supplies the claims and the thinking; the agent
supplies the source's text, a discussion partner's questions, and marked views and
scaffolds.

If a technique skill named below is missing, stop and tell the user to install the full
marginalia set.

Terms (Thread, Passage, Passage tag, Seen, Intention, Prior belief, Source point,
Implications, Key Concepts, Mentioned, Reading state, Meet and return, Rider, Scaffold, End
review, Wrap-up): `references/terms.md`.

## Steps

1. **Get the source.** A URL goes through `clip-article` or `clip-youtube`; pasted text is
   used as is. In plain chat, ask for the pasted text. Read all of it. If the clip says
   `captions: auto-generated`, warn once that quotes may carry transcription errors.
2. **List the passages, then the threads.** Walk the source from the first sentence to the
   last and list every passage (paragraphs, examples, code blocks, tables, images, demos),
   each tagged ask or mention (`references/passages.md`). Group them into 2–4 threads,
   sized for about 20–30 minutes; a thread holds about four ask passages, with sibling
   examples merged into one. Each claim in a thread carries one exact quote from the
   source body (never frontmatter or an AI summary); a claim from material the author
   quotes belongs to the quoted person. Keep the quotes unseen until the user has answered
   or is stuck. Done when every passage sits in a thread or is skipped with a reason.
3. **Open.** Done when both questions are answered or declined. Ask two questions, one per
   line: what the user already thinks about the topic (the Prior belief), and "What makes
   you want to read this?" ("watch" for a video; the answer is the Intention). When the
   user gives no Intention, suggest one way the source could help and let them take it,
   change it or drop it. When the user says they have not read the source in full, run
   `guided-reading-technique`.
4. **Show the threads.** Order them by the Intention, else by the source's order. Show them
   as one-line chains with a progress marker, the examples each thread holds (named by a
   short label, not their content) and the finish line, and put the first question of the
   first thread in the same message:

   ```
   Threads: ① … (the demo) [now]  ② …  ③ … (the table)
   Done when each thread has your take. Then: wrap-up, notes.
   ```

   The user may reorder, add or drop threads.
5. **Discuss a thread.**
   - Open with one question that asks for the user's take, naming only the topic.
   - Name the author in the third person and speak of your own views in the first person;
     never speak as the author. The marker for a view is in `reading-the-answer.md`; a
     scaffold always opens with its own full marker (`scaffold-technique`).
   - Every question is about a passage of the source. The user's own idea is connected to
     the source and recorded; working it out is `ideate`'s job.
   - Read each answer with `references/reading-the-answer.md`: take the first matching row
     and show the user only the question. Show each ask passage after the user's take
     (`references/passages.md`).
   - Open each reply with the next question, or with something the user said in an earlier
     turn that bears on the point. Refer to their last message only by a short phrase
     quoted from it. A receipt ("Noted."), a verdict ("That matches.") or a restatement
     ("So you think X, why?") is not an opening.
   - Ask one question per turn, in plain words: one question mark, and no "and" that adds a
     second ask. The second ask waits for the answer to the first.
   - Relate the thread to the Intention once, as a question that recalls the Intention in
     the user's words ("You said you're reading this to '…'. Where does this thread fit
     that?"), never as your statement of the link.
   - Record per thread, without announcing it: the claim in the user's words, its quote,
     and the user's Implications. The user's answer to a thread's opening question becomes
     the claim line or an Implication (`references/source-notes.md`).
6. **Move on.** A thread is done when each ask passage in it is seen, each claim in it that the user discussed has a claim line that passed the
   quote check, the thread has been related to the Intention, and row 11's offer has been
   made or the thread never reached it. Show the thread's mention passages together, word
   for word, in one message with no question when the marker moves. Before moving the
   marker, check the thread's passages against the conversation and ask about any ask
   passage not seen, one at a time. Move the marker, say what comes next, and ask the next
   thread's first question. When the user asks to skip a thread, mark it untouched and move
   on.
7. **Wrap-up.** Start on the user's signal ("done", "that's everything", or a request for
   the notes), or once every thread is done. In order:
   1. Name the threads and passages not discussed. When the user asked for the notes
      without saying they are done, offer them once.
   2. Name up to three Implications that look worth refining in `ideate`, as a suggestion
      the user may ignore.
   3. Ask for the main idea. The user states it first; offer two tighter candidates only
      when their statement is long or loose.
   4. Read the Key Concepts and Mentioned definitions in `references/terms.md`. Propose
      them in one message, one line per source point you will write (Key Concepts |
      Mentioned), from that point's passages: propose a term only when the claim line or
      the user's words would lose meaning without it, at most about five per point; judge
      by the source's field and ask when it is unclear. Give each term a short reason for
      being there ("Term: why"). Add a last line for the map, from
      the whole passage list, discussed or not: the vocabulary and proper names the source
      uses that no source point holds, at most about eight. List each term once, at the
      point it fits most. The user chooses here, ahead of the End review: they add, drop
      or correct, and silence on a point accepts it. Done after one reply from the user, or
      a decline.
   5. Show the notes for the End review (`references/end-review.md`).
   6. Ask once for a folder, then write the files. With no folder, leave the notes in chat.
8. **Notes.** Read `references/source-notes.md` before drafting.

## Hard rules

- Build each claim line from what the user said, or from what its quote supports when the
  user pasted the passage. Attribute it to the author by name in the third person, and add
  no claim the user did not discuss.
- Copy the Prior belief, the Intention, the main idea and the Implications word for word,
  fixing only spelling.
- Keep scaffolds, candidate wordings and your own views in chat. They enter a note only
  when the user adopts them in their own words, as an Implication.
- Quote only for threads that were discussed. An undiscussed thread leaves no source point
  or quote; only the terms the user accepts at Wrap-up step 4 reach the map. A partial note
  is valid.
- Write files only after the End review and a folder from the user.
- Reply in the user's language. Whatever names the source stays in the source's language
  (`references/source-notes.md`).
