# marginalia

Skills that sharpen the user's thinking about a source or an idea, and draft notes from the
discussion for the user to refine, while the user's wording stays the user's.

## Language

### Notes

**Source**:
One article, video or post the user discusses.
_Avoid_: resource

**Clip**:
The markdown text of a source fetched from a URL. It lives in the temp folder for the session, never in the vault.

**Draft**:
What a mode writes: a starting point the user refines into their own note. The discussion aims at the user's sharpened thinking; the draft records it and does not replace the user's writing. The same in `ingest`, `ideate` and `define`; only the content differs.
_Avoid_: final note, output

**Source note**:
One file per source. Opens with the loose Implications and Quotes that fit no point, holds a section per source point, then Beyond the source, then Key Concepts and Mentioned at the foot.
_Avoid_: literature note, map note

**Source point**:
One Spine item as the source states it: a `##` section of the source note, headed by the claim (short, positive, no author name). It carries the author's stand as a block quote of the Highlight, a Locator, each seen Example under a short label with the user's Reactions beneath it, the Quoted lines of its seen passages, the user's Stance, and Implications. A claim line appears only when the user asks for one at the End review. One Spine item, one source point: a passage that repeats an item merges into it.
_Avoid_: point note, claim note

**Reaction**:
The user's response to one passage, in their words, written directly under the Example, Quoted line or block quote the question was about. A reply on several passages goes under the passage the question named; a reply on a passage with no place of its own goes under its Spine item's block quote. Nothing is added to it.

**Stance**:
The user's one-sentence position on a source point, with the reason, written so it reads without the chat. When the discussion already holds their agreement or disagreement with a reason, that reply becomes the Stance and nothing is asked. Otherwise it is asked once, when the thread closes, with one re-ask when the reply leans on the question. Spelling fixed. The user may decline, and that point has no Stance.

**Offshoot**:
A thought of the user's that brings in a context the source never mentions: another culture, product, field or their own experience. Held silently during the discussion. At Wrap-up the user writes one standalone sentence, keeps their original words, or drops it. Written under `## Beyond the source` with a plain-text `From:` pointer to its source point. `ideate` starts from Offshoots.

**Implications**:
The user's own doubts and questions the source does not answer, in their words, one bullet per thought, under the source point they arose from, or below the title when they fit no point. Nothing is added to them.
_Avoid_: take

**Example**:
A concrete case the author gives to show what a claim means: a prose case, code, a table or flowchart shown as code, an image or demo. Written under its source point, with a short label, when the user has seen it; verbatim from the clip, or the caption of an image or demo, flagged as not source text.
_Avoid_: illustration

**Quoted**:
A person the author quotes in a passage the user has seen, written `Quoted: Person says "words"` under the source point. Verbatim from the clip. The agent places it. Not a Quote.

**Key Concepts**:
The domain vocabulary, concepts, methods and frameworks a source point, or the source as a whole, leans on, in the singular. A term counts when a Reference note could define it (what it is, how it forms, how it relates to other terms); the field of the source decides. A common noun of the field is a Key Concept: "Affordance" in a UX article, "Coal", "Seam" and "Sediment layer" in a mining article. So is a named concept, method or framework ("Occam's razor", "Agile"); its originator or the work that coined it is Mentioned. The general kind of a named place ("Delta", "Basin") is a Key Concept. Key Concepts are the candidates for `define`. They are proposed per source point at Wrap-up and written once each at the foot of the source note.

**Mentioned**:
Anything with a proper name that a source point, or the source as a whole, names: people, places, organizations, works, tools or events ("Balikpapan", "Stripe Sessions 2024"), with the footnote or link that points to it. A specific named place is Mentioned even when it is a field term. A brand used as a generic noun is Mentioned only when the source means the product. Written once each at the foot of the source note.

**Quote**:
A line the user picks to keep, written `"text" - [[Name]]`, where Name is whoever said it: the author, or someone the author quotes. Verbatim from the clip. It sits under the source point it relates to, or below the title when it fits none. The user names it; the agent never picks one. Not a Quoted line.
_Avoid_: highlight

**Highlight**:
The exact passage behind a claim, found verbatim in the clip. The agent holds it as proof, and the note writes it as a block quote: the author's stand for the source point. A line the user also names as a Quote is written once, as the Quote.
_Avoid_: quote

**Locator**:
The link from a source point to its highlight: a linked `[mm:ss]` timestamp for a video, the nearest heading for an article, the source title when no heading sits above it.

**Thought note**:
An atomic idea of the user's own, titled by a claim and optionally backed by source notes. Written by `ideate`.

**Reference note**:
The user's glossary entry for a term: one neutral definition in the user's vocabulary, built from their notes. Written by `define`. Any further heading is the user's own.

**Reading map**:
The one message `sift` produces: the source's claims with their Locators, led by the Intention, what else the source holds, and what to skip. Shown in chat; the user writes the note.

### Discussion

**Intention**:
What makes the user want to read or watch the source and what they want from it, in their words, often including what they will do with it. Set at the start to steer the discussion and recalled once per session. Not written to the note.
_Avoid_: purpose, goal

**Prior belief**:
What the user thinks about the topic before the discussion, in their words. Asked at the start; not written to the note.

**Spine**:
The few things a source is about: three to six items, each a core idea or a structure the author names (a formula, layers, a framework, a list). The user names what they think it holds first; the agent adds what they missed, and the user confirms. Without having read the source, the user edits the agent's list. A claim that repeats an item merges into it.
_Avoid_: main idea, summary

**Thread**:
The discussion of one Spine item and the passages behind it, possibly across headings. The discussion runs thread by thread, shown with a progress marker and the examples each holds.
_Avoid_: topic, heading

**Passage**:
One paragraph-sized unit of the source: a paragraph, example, code block, table, list, cited quote, image or demo. The agent lists every passage, first to last, before it groups them into threads.
_Avoid_: section, chunk

**Seen**:
A passage is seen once the user has met its exact words (the agent showed them, before or after the user's take, or the user pasted them or put them in other words with the same meaning) and has answered a question about it. The parts of a passage (table rows, list entries) belong to it. A thread is done only when each of its ask passages is seen.

**Passage tag**:
Each passage is tagged ask (the passage that states a Spine item, and at most one example or supporting passage for it: it gets a question) or mention (every other passage: shown with the rest at the end of the thread, with no question). A passage that repeats one already listed is skipped as a repeat.

**Reading state**:
Which row of the routing table in `reading-the-answer.md` the user's last answer matches. It routes the agent's next move and is never named to the user.

**Rider**:
The one extra item a reply may carry besides its question: the author's exact words, or a remark that the user's claim goes beyond its highlight. The three beats of meet and return count as one reply.

**Frame**:
One of the plain question forms every `ingest` question to the user takes (`references/questions.md`). Each states what it asks and what kind of answer it wants, names its object, and avoids idiom, because the user may read English as a second language.

**Meet and return**:
The `ingest` reply to the user's own thinking: the agent's view in one or two sentences (agree or differ; marked "From my own knowledge, not <Author>'s:" only when it differs from the author's), then the author's passage that bears on it if unseen, then one question about that passage. It never labels the user's idea as outside the source and does not work the idea out. Not a scaffold.

**Scaffold**:
The agent's marked contribution: one example or counter-case offered on a complete tentative claim, or the stuck ladder (point to the passage, quote the author, explain plainly with an example). First person, marked as the agent's own knowledge, and never part of a source point.
_Avoid_: hint, tip

**End review**:
The one review at the end of `ingest`. The agent shows the drafted source note for the user to edit, keep or cut the Examples and Quoted lines the agent placed, and name lines to keep as Quotes; Reactions, Stances, Offshoots and Implications keep the user's words unchanged.

**Wrap-up**:
`ingest`'s ending sequence: the coverage list, Offshoots, Key Concepts and Mentioned proposal, End review, folder, files written, `ideate` suggestions.

**Statement gate**:
The `ideate` rule that a claim is fixed only on the user's open confirmation. Not used in `ingest`.

**Done gate**:
The `ideate` ending: the "so what" question, the sign-off pass, then the note. Not used in `ingest`.

### Skills

**Mode**:
A user-invoked skill that runs a whole session: `ingest`, `ideate`, `define` or `sift`.

**Technique**:
A skill a mode calls by name for one move of the interview.
