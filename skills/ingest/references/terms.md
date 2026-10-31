# Terms

Read when a rule in SKILL.md is unclear. The repo's `CONTEXT.md` is the source; this is the
copy that ships with the skill.

- **Source notes**: the map note plus the source points from one source.
- **Map note**: one per source. Holds the Prior belief, the Intention, the main idea and
  links to its source points.
- **Source point**: one standalone proposition the source makes, titled by the claim. It
  carries a claim line attributed to the author by name, in the user's words, and one
  verbatim quote.
- **Main idea**: what the source chiefly argues, in the user's words. The user states it
  first.
- **Implications**: the user's own thinking, kept verbatim under the source point it
  concerns or on the map: tangents, cross-domain links, doubts, examples from their life.
- **Key Concepts**: the domain vocabulary, concepts, methods and frameworks a source point,
  or the source as a whole, leans on, in the singular. A term counts when a Reference note
  could define it (what it is, how it forms, how it relates to other terms); the field of
  the source decides. A common noun of the field is a Key Concept: "Affordance" in a UX
  article, "Coal", "Seam" and "Sediment layer" in a mining article. So is a named concept,
  method or framework ("Occam's razor", "Agile"); its originator or the work that coined it
  is Mentioned. The general kind of a named place ("Delta", "Basin") is a Key Concept. They
  are the candidates for `define`.
- **Mentioned**: anything with a proper name that a source point, or the source as a whole,
  names: people, places, organizations, works, tools or events ("Balikpapan", "Stripe
  Sessions 2024"), with the footnote or link that points to it. A specific named place is
  Mentioned even when it is a field term. A brand used as a generic noun is Mentioned only
  when the source means the product.
- **Open Questions**: gaps the source leaves, flagged by the user only.
- **Intention**: what makes the user want to read or watch the source and what they want
  from it, in their words, often including what they will do with it. Set at the start,
  kept on the map, and recalled once per thread.
- **Prior belief**: what the user thinks about the topic before the discussion, in their
  words.
- **Thread**: a chain of related claims and passages in the source, possibly across
  headings. The discussion runs thread by thread, shown at the start with a progress marker
  and the examples it holds.
- **Passage**: one paragraph-sized unit of the source: a paragraph, example, code block,
  table, list, cited quote, image or demo. See `passages.md`.
- **Seen**: a passage is seen once the agent showed it verbatim after the user's take, or
  the user pasted it or put it in other words with the same meaning. A thread is done only
  when each of its passages is seen.
- **Reading state**: how the user's last answer landed. The states are in the table in
  `reading-the-answer.md`. It routes the next move and is never named to the user.
- **Meet and return**: the reply to the user's own thinking: your marked view in one or two
  sentences (agree or differ), then the author's passage that bears on it if unseen, then
  one question. It never labels the user's idea as outside the source. Not a scaffold.
- **Scaffold**: the agent's marked contribution: one example or counter-case offered
  before the user settles, or the stuck ladder. First person, marked as the agent's own
  knowledge, never part of a source point.
- **End review**: the one review at the end, where the user edits the drafted notes.
  See `end-review.md`.
- **Wrap-up**: the ending sequence in SKILL.md step 7.
