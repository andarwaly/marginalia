---
name: ingest
description: "Discusses one source with the user, then drafts source notes whose claims and Implications stay in the user's words. Use when the user runs /ingest with a URL or pasted text."
disable-model-invocation: true
---

# Ingest

Discuss one source with the user until they can say, in their own words, what it claims and
what they make of it. Then draft source notes. The user supplies the claims and the
thinking; the agent supplies the source's text, a discussion partner's questions and
marked scaffolds.

If a technique skill named below is missing, stop and tell the user to install the full
marginalia set.

Terms (Thread, Intention, Prior belief, Source point, Implications, Scaffold, End review,
Wrap-up): `references/terms.md`.

## Steps

1. **Get the source.** A URL goes through `clip-article` or `clip-youtube`; pasted text is
   used as is. In plain chat, ask for the pasted text. Read all of it. If the clip says
   `captions: auto-generated`, warn once that quotes may carry transcription errors.
2. **Find the threads.** List 2–4 threads, sized for about 20–30 minutes of discussion. Each claim in a thread carries one exact
   quote from the source body (never frontmatter or an AI summary); a claim from material
   the author quotes belongs to the quoted person. Keep the quotes unseen until the user
   has answered or is stuck.
3. **Open.** Done when both questions are answered or declined. Ask two questions, one per
   line: what the user already thinks about the topic (the Prior belief), and "What makes
   you want to read this?" ("watch" for a video; the answer is the Intention). When the
   user gives no Intention, suggest one way the source could help and let them take it,
   change it or drop it. When the user says they have not read the source in full, run
   `guided-reading-technique`.
4. **Show the threads.** Order them by the Intention, else by the source's order. Show them
   as one-line chains with a progress marker and the finish line, and put the first
   question of the first thread in the same message:

   ```
   Threads: ① … [now]  ② …  ③ …
   Done when each has your claim in your own words. Then: wrap-up, notes.
   ```

   The user may reorder, add or drop threads.
5. **Discuss a thread.**
   - Open with one question that asks for the user's take, naming only the topic.
   - Name the author in the third person and mark anything of your own as yours; never
     speak as the author.
   - Read each answer (`references/reading-the-answer.md`), pick the technique, load it with
     the Skill tool the first time it is needed, and show the user only the question.
   - Open each reply with the next question, or with something the user said in an earlier
     turn that bears on the point. Refer to their last message only by a short phrase
     quoted from it. A receipt ("Noted."), a verdict ("That matches.") or a restatement
     ("So you think X, why?") is not an opening. One exception: for the user's own idea,
     the "that's yours" clause in Record, below, may come first.
   - Ask one question per turn, in plain words: one question mark, and no "and" that adds a
     second ask. The second ask waits for the answer to the first.
   - Call `scaffold-technique` when the user is about to settle (once per thread) and when
     the user is stuck.
   - Relate the thread to the Intention once, as a question that recalls the Intention in
     the user's words ("You said you're reading this to '…'. Where does this thread fit
     that?"), never as your statement of the link.
   - Follow a tangent or a cross-domain link for a turn or two with `maieutic-technique`;
     it is the user's Implication. A way the user would apply a point is an Implication too.
   - When the user cannot phrase a point, invite a rough dump in any language, then offer
     two or three candidate wordings that differ in substance, labeled as yours. The user
     picks one or rewrites it in their own words.
   - Check each claim against its quote yourself. When the user's reading of what the
     author says goes beyond or against the quote, raise it as an ordinary remark that gives
     the quote. When the user's remark fits no thread, follow
     `references/reading-the-answer.md`.
   - Record per thread: the claim in the user's words, its quote, and the user's
     Implications. Announce a record only for the user's own idea, example or application
     (not a reading of the author), in one clause: "that's yours, not <Author>'s, so it
     goes in as your Implication."
6. **Move on.** A thread is done when each claim in it that the user discussed has a claim
   line in their words that passed the quote check, the thread has been related to the
   Intention, and the scaffold offer has been made or the user moved on before settling.
   Move the marker, say what comes next, and ask the next thread's first question. When the
   user asks to skip a thread, mark it untouched and move on.
7. **Wrap-up.** Start on the user's signal ("done", "that's everything", or a request for
   the notes), or once every thread is done. In order:
   1. When threads are untouched or unfinished and the user asked for the notes without
      saying they are done, offer those threads once.
   2. Name up to three Implications that look worth refining in `ideate`, as a suggestion
      the user may ignore.
   3. Ask for the main idea. The user states it first; offer two tighter candidates only
      when their statement is long or loose.
   4. Read the Key Concepts and Mentioned definitions in `references/terms.md`. Propose
      them for every source point you will write, in one message, one line per point (Key
      Concepts | Mentioned). Key Concepts come from the quote and the discussion: propose a
      term only when the claim line or the user's words would lose meaning without it, at
      most about five per point; judge by the source's field and ask when it is unclear.
      Mentioned are the proper names in the quote, the footnotes it marks and the links in
      its paragraph. Add a last line for vocabulary the user or the main idea used that no
      source point holds; it goes on the map. Vocabulary from undiscussed threads stays
      out. The user chooses here, ahead of the End review: they add, drop or correct, and
      silence on a point accepts it. Done after one reply from the user, or a decline.
   5. Show the notes for the End review (`references/end-review.md`).
   6. Ask once for a folder, then write the files. With no folder, leave the notes in chat.
8. **Notes.** Read `references/source-notes.md` before drafting.

## Hard rules

- Build each claim line from what the user said, attribute it to the author by name in the
  third person, and add no claim the user did not make.
- Copy the Prior belief, the Intention, the main idea and the Implications word for word,
  fixing only spelling.
- Keep scaffolds, candidate wordings and your own views in chat. They enter a note only
  when the user adopts them in their own words, as an Implication.
- Quote only for threads that were discussed. An undiscussed thread leaves no trace; a
  partial note is valid.
- Write files only after the End review and a folder from the user.
- Reply in the user's language. Whatever names the source stays in the source's language
  (`references/source-notes.md`).
