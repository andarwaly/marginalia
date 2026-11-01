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
   - Expect: it opens with the next question, or with something the user said in an earlier
     turn that bears on the point.
   - Fails: a stock opener ("Noted.", "Fixed.", "That matches the article."), a restatement
     of the user's message ("Your point is that…", "So you think X, why?"), or a label for the user's remark ("your
     reaction").
10. Setup: in an earlier turn the user told a bootcamp story; a later point bears on it.
    - Expect: the agent brings that story back in a question.
11. The user answers with a tangent ("this reminds me of how CLIs show help").
    - Expect: meet and return: the agent's view, marked as its own; then the author's passage
      that bears on it, if unseen; then one question. It is recorded as an Implication, and
      the thread resumes afterwards.
    - Fails: it parks the tangent without a reply, or labels it ("that's yours").
12. The user says "I get it but I can't put it into words", then sends a rough dump.
    - Expect: two or three candidate wordings that differ in substance, labeled as the
      agent's; the user's final claim line is the one they pick or rewrite.
13. The user gives a tentative claim.
    - Expect: one marked example (`scaffold-technique`), at most once in the thread.
14. The user says "I'm stuck, I don't know what this paragraph is saying".
    - Expect: the ladder, one rung per turn, entering at the rung that matches what the user
      has said. The user sees only the question. A first plain "no idea" gets rung 1, the
      passage named by its opening words, not the full ladder.
    - Fails: a refusal such as "re-read the paragraph" with no further help.
15. A technique is chosen after the user's answer.
    - Expect: the user sees only the question, never "row 2", "guided-reading-technique" or
      a row number.
16. The user's claim goes beyond its quote (it says more than the quote supports).
    - Expect: an ordinary remark that gives the quote, not a scripted confirmation question.
    - Fails: "that's wrong", or silence on the extra part.
17. Once per thread.
    - Expect: the agent relates the thread to the Intention as a question the user answers.
    - Fails: the agent states the link itself ("It bears on your Intention…").
18. The user's first answer in a thread is clear and correct.
    - Expect: no verdict such as "that matches"; the next question goes to the next unseen
      ask passage, the Intention question, or one push (row 12's order).
    - Fails: the thread closes after one answer, before the Intention link.
19. The user asks to skip a thread.
    - Expect: it is marked untouched and the next thread begins.
20. The user makes a remark tied to no thread.
    - Expect: the agent quotes the nearest passage and asks; a personal read is kept as an
      Implication.

## Wrap-up and notes

21. The user says "done" with one thread untouched.
    - Expect: the offer on the untouched thread is skipped; suggestions for `ideate`, the
      main idea, the Key Concepts and Mentioned proposal, the End review and the folder
      question still run.
22. The agent asks for the main idea.
    - Expect: the user states it first; the agent offers candidates only if the statement is
      long or loose.
23. The End review.
    - Expect: the full notes in fenced blocks; the user's edits are applied; files are
      written only after the user has no further edits and has named a folder.
    - Fails: files written before the review, or a per-statement confirmation question.
24. The notes.
    - Expect: Prior belief, Intention and main idea appear word for word; Implications keep
      the user's words; every claim line names the author in the third person; every quote appears verbatim in the
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
28. The user's own idea touches a passage the user has not seen.
    - Expect: the agent's view in first person (agree or differ, cited only if it can
      vouch, no marker when it does not differ from the author), then the author's passage
      and how it sits with the idea, then one question about that passage. The idea is
      recorded without announcement.
    - Fails: "That's yours, not <Author>'s…", a bare restatement, no return to the source,
      a second ask ("…and what…?"), a question about the user's idea instead of the
      passage, or a "From my own knowledge, not <Author>'s:" marker on a view that does
      not differ from the author.
29. A scaffold or any question in a thread.
    - Expect: one ask in plain words; a second ask waits for the answer.
    - Fails: "X, and what does that say about Y?" in one turn.
30. Wrap-up, after the main idea.
    - Expect: one message proposes Key Concepts (singular form, at most about five per
      point) and Mentioned (names, works, tools, footnote links), one line per point, each
      term with a short reason ("Term: why"); the
      user's reply, or silence on a point, decides the notes; the step ends after that one
      reply.
    - Fails: the agent chooses them without asking, asks a second round, or leaves out a
      footnote link the user can see in the clip.
31. The opening question.
    - Expect: "What makes you want to read this?" ("watch" for a video), one per line with
      the Prior belief question.
32. A UX article explains a design decision with "affordance".
    - Expect: "Affordance" is proposed as a Key Concept, in the singular.
    - Fails: it is dropped because it is abstract and unnamed.
33. A mining article on Balikpapan uses "coal", "seam" and "sediment layer".
    - Expect: "Coal", "Seam" and "Sediment layer" are proposed as Key Concepts, and
      "Balikpapan" as Mentioned.
    - Fails: "Coal" is skipped as too concrete, or "Balikpapan" is filed as a Key Concept.
34. Wrap-up: the source holds a term in a thread the user never discussed.
    - Expect: the last line of the proposal offers it for the map, and the user may drop it;
      no source point or quote exists for that thread.
    - Fails: a source point or quote for the undiscussed thread.
35. A named framework ("Occam's razor") and a named place that is also a field term
    ("Kutai Basin").
    - Expect: "Occam's razor" is a Key Concept and its originator is Mentioned; "Kutai
      Basin" is Mentioned and "Basin" is a Key Concept.
36. The source has an example, a code block, a table and a demo.
    - Expect: the thread list names the examples each thread holds by a short label; each
      ask passage is shown after the user's take and discussed ("what does it show?",
      then why this one); sibling examples merge into one item, about four ask passages per thread.
    - Fails: an example or code block never comes up, or the label gives away its content.
37. A demo or image the clip dropped ("the animation below").
    - Expect: the agent names it by its text and asks the user to open it at the source and
      say what they see.
    - Fails: the agent describes a demo it cannot see.
38. The user pastes the passage.
    - Expect: one question, what they make of it; the passage is not shown again.
    - Fails: the agent shows the passage again or asks for it in the user's own words.
39. The user puts the passage in other words, same meaning.
    - Expect: the agent accepts it, shows the author's exact words, and asks what they make
      of it. It does not ask for a restatement in their own words.
    - Fails: "put that in your own words", or accepting without showing the exact text.
40. The user's reading goes against a passage.
    - Expect: `guided-reading-technique` for the recheck only: the passage named by its
      opening words, a request to look again. A paste or other words are accepted.
    - Fails: "that's wrong", the exact quote dropped as a correction, or a pressing
      contradiction question.
41. An ask passage of a thread was never seen when the user seems done with it.
    - Expect: the agent asks about it, one at a time, before the marker moves; the thread's
      mention passages appear together, with no question.
    - Fails: the marker moves with an ask passage unseen, or every context paragraph gets
      its own question.
42. Wrap-up.
    - Expect: the agent names the threads and passages not discussed and offers them once;
      the last line of the Key Concepts and Mentioned proposal comes from the whole passage
      list.
43. The source has an example the author gives (a demo, a comparison, a code block).
    - Expect: it is discussed in a thread before the notes; the agent never offers it as its
      own knowledge.
    - Fails: the agent says "From my own knowledge, not <Author>'s" about something the
      source contains.
44. The user's own idea touches only passages already seen.
    - Expect: the agent's view, the seen passage named by its opening words (not quoted
      again), then one question.
    - Fails: the passage is quoted again, or the reply has no pointer back.
45. The agent's view cites a work.
    - Expect: a citation only for a work it can name exactly, never a URL; otherwise no
      citation.
    - Fails: an invented author, year or link.
46. The author already covers the user's point.
    - Expect: the agent treats it as a return and shows the author's passage; it does not
      offer it as "From my own knowledge".
    - Fails: it offers the author's own example as its own knowledge (the tabular-nums
      case).
47. The End review.
    - Expect: below the notes, a list of every bracketed referent the agent added to an
      Implication, for the user to confirm or reword.
48. The user asks a question the source does not answer ("Does he have a way for agencies?").
    - Expect: the agent says the source does not cover it, and the question becomes an Open
      Question in the notes.
    - Fails: the question is dropped.
49. The user pastes a passage and adds an idea of their own.
    - Expect: meet and return; the pasted passage is named by its opening words, not quoted
      again.
    - Fails: "what do you make of it?" about a passage the user has just answered.
50. The user rewrites a passage and part of it is wrong.
    - Expect: a recheck of the wrong part only; nothing is accepted, and the passage stays
      unseen.
51. A tentative claim that misreads a passage.
    - Expect: the recheck; the scaffold offer is not spent, and a later tentative claim in
      the thread gets the offer.
52. A clear answer, every ask passage of the thread seen, the Intention question asked.
    - Expect: one push (a reason or a consequence), then the marker moves.
    - Fails: the agent loops on the same thread.
53. The user states their own idea and says they are stuck in the same message.
    - Expect: the ladder; the idea is recorded as an Implication and not announced.
54. The user asks a question the source answers.
    - Expect: the passage named by its opening words, then "what do you make of it?".
    - Fails: the agent answers from its own knowledge.
55. The user says "I'm stuck, I can't put it into words".
    - Expect: the ladder from the rung that fits (row 2), not candidate wordings.
    - Fails: candidate wordings or a rough-dump invitation before any ladder rung.
56. The user says "skip this one" about a thread.
    - Expect: the thread is marked untouched and the next thread begins.
    - Fails: the ladder runs on "skip".
57. A doubt phrased as a question ("Isn't that just practice?").
    - Expect: meet and return (the agent's view, the author's passage if unseen, one
      question).
    - Fails: "what do you make of it?" about a passage, with no view from the agent.
58. The user says "I think taste is mostly practice" (a complete claim, stated tentatively).
    - Expect: the scaffold offer once, when it has not been made in this thread.
    - Fails: a feynman-style "say it again" for a claim that is already complete.
59. The user says "Something about practice? Maybe?" (no claim stated yet).
    - Expect: `feynman-technique`, one plain-language question built on what they said.
    - Fails: the ladder, or the scaffold offer.
60. The user says "Taste is innate, and practice builds it, so you just have it."
    - Expect: `self-explanation-technique`, a question asking how the two parts fit.
    - Fails: "that's wrong" or a guided-reading recheck.
61. Clear answers keep coming after the Intention question and one push.
    - Expect: after the single push in the thread, the step 6 checks run and the marker moves.
    - Fails: a push on every later answer.
62. The user disagrees with the author and the agent sides with the user.
    - Expect: the view opens "From my own knowledge, not <Author>'s:", then the author's
      passage, then one question about that passage.
    - Fails: no marker, or a marker on a view that agrees with the author.
63. The user's own idea (a rule they would write, a value, a design) after a return.
    - Expect: the idea is recorded; the question is about the author's next passage or the
      returned one.
    - Fails: "How would you write that rule?", "What would you set it to?" or any further
      probing of the user's design (that is `ideate`).
64. An ask passage is a table, a list of rules or a code block with many parts.
    - Expect: one question about the whole passage ("what does this table show?"); the
      reason for choosing it waits for the answer.
    - Fails: a question per row or rule, or a passage shown only as a bridge to a question
      about the user's own idea and then counted as seen.
65. A thread's passage was shown, but the user's reply was about something else.
    - Expect: the passage is not seen; the agent asks about it before the marker moves.
    - Fails: the marker moves, and the coverage list calls it "shown but not discussed".
66. Wrap-up proposal and notes: Key Concepts and Mentioned.
    - Expect: each term carries a reason in the proposal; in the notes the entry reads
      `- Term: what it is, and why it is here`, with no `※` and no wikilink.
    - Fails: a bare term, a wikilink, or a definition from outside the source.
67. A source point whose passage holds an example, code block, table or flowchart.
    - Expect: an `## Example` section between the quote and Key Concepts, word for word
      with fenced blocks and a one-line label; a point with no example has no section.
    - Fails: a paraphrased example, a missing fence, or an empty Example section.
68. The user answers a pick question ("b is closest, the pointer pushes them away").
    - Expect: the Implication stands alone: "[The Linear logo demo]: the pointer pushes the
      particles away…", the user's wording kept, the referent in square brackets.
    - Fails: the bare reply pasted, or a paraphrase that changes the user's words.
69. The user gives three replies on one thought.
    - Expect: one bullet, in the user's order, with no sentence of the agent's between.
    - Fails: three fragments, or a merged bullet that reorders or rewrites the thought.
70. The user replies "Yes." or picks a candidate wording with no thought of their own.
    - Expect: "Yes." folds into the bullet it answers, or is dropped; a bare pick is dropped,
      and the wording enters only as the user's own restatement.
    - Fails: "Yes." as its own bullet, or the agent's wording in a note.
71. Any Implication, read alone.
    - Expect: a reader with no question and no chat can tell what it is about; no bracket
      holds an opinion.
    - Fails: a pronoun with no referent ("it", "so"), a bracket with an adjective or a view
      ("[Kowalski's clumsy demo]"), or a joined bullet with words added or dropped.
72. A question in a thread.
    - Expect: it invites a thought ("What do you make of…"); after a pick, the next
      question asks for the idea behind it.
    - Fails: a run of picks and yes/no questions. Rows 2 and 4 may offer a pick; that turn
      is not a failure.
73. The vault's AGENTS.md names a note template.
    - Expect: the template sets filenames, frontmatter and headings; the content rules
      (claim line, quote, Implications) still apply.
    - Fails: the agent ignores the template, or drops a content rule because the template
      does not repeat it.
