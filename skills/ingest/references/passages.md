# Passages

Read at step 2. The move for each answer is in `reading-the-answer.md`.

## The passage list

Walk the source from the first sentence to the last. A passage is one paragraph-sized
unit: a paragraph, an example, a code block, a table, a list, a cited quote, an image or a
demo. List them in source order, each assigned to a thread or skipped with a reason
(boilerplate, navigation, a repeat). A table, list or code block and the rules or
sentences that explain it are one passage; its rows and entries are parts, not passages.

## The Spine

Draft three to six items from the list: what the source would still say with everything
else removed. An item is a core idea, or a structure the author names (a formula, layers, a
framework, a list); a named structure is always an item. Weigh by what the rest of the
source depends on, and by what the author returns to. A claim that repeats an item merges
into it, and a passage that only restates one already listed is skipped as a repeat. A
source that holds more than six items keeps the six the others depend on, and the rest are
mention passages.

Tag each passage:

- **Ask**: the passage that states a Spine item, and at most one example or supporting
  passage for it, the one that shows the item best. Merge sibling examples (three code
  blocks of one kind) into one item.
- **Mention**: every other passage. They are shown together at the end of the thread, with
  no question.

The user may take up any listed passage at any time. It becomes an ask for that turn, and
the reply goes under the Spine item the passage supports.

A demo, image or video the clip dropped shows only as text ("below", "the animation
here", a caption). Name it by that text and ask the user to open it at the source, with
frame 3 naming what to look at ("What do you see in the Linear logo when you move the
mouse?").

## Seen

A passage is seen when the user has met its exact words (the agent showed them, before or
after the user's take, or the user pasted them, or put them in other words with the same
meaning) and has answered a question about that passage, whether the question came before
or after the showing. Only a question about the passage counts; one about the user's own idea does
not. Compare the user's wording with the listed passage text; when unsure, treat it as
other words, show the exact text and ask. A passage the user misread is not seen. Check
each answer against the current thread's passages, then against the rest of the list.

The ask about a passage is one question from `questions.md`, with the passage shown. A
claim passage gets frame 1, then frame 2, skipping a frame the user has already answered
(`questions.md`, Asked once). An example, code block or table gets frame 4
or 3 ("What is this table for?", "What do you see in the demo?"); why the author chose it
(frame 5) waits for the answer.

One question covers the whole passage. The user may take up a part (a row, a rule, a
sentence inside a claim paragraph) when it interests them.
