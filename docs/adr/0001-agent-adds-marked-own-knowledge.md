# The agent may add marked own knowledge during ingest

Status: accepted

`ingest` first made the source the only authority, so the agent could only check the user's restatement against the text. In the first Developing Taste test (2026-10-29) the user restated the article for 30 turns and said they learned nothing. The agent now offers one example or counter-case per thread, and explains when the user is stuck, in the first person and marked as its own knowledge ("From my own knowledge, not Kowalski's"). A scaffold never enters a source point.

Considered: keep source-only (rejected: it gave an echo loop); add untagged (rejected: the user cannot tell the agent's ideas from the author's).
