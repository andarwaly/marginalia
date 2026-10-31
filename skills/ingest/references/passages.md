# Passages

Read at step 2. The move for each answer is in `reading-the-answer.md`.

## The passage list

Walk the source from the first sentence to the last. A passage is one paragraph-sized
unit: a paragraph, an example, a code block, a table, a list, a cited quote, an image or a
demo. List them in source order, each assigned to a thread or skipped with a reason
(boilerplate, navigation, a repeat). A table, list or code block and the rules or
sentences that explain it are one passage; its rows and entries are parts, not passages.
Tag each one:

- **Ask**: every example, code block, table, image or demo, and the passage behind each
  claim. Each gets one question. Merge sibling examples (three code blocks of one kind)
  into one item.
- **Mention**: context paragraphs. They are shown together at the end of the thread, with
  no question.

A demo, image or video the clip dropped shows only as text ("below", "the animation
here", a caption). Name it by that text and ask the user to open it at the source and say
what they see.

## Seen

A passage is seen when the user has met its exact words (the agent showed them after the
user's take, or the user pasted them, or put them in other words with the same meaning)
and has answered a question about that passage, whether the question came before or after
the showing. Only a question about the passage counts; one about the user's own idea does
not. Compare the user's wording with the listed passage text; when unsure, treat it as
other words, show the exact text and ask. A passage the user misread is not seen. Check
each answer against the current thread's passages, then against the rest of the list.

The ask about a passage is one question: what do they make of it. For an example, code
block or table, ask what it shows; why the author chose it waits for the answer.

One question covers the whole passage. The user may take up a part (a row, a rule, a
sentence inside a claim paragraph) when it interests them.
