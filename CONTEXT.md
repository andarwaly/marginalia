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

**Source notes**:
The map note plus the source points from one source.
_Avoid_: literature note

**Map note**:
One per source. Holds the Prior belief, the Intention, the main idea and links to its source points.

**Source point**:
One standalone proposition the source makes, titled by the claim. It carries a claim line attributed to the author by name, in the user's words, and one verbatim quote.
_Avoid_: point note, claim note

**Main idea**:
What the source chiefly argues, in the user's words. The user states it first.
_Avoid_: core idea

**Implications**:
The user's own thinking, kept verbatim under the source point it concerns or on the map: tangents, cross-domain links, doubts, examples from their life.
_Avoid_: reaction, take

**Key Concepts**:
The domain vocabulary, concepts, methods and frameworks a source point, or the source as a whole, leans on, in the singular. A term counts when a Reference note could define it (what it is, how it forms, how it relates to other terms); the field of the source decides. A common noun of the field is a Key Concept: "Affordance" in a UX article, "Coal", "Seam" and "Sediment layer" in a mining article. So is a named concept, method or framework ("Occam's razor", "Agile"); its originator or the work that coined it is Mentioned. The general kind of a named place ("Delta", "Basin") is a Key Concept. Key Concepts are the candidates for `define`.

**Mentioned**:
Anything with a proper name that a source point, or the source as a whole, names: people, places, organizations, works, tools or events ("Balikpapan", "Stripe Sessions 2024"), with the footnote or link that points to it. A specific named place is Mentioned even when it is a field term. A brand used as a generic noun is Mentioned only when the source means the product.

**Open Questions**:
Gaps the source leaves, flagged by the user only.

**Thought note**:
An atomic idea of the user's own, titled by a claim and optionally backed by source notes. Written by `ideate`.

**Reference note**:
The user's glossary entry for a term, built from their notes. Written by `define`.

### Discussion

**Intention**:
What makes the user want to read or watch the source and what they want from it, in their words, often including what they will do with it. Set at the start, kept on the map, and recalled once per thread.
_Avoid_: purpose, goal

**Prior belief**:
What the user thinks about the topic before the discussion, in their words.

**Thread**:
A chain of related claims in the source, possibly across headings. The discussion runs thread by thread, shown at the start with a progress marker.
_Avoid_: topic, heading

**Reading state**:
How the user's last answer landed: confident, hesitant, blank or confused. It routes the agent's next move and is never named to the user.

**Scaffold**:
The agent's marked contribution: one example or counter-case offered before the user settles, or the stuck ladder (point to the passage, quote the author, explain plainly with an example). First person, marked as the agent's own knowledge, and never part of a source point.
_Avoid_: hint, tip

**End review**:
The one review at the end of `ingest`. The agent shows the drafted claim lines for the user to edit; Implications are copied verbatim and the main idea is the user's.

**Wrap-up**:
`ingest`'s ending sequence: `ideate` suggestions, main idea, End review, folder, files written.

**Statement gate**:
The `ideate` rule that a claim is fixed only on the user's open confirmation. Not used in `ingest`.

**Done gate**:
The `ideate` ending: the "so what" question, the sign-off pass, then the note. Not used in `ingest`.

### Skills

**Mode**:
A user-invoked skill that runs a whole session: `ingest`, `ideate` or `define`.

**Technique**:
A skill a mode calls by name for one move of the interview.
