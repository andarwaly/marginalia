# marginalia

Skills that turn a source into notes, and the user's own ideas into thought notes, while
the user's wording stays the user's.

## Language

### Notes

**Source**:
One article, video or post the user discusses.
_Avoid_: resource

**Clip**:
The markdown text of a source fetched from a URL. It lives in the temp folder for the session, never in the vault.

**Source note**:
One file per source. Opens with Why I'm here and the main idea, each under its heading, then holds loose Quotes and Implications, a section per source point, and at the foot Key Concepts, Mentioned and Open Questions.
_Avoid_: literature note, map note

**Source point**:
One proposition the source makes: a `##` section of the source note, headed by the claim (short, positive, no author name). It carries a claim line attributed to the author by name, in the user's words, a Locator, the user's Implications, and a fenced code block when the source shares code.
_Avoid_: point note, claim note

**Main idea**:
What the source chiefly argues, in the user's words. The user states it first. It sits under its own heading, after Why I'm here.
_Avoid_: core idea

**Implications**:
The user's own thinking, in their words and standing on its own (only a bracketed referent is added), under the source point it concerns, or below the main idea when it fits no point: tangents, cross-domain links, doubts, examples from their life.
_Avoid_: reaction, take

**Key Concepts**:
The domain vocabulary, concepts, methods and frameworks a source point, or the source as a whole, leans on, in the singular. A term counts when a Reference note could define it (what it is, how it forms, how it relates to other terms); the field of the source decides. A common noun of the field is a Key Concept: "Affordance" in a UX article, "Coal", "Seam" and "Sediment layer" in a mining article. So is a named concept, method or framework ("Occam's razor", "Agile"); its originator or the work that coined it is Mentioned. The general kind of a named place ("Delta", "Basin") is a Key Concept. Key Concepts are the candidates for `define`. They are proposed per source point at Wrap-up and written once each at the foot of the source note.

**Mentioned**:
Anything with a proper name that a source point, or the source as a whole, names: people, places, organizations, works, tools or events ("Balikpapan", "Stripe Sessions 2024"), with the footnote or link that points to it. A specific named place is Mentioned even when it is a field term. A brand used as a generic noun is Mentioned only when the source means the product. Written once each at the foot of the source note.

**Open Questions**:
Gaps the source leaves, flagged by the user only.

**Quote**:
A line the user picks to keep, written `"text" - [[Name]]`, where Name is whoever said it: the author, or someone the author quotes. Verbatim from the clip. It sits under the source point it relates to, or below the main idea when it fits none. The user names it; the agent never picks one.
_Avoid_: highlight

**Highlight**:
The exact passage behind a claim, found verbatim in the clip. The agent holds it as proof before it talks about the claim; the note keeps only its Locator.
_Avoid_: quote

**Locator**:
The link from a source point to its highlight: a linked `[mm:ss]` timestamp for a video, the nearest heading for an article, the source title when no heading sits above it.

**Thought note**:
An atomic idea of the user's own, titled by a claim and optionally backed by source notes. Written by `ideate`.

**Reference note**:
The user's glossary entry for a term, built from their notes. Written by `define`.

### Discussion

**Intention**:
What makes the user want to read or watch the source and what they want from it, in their words, often including what they will do with it. Set at the start, written as the Why I'm here section at the top of the source note, and recalled once per thread.
_Avoid_: purpose, goal

**Prior belief**:
What the user thinks about the topic before the discussion, in their words. Asked at the start; not written to the note.

**Thread**:
A chain of related claims and passages in the source, possibly across headings. The discussion runs thread by thread, shown at the start with a progress marker and the examples it holds.
_Avoid_: topic, heading

**Passage**:
One paragraph-sized unit of the source: a paragraph, example, code block, table, list, cited quote, image or demo. The agent lists every passage, first to last, before it groups them into threads.
_Avoid_: section, chunk

**Seen**:
A passage is seen once the agent showed it verbatim after the user's take, or the user pasted it or put it in other words with the same meaning, and the user has answered a question about it. The parts of a passage (table rows, list entries) belong to it. A thread is done only when each of its ask passages is seen.

**Passage tag**:
Each passage is tagged ask (every example, code block, table, image or demo, and the passage behind each claim: it gets one question) or mention (a context paragraph: shown with the rest at the end of the thread, with no question).

**Reading state**:
Which row of the routing table in `reading-the-answer.md` the user's last answer matches. It routes the agent's next move and is never named to the user.

**Rider**:
The one extra item a reply may carry besides its question: the author's exact words, or a remark that the user's claim goes beyond its highlight. The three beats of meet and return count as one reply.

**Meet and return**:
The `ingest` reply to the user's own thinking: the agent's view in one or two sentences (agree or differ; marked "From my own knowledge, not <Author>'s:" only when it differs from the author's), then the author's passage that bears on it if unseen, then one question about that passage. It never labels the user's idea as outside the source and does not work the idea out. Not a scaffold.

**Scaffold**:
The agent's marked contribution: one example or counter-case offered on a complete tentative claim, or the stuck ladder (point to the passage, quote the author, explain plainly with an example). First person, marked as the agent's own knowledge, and never part of a source point.
_Avoid_: hint, tip

**End review**:
The one review at the end of `ingest`. The agent shows the drafted source note for the user to edit, and the user may name lines to keep as Quotes; Implications keep the user's words, with bracketed referents the user can check, and the main idea is the user's.

**Wrap-up**:
`ingest`'s ending sequence: the coverage list, `ideate` suggestions, main idea, Key Concepts and Mentioned proposal, End review, folder, files written.

**Statement gate**:
The `ideate` rule that a claim is fixed only on the user's open confirmation. Not used in `ingest`.

**Done gate**:
The `ideate` ending: the "so what" question, the sign-off pass, then the note. Not used in `ingest`.

### Skills

**Mode**:
A user-invoked skill that runs a whole session: `ingest`, `ideate` or `define`.

**Technique**:
A skill a mode calls by name for one move of the interview.
