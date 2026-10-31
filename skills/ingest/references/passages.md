# Passages

Read at step 2. The move for each answer is in `reading-the-answer.md`.

## The passage list

Walk the source from the first sentence to the last. A passage is one paragraph-sized
unit: a paragraph, an example, a code block, a table, a list, a cited quote, an image or a
demo. List them in source order, each assigned to a thread or skipped with a reason
(boilerplate, navigation, a repeat). Tag each one:

- **Ask**: every example, code block, table, image or demo, and the passage behind each
  claim. Each gets one question. Merge sibling examples (three code blocks of one kind)
  into one item.
- **Mention**: context paragraphs. They are shown together at the end of the thread, with
  no question.

A demo, image or video the clip dropped shows only as text ("below", "the animation
here", a caption). Name it by that text and ask the user to open it at the source and say
what they see.

## Seen

A passage is seen when the agent has shown it word for word after the user's take, or the
user has pasted it, or the user has put it in other words with the same meaning. Compare
the user's wording with the listed passage text; when unsure, treat it as other words,
show the exact text and ask. A passage the user misread is not seen. Check each answer
against the current thread's passages, then against the rest of the list.

The ask about a passage is one question: what do they make of it. For an example, code
block or table, ask what it shows and why the author chose it.
