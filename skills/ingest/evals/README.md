# Ingest evals

Judged by behavior, not keywords. Each case: the setup, the expected behavior, and what
fails it. Source for all cases: a short article, "Developing Taste", clipped to the session.

## Routing

1. `/ingest https://emilkowal.ski/ui/developing-taste`
   - Expect: `clip-article` runs, then the agent asks the Prior belief and Intention
     questions, one per line.
   - Fails: the agent summarizes the article, shows passages, or shows threads first.
2. "summarize this article: <URL>" (no slash)
   - Expect: ingest does not run (it is user-invoked).
3. "explain this simply" / "challenge my idea"
   - Expect: no skill from this repo runs.
4. A technique skill is missing (one-folder install).
   - Expect: stop with "install the full marginalia set", no improvised interview.

## Opening and threads

5. The user has set the Spine.
   - Expect: one thread per Spine item as one-line chains, ordered by the Intention, with a
     progress marker, the finish line, and the first thread's first question in the same
     message.
   - Fails: passages shown, headings used as the threads, or the thread list hidden.
6. The user gives no Intention.
   - Expect: the agent suggests one way the source could help and lets the user take,
     change or drop it.
7. The agent opens a thread on a Spine item it added.
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
      that bears on it, if unseen; then one question. It is recorded as an Offshoot (it brings in
      a context the source never mentions), and the thread resumes afterwards.
    - Fails: it parks the tangent without a reply, or labels it ("that's yours").
12. The user says "I get it but I can't put it into words", then sends a rough dump.
    - Expect: two or three candidate wordings that differ in substance, labeled as the
      agent's; the user's Reaction is the wording they pick or rewrite.
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
16. The user's claim goes beyond its highlight (it says more than the highlight supports).
    - Expect: an ordinary remark that gives the highlight's words, not a scripted
      confirmation question.
    - Fails: "that's wrong", or silence on the extra part.
17. Once per session.
    - Expect: the agent relates the source to the Intention as a question the user answers,
      in the thread that bears most on it.
    - Fails: the agent states the link itself ("It bears on your Intention…").
18. The user's first answer in a thread is clear and correct.
    - Expect: no verdict such as "that matches"; the next question goes to the next unseen
      ask passage, the Intention question, or one push (row 12's order).
    - Fails: the thread closes after one answer with an ask passage unseen.
19. The user asks to skip a thread.
    - Expect: it is marked untouched and the next thread begins.
20. The user makes a remark tied to no thread.
    - Expect: the agent quotes the nearest passage and asks; a personal read is kept as a
      Reaction under that passage.

## Wrap-up and notes

21. The user says "done" with one thread untouched.
    - Expect: the offer on the untouched thread is skipped; the Key Concepts and Mentioned
      proposal, the End review, the folder question and, after the file, the suggestions for
      `ideate` still run.
22. Wrap-up.
    - Expect: the agent does not ask for a main idea and the note has none.
    - Fails: a main-idea question, or a main-idea section in the note.
23. The End review.
    - Expect: the full note in a fenced block; the user's edits are applied; the file is
      written only after the user has no further edits and has named a folder.
    - Fails: files written before the review, or a per-statement confirmation question.
24. The note.
    - Expect: the Intention and the Prior belief are not in the note; Reactions, Stances,
      Offshoots and Implications keep the user's words; every source point opens with the
      highlight as a block quote and carries a locator; every block quote, Example, Quoted
      line, Quote and code block appears verbatim in the clip.
25. A scaffold, a candidate wording or the agent's own view appears in chat.
    - Expect: none appears in any note unless the user adopted it in their own words.
26. The user writes in Indonesian ("Barusan lewat di threads tentang taste…").
    - Expect: the agent's questions are in Indonesian; quotes, titles, filenames, claim
      headings, block quotes, Examples and Quoted lines stay in English; Reactions, Stances,
      Offshoots and Implications keep the user's Indonesian words; section headings stay
      English.
27. Only two of three threads were discussed.
    - Expect: the coverage list marks the third untouched, and it leaves no source
      point, locator or quote in the note.
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
30. Wrap-up, after the Offshoots.
    - Expect: one message proposes Key Concepts (singular form, at most about three per
      point, with the parts of a structure the author lists outside that count) and Mentioned (names, works, tools, footnote links), one line per point, each
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
    - Expect: the last line of the proposal offers it for the whole source, and the user may
      drop it; no source point or locator exists for that thread.
    - Fails: a source point or locator for the undiscussed thread.
35. A named framework ("Occam's razor") and a named place that is also a field term
    ("Kutai Basin").
    - Expect: "Occam's razor" is a Key Concept and its originator is Mentioned; "Kutai
      Basin" is Mentioned and "Basin" is a Key Concept.
36. The source has an example, a code block, a table and a demo.
    - Expect: the thread list names the examples each thread holds by a short label; at most
      one example per thread is an ask passage, shown with a frame question ("What is X
      for?", "What do you see in X?"), then why this one (frame 5); the others are shown as
      mentions.
    - Fails: an example gets a question beyond the one chosen, unless the user took it up, or
      the label gives away its content.
37. A demo or image the clip dropped ("the animation below").
    - Expect: the agent names it by its text and asks the user to open it at the source, with
      what to look at named (frame 3).
    - Fails: the agent describes a demo it cannot see.
38. The user pastes the passage.
    - Expect: one question, frame 2 ("Do you agree? Tell me why."); the passage is not shown
      again.
    - Fails: the agent shows the passage again or asks for it in the user's own words.
39. The user puts the passage in other words, same meaning.
    - Expect: the agent accepts it, shows the author's exact words, and asks frame 2. It
      does not ask for a restatement in their own words.
    - Fails: "put that in your own words", or accepting without showing the exact text.
40. The user's reading goes against a passage.
    - Expect: `guided-reading-technique` for the recheck only: the passage named by its
      opening words, a request to look again. A paste or other words are accepted.
    - Fails: "that's wrong", the highlight's words given as a correction, or a pressing
      contradiction question.
41. An ask passage of a thread was never seen when the user seems done with it.
    - Expect: the agent asks about it, one at a time, before the marker moves; the thread's
      mention passages appear together, with no question.
    - Fails: the marker moves with an ask passage unseen, or every context paragraph gets
      its own question.
42. Wrap-up.
    - Expect: the agent names the threads not discussed and the passages skipped, and offers
      the threads once;
      the last line of the Key Concepts and Mentioned proposal comes from the whole passage
      list.
43. The source has an example the author gives (a demo, a comparison, a code block).
    - Expect: it is shown in its thread before the notes; the agent never offers it as its
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
    - Expect: below the note, a list of every block quote, Example and Quoted line the agent
      placed, for the user to keep or cut, and each source point with no Stance.
48. The user asks a question the source does not answer ("Does he have a way for agencies?").
    - Expect: the agent says the source does not cover it, and the question is kept as the
      user's own bullet, word for word, ending in its question mark.
    - Fails: the question is dropped.
49. The user pastes a passage and adds an idea of their own.
    - Expect: meet and return; the pasted passage is named by its opening words, not quoted
      again.
    - Fails: a question about a passage the user has just answered.
50. The user rewrites a passage and part of it is wrong.
    - Expect: a recheck of the wrong part only; nothing is accepted, and the passage stays
      unseen.
51. A tentative claim that misreads a passage.
    - Expect: the recheck; the scaffold offer is not spent, and a later tentative claim in
      the thread gets the offer.
52. A clear answer, every ask passage of the thread seen, no Intention question due here.
    - Expect: one push (a reason or a consequence), then the marker moves.
    - Fails: the agent loops on the same thread.
53. The user states their own idea and says they are stuck in the same message.
    - Expect: the ladder; the idea is recorded as an Implication and not announced.
54. The user asks a question the source answers.
    - Expect: the passage shown, then frame 1 ("In your own words, what does this line
      say?").
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
    - Fails: a question about a passage, with no view from the agent.
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
    - Expect: one question about the whole passage ("What is this table for?"); the
      reason for choosing it waits for the answer.
    - Fails: a question per row or rule, or a passage shown only as a bridge to a question
      about the user's own idea and then counted as seen.
65. A thread's passage was shown, but the user's reply was about something else.
    - Expect: the passage is not seen; the agent asks about it before the marker moves.
    - Fails: the marker moves, and the coverage list calls it "shown but not discussed".
66. Wrap-up proposal and notes: Key Concepts and Mentioned.
    - Expect: each term carries a reason in the proposal; in the note the entry reads
      `- Term: what it is, and why it is here`, once, at the foot, with no `※` and no
      wikilink.
    - Fails: a bare term, a wikilink, or a definition from outside the source.
67. A source point whose seen passage holds a code block, a table or a flowchart.
    - Expect: for code, a fenced block under its example label, word for word, with the
      language tag; a point with no code has none. A table or flowchart the source shows as a
      code block is copied as code; one shown any other way is not copied, and what the user
      said about it is a Reaction.
    - Fails: paraphrased code, a missing fence, a table or flowchart copied from outside a
      code block, or an empty `## Example` section.
68. The user answers a pick question ("b is closest, the pointer pushes them away").
    - Expect: the reply is kept under the passage the question named, in the user's
      wording, with nothing added.
    - Fails: the bare reply left with no place, a paraphrase that changes the user's words, or
      a bracketed referent.
69. The user gives three replies on one thought.
    - Expect: one bullet, in the user's order, with no sentence of the agent's between.
    - Fails: three fragments, or a merged bullet that reorders or rewrites the thought.
70. The user replies "Yes." or picks a candidate wording with no thought of their own.
    - Expect: "Yes." folds into the bullet it answers, or is dropped; a bare pick is dropped,
      and the wording enters only as the user's own restatement.
    - Fails: "Yes." as its own bullet, or the agent's wording in a note.
71. Any Reaction, Stance, Offshoot or Implication.
    - Expect: the user's words, spelling fixed, placed as the layout says, with no word added
      or dropped and no bracket, tag or wikilink.
    - Fails: a bracketed referent, an added tag or link, or a joined bullet with words added
      or dropped.
73. The vault's AGENTS.md names a note template.
    - Expect: the template sets filenames, frontmatter and headings; the content rules
      (block quote, locator, Stance, Offshoots) still apply.
    - Fails: the agent ignores the template, or drops a content rule because the template
      does not repeat it.
74. The note's layout.
    - Expect: one note for the source. Frontmatter holds `author`, `published` and `url`;
      loose Implications and Quotes sit under the title; each source point is a `##` heading
      of five to nine words, with no author name and none of `: # ^ [ ] | \ /`, then a block
      quote, a locator, labelled Examples with Reactions, and a Stance; `## Beyond the
      source` follows the last point; Key Concepts and Mentioned sit once at the foot; the
      agent writes no `## What I think`.
    - Fails: a separate file per source point, a map note, an author name in a heading, Key
      Concepts repeated under each point, or a Why I'm here, main idea or Open Questions
      section.
75. Locator and highlight.
    - Expect: every source point opens with the highlight as a block quote
      `> words - [[Name]]`, then a locator on the next line (a linked `[mm:ss]` for a video,
      the nearest heading for an article); no claim line unless the user asked for one.
    - Fails: a source point with no block quote or locator, a paraphrase inside the block
      quote, or a locator that points at nothing.
76. The user names a line to keep at the End review.
    - Expect: `"text" - [[Name]]`, word for word from the clip, under the source point it
      relates to or below the title; Name is whoever said it.
    - Fails: a Quote the user did not name, a paraphrase, or the author named for a line the
      author quotes from someone else.
77. A doubt or question that fits no source point.
    - Expect: it sits below the title, before the first source point.
    - Fails: it is dropped, or placed under an unrelated source point.
78. A seen prose example, then an example the user never engaged with.
    - Expect: an `Example:` line for the seen one, word for word from the clip, under its own
      `####` label inside the point it illustrates; none for the other.
    - Fails: a paraphrased example, an example the user did not see, or an example under the
      wrong point.
79. An image or demo example the clip dropped.
    - Expect: its caption or alt text under `Example:`, flagged in the After-the-block check
      as not source text.
    - Fails: a description the agent wrote, or no flag.
80. The author quotes a person in a seen passage.
    - Expect: `Quoted: Person says "words"` under the point, word for word, naming the quoted
      person.
    - Fails: a paraphrase, or the author named for the quoted person's words.
81. A line the user names as a Quote is also the author's quotation of someone.
    - Expect: it is written once, as the Quote, with no `Quoted:` duplicate.
    - Fails: the line written twice.
82. The user raises a question the source answers and a gap it leaves.
    - Expect: the gap is the user's bullet, word for word, ending in its question mark; no
      Open Questions section.
    - Fails: a section of questions, or the question reworded.

## Stance, Reactions, Offshoots

83. The user reacts to the easing flowchart, then to the duration table, in one thread.
    - Expect: each reaction sits directly under its own labelled Example (`#### Decision
      tree`, `#### Grouped elements + Range`), with no agent text between.
    - Fails: the reactions in one flat list after all the examples, or a reaction under the
      wrong example.
84. A thread closes, and the user has already said "Agree, domain expertise makes the shaping
    precise" about its item.
    - Expect: that reply is the Stance and no question is asked; it appears once in the note.
    - Fails: "Do you agree?" asked again, or the same thought as both a Reaction and a Stance.
84a. A thread closes with no agreement or disagreement stated.
    - Expect: one line, "<claim heading>: Do you agree? Tell me why in one sentence. Name the
      topic in your sentence.", before the marker moves.
    - Fails: "makes sense without this chat", or the marker moving first.
85. The user's Stance reply leans on the question ("it makes sense because of that").
    - Expect: one re-ask for a version that names its subject; the next reply is taken as
      given and written in the user's words.
    - Fails: no re-ask, a second re-ask, or the agent writing the sentence for the user.
86. The user declines a Stance.
    - Expect: that source point has no `Stance:` line, and the After-the-block list names it.
    - Fails: a Stance the agent wrote, or a placeholder line.
87. A reply brings in a context the source never mentions (Japan's UI preference, an
    on-the-go meeting app).
    - Expect: the agent holds it silently as an Offshoot and the thread resumes; at Wrap-up
      it lists each Offshoot once, in the user's own short phrase, and asks in one message
      for each: write one sentence, keep it as said, or drop it.
    - Fails: the Offshoot lost in the Reactions, announced mid-thread, the list shown twice,
      or no way to keep it as said.
88. The note after Wrap-up with two Offshoots.
    - Expect: `## Beyond the source` after the last source point, one bullet per Offshoot in
      the user's sentence or original words, each ending `From: <claim heading>` as plain text; a dropped
      Offshoot is not written.
    - Fails: an Offshoot under a source point, a wikilink in `From:`, or a rewritten sentence.
89. A source point is drafted.
    - Expect: the heading, the highlight as a block quote with its attribution, a locator,
      then labelled Examples with Reactions, Quoted lines, the Stance, and doubts.
    - Fails: a paraphrase in place of the block quote, or a claim line the user did not ask
      for.
90. Two passages state the same Spine item.
    - Expect: one source point, the highlight written once.
    - Fails: two source points for one item.
91. Every question in a session.
    - Expect: each is one frame of `questions.md`, fifteen words or fewer plus the shown
      object, with one question mark.
    - Fails: "What do you make of", "sit with", "where does … fit", "draws the line", "part
      ways", "thread" or "take" as a noun in a question.
92. A question about a passage.
    - Expect: the question names its object in the same sentence (a line shown, opening
      words, a caption, a row's text); a claim passage is shown whole.
    - Fails: "that step", "the person doing it" or "that last line" with no object beside it.
93. A question that needs the author's wording (frames 1 to 8).
    - Expect: the author's line shown first, then the frame. Only frames 0 and 9 are asked
      before the passage is met.
    - Fails: a passage described vaguely so as to keep it hidden.
94. The user says "what do you mean?" or "I didn't get your question".
    - Expect: the object shown and a plainer question, with no defence of the first; from then
      on in the session every question shows the author's line first.
    - Fails: the same question repeated, a defence, or a return to take-first questions.
95. The Intention link.
    - Expect: frame 8, quoting the Intention and naming the content ("What does the easing
      flowchart teach you about that?"), once per session.
    - Fails: the same question in a second thread, "Where does this thread fit that?" or
      "what we just covered".
96. Across a session's replies.
    - Expect: a quoted phrase of the user's opens a reply only when it is the reason for the
      next passage, at most one reply in four; the others open on the passage or question.
    - Fails: `You said "…"` followed by an unrelated "Next, he…", or a restatement of the
      user's reply.

## Spine

97. A video states a formula and names four layers, and the user lists two other ideas at
    step 4.
    - Expect: frame 9 is asked once; the user's lines come first in their words; the formula
      and the layers appear under "Also in the source:" with locators, before the threads.
    - Fails: the agent shows its list first, or a named structure is left to Key Concepts.
98. The user says they have not read the source.
    - Expect: the agent's draft, marked as its own, and `guided-reading-technique`.
    - Fails: frame 9 pressed again.
99. A long source with many claims.
    - Expect: three to six Spine items, one thread and one source point each; a passage that
      repeats an item is skipped or merged.
    - Fails: a source point per claim, or a repeat asked about again.
100. The user named a Spine item.
     - Expect: its thread opens on the highlight with frame 2, and the user's line is a
       Reaction under that highlight.
     - Fails: frame 0 or frame 1 asks for what the user's line already gave.
101. The user takes up a mention passage ("extending can be complex too").
     - Expect: it is discussed for that turn, and the reply sits under the Spine item the
       passage supports.
     - Fails: the reply is lost, or the passage becomes its own source point.
102. A question whose answer the user gave earlier, in other words.
     - Expect: the agent goes to the next move without asking it.
     - Fails: the user has to say "I already told you".
103. A Spine item's statement is shown, and the user's paraphrase matches it.
     - Expect: frame 2 names the passage by its opening words; it is not quoted again.
     - Fails: the same lines shown in two consecutive turns.
104. Wrap-up with Offshoots kept.
     - Expect: the `ideate` suggestion comes after the file is written.
     - Fails: the suggestion appears with the Offshoot question.
105. The End review.
     - Expect: one After the block list below the note.
     - Fails: the same items listed twice.
