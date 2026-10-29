# Ingest evals

Judged by behavior, not keywords. Each case: the setup, the expected behavior, and what
fails it. Source for all cases: a short article, "Developing Taste", clipped to the session.

## Routing

1. `/ingest https://emilkowal.ski/ui/developing-taste`
   - Expect: `clip-article` runs, then the agent asks the Prior belief and Intention
     questions, one per line.
   - Fails: the agent summarizes the article, shows quotes, or shows threads first.
2. "summarize this article: <URL>" (no slash)
   - Expect: ingest does not run (it is user-invoked).
3. "explain this simply" / "challenge my idea"
   - Expect: no skill from this repo runs.
4. A technique skill is missing (one-folder install).
   - Expect: stop with "install the full marginalia set", no improvised interview.

## Opening and threads

5. The user answers the Prior belief and Intention questions.
   - Expect: 2–4 threads as one-line chains, ordered by the Intention, with a progress
     marker, the finish line, and the first thread's first question in the same message.
   - Fails: quotes shown, headings used as the threads, or the thread list hidden.
6. The user gives no Intention.
   - Expect: the agent suggests one way the source could help and lets the user take,
     change or drop it.
7. The agent opens a thread.
   - Expect: one question asking for the user's take, naming only the topic.
   - Fails: it states what the source says, or asks two things.
8. A thread finishes.
   - Expect: the marker moves, the agent says what is next, and asks the next thread's first
     question.

## Conversation

9. Any reply during a thread.
   - Expect: it starts from the substance of the user's last message.
   - Fails: a stock opener ("Noted.", "Fixed.", "That matches the article."), or a label for
     the user's remark ("your reaction").
10. Setup: in an earlier turn the user told a bootcamp story; a later point bears on it.
    - Expect: the agent brings that story back in a question.
11. The user answers with a tangent ("this reminds me of how CLIs show help").
    - Expect: the agent follows it for a turn or two, asking what the user sees in it; it is
      recorded as an Implication; the thread resumes afterwards.
    - Fails: it parks the tangent without a reply.
12. The user says "I get it but I can't put it into words", then sends a rough dump.
    - Expect: two or three candidate wordings that differ in substance, labeled as the
      agent's; the user's final claim line is the one they pick or rewrite.
13. The user gives a tentative claim.
    - Expect: one marked example (`scaffold-technique`), at most once in the thread.
14. The user says "I'm stuck, I don't know what this paragraph is saying".
    - Expect: the ladder, one rung per turn. The user sees only the question.
    - Fails: a refusal such as "re-read the paragraph" with no further help.
15. A technique is chosen after the user's answer.
    - Expect: the user sees only the question, never "blank → guided-reading-technique" or a
      state name.
16. The user's claim goes beyond its quote.
    - Expect: an ordinary remark that gives the quote, not a scripted confirmation question.
17. Once per thread.
    - Expect: the agent relates the thread to the Intention, in conversation.
18. The user's first answer in a thread is clear and correct.
    - Expect: no verdict such as "that matches"; the next question pushes the point further.
    - Fails: the thread closes after one answer, before the Intention link.
19. The user asks to skip a thread.
    - Expect: it is marked untouched and the next thread begins.
20. The user makes a remark tied to no thread.
    - Expect: the agent quotes the nearest passage and asks; a personal read is kept as an
      Implication.

## Wrap-up and notes

21. The user says "done" with one thread untouched.
    - Expect: the offer on the untouched thread is skipped; suggestions for `ideate`, the
      main idea, the End review and the folder question still run.
22. The agent asks for the main idea.
    - Expect: the user states it first; the agent offers candidates only if the statement is
      long or loose.
23. The End review.
    - Expect: the full notes in fenced blocks; the user's edits are applied; files are
      written only after the user has no further edits and has named a folder.
    - Fails: files written before the review, or a per-statement confirmation question.
24. The notes.
    - Expect: Prior belief, Intention, main idea and Implications appear word for word; every
      claim line names the author in the third person; every quote appears verbatim in the
      clip.
25. A scaffold, a candidate wording or the agent's own view appears in chat.
    - Expect: none appears in any note unless the user adopted it in their own words as an
      Implication.
26. The user writes in Indonesian ("Barusan lewat di threads tentang taste…").
    - Expect: the agent's questions are in Indonesian; quotes, titles, filenames (with the
      `§` prefix) and claim lines stay in English; the Prior belief, Intention, main idea and
      Implications keep the user's Indonesian words; section headings stay English.
27. Only two of three threads were discussed.
    - Expect: the coverage list marks the third untouched, and it leaves no quote or source
      point in the notes.
