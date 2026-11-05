# Terms

Read when a rule in SKILL.md is unclear. The repo's `CONTEXT.md` is the source; this is the
copy that ships with the skill.

- **Draft**: what a mode writes: a starting point the user refines into their own note. The
  discussion aims at the user's sharpened thinking; the draft records it and does not
  replace the user's writing.
- **Source note**: one file per source. Opens with the loose Implications and Quotes that
  fit no point, holds a section per source point, and at the foot Key Concepts and
  Mentioned.
- **Source point**: one proposition the source makes: a `##` section of the source note,
  headed by the claim (short, positive, no author name). It carries a claim line attributed
  to the author by name, in the user's words, a Locator, the Examples and Quoted lines of
  its seen passages, and the user's Implications.
- **Implications**: the user's own thinking, in their words, one bullet per thought, under
  the source point it concerns, or below the title when it fits no point: tangents,
  cross-domain links, doubts, questions the source does not answer, examples from their
  life. Nothing is added to them.
- **Example**: a concrete case the author gives to show what a claim means: a prose case,
  code, a table or flowchart shown as code, an image or demo. Written under its source
  point when the user has seen it; verbatim from the clip, or the caption of an image or
  demo, flagged as not source text.
- **Quoted**: a person the author quotes in a passage the user has seen, written
  `Quoted: Person says "words"` under the source point. Verbatim from the clip. The agent
  places it. Not a Quote.
- **Key Concepts**: the domain vocabulary, concepts, methods and frameworks a source point,
  or the source as a whole, leans on, in the singular. A term counts when a Reference note
  could define it (what it is, how it forms, how it relates to other terms); the field of
  the source decides. A common noun of the field is a Key Concept: "Affordance" in a UX
  article, "Coal", "Seam" and "Sediment layer" in a mining article. So is a named concept,
  method or framework ("Occam's razor", "Agile"); its originator or the work that coined it
  is Mentioned. The general kind of a named place ("Delta", "Basin") is a Key Concept. They
  are the candidates for `define`. They are proposed per source point at Wrap-up and
  written once each at the foot of the source note.
- **Mentioned**: anything with a proper name that a source point, or the source as a whole,
  names: people, places, organizations, works, tools or events ("Balikpapan", "Stripe
  Sessions 2024"), with the footnote or link that points to it. A specific named place is
  Mentioned even when it is a field term. A brand used as a generic noun is Mentioned only
  when the source means the product. Written once each at the foot of the source note.
- **Quote**: a line the user picks to keep, written `"text" - [[Name]]`, where Name is
  whoever said it: the author, or someone the author quotes. Verbatim from the clip. It
  sits under the source point it relates to, or below the title when it fits none. The
  user names it; the agent never picks one. Not a highlight, not a Quoted line.
- **Highlight**: the exact passage behind a claim, found verbatim in the clip. The agent
  holds it as proof before it talks about the claim; the note keeps only its Locator,
  unless the highlight is itself the Example. Not a quote.
- **Locator**: the link from a source point to its highlight: a linked `[mm:ss]`
  timestamp for a video, the nearest heading for an article, the source title when no
  heading sits above it.
- **Intention**: what makes the user want to read or watch the source and what they want
  from it, in their words, often including what they will do with it. Set at the start to
  steer the discussion and recalled once per thread. Not written to the note.
- **Prior belief**: what the user thinks about the topic before the discussion, in their
  words. Asked at the start; not written to the note.
- **Thread**: a chain of related claims and passages in the source, possibly across
  headings. The discussion runs thread by thread, shown at the start with a progress marker
  and the examples it holds.
- **Passage**: one paragraph-sized unit of the source: a paragraph, example, code block,
  table, list, cited quote, image or demo. See `passages.md`.
- **Seen**: a passage is seen once the agent showed it verbatim after the user's take, or
  the user pasted it or put it in other words with the same meaning, and the user has
  answered a question about it. The parts of a passage (table rows, list entries) belong
  to it. A thread is done only when each of its ask passages is seen.
- **Passage tag**: each passage is tagged ask (every example, code block, table, image or
  demo, and the passage behind each claim: it gets one question) or mention (a context
  paragraph: shown with the rest at the end of the thread, with no question).
- **Reading state**: which row of the routing table in `reading-the-answer.md` the user's
  last answer matches. It routes the next move and is never named to the user.
- **Rider**: the one extra item a reply may carry besides its question: the author's exact
  words, or a remark that the user's claim goes beyond its highlight. The three beats of meet
  and return count as one reply.
- **Meet and return**: the reply to the user's own thinking: your view in one or two
  sentences (agree or differ; marked "From my own knowledge, not <Author>'s:" only when it
  differs from the author's), then the author's passage that bears on it if unseen, then
  one question about that passage. It never labels the user's idea as outside the source
  and does not work the idea out. Not a scaffold.
- **Scaffold**: the agent's marked contribution: one example or counter-case offered
  on a complete tentative claim, or the stuck ladder. First person, marked as the agent's own
  knowledge, never part of a source point.
- **End review**: the one review at the end, where the user edits the drafted source note, keeps or cuts the Examples and Quoted lines the agent placed, and may name lines to keep as Quotes.
  See `end-review.md`.
- **Wrap-up**: the ending sequence in SKILL.md step 7: the coverage list, `ideate`
  suggestions, Key Concepts and Mentioned proposal, End review, folder, files.
