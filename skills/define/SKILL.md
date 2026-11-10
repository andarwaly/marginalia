---
name: define
description: "Writes a glossary entry for a term from the user's notes: one neutral definition in the user's vocabulary. Offers further headings only from those notes; the user writes them."
disable-model-invocation: true
---

# Define

Write the user's glossary entry for each term named, built only from their notes. There is
no interview: the agent synthesizes the definition, shows the entry, and asks one question.
The agent never fills a gap from general knowledge. The entry is a Draft the user refines.

## Terms

- **Draft**: what a mode writes: a starting point the user refines into their own note. The
  discussion aims at the user's sharpened thinking; the draft records it and does not
  replace the user's writing.
- **Reference note**: the glossary entry this skill writes, titled by the term: one neutral
  definition in the user's vocabulary. Any further heading is the user's own.
- **Admission sequence**: the ordered checks that decide whether a term earns an entry.
- **Support path**: one independent source. Notes with the same source URL, or the same
  author, count as one path.
- **Bounded lookup**: the entry covers one coherent subject, nothing else.

Fuller definitions and examples: `references/admission.md`.

## Steps

1. **Take the input.** The user names one or more terms. The notes are the point notes they
   paste with each note's frontmatter (`author`, `url`), a source note drafted in this
   session, or a note they name. With none of these, ask for them; search no vault.
   Alternate names the user gives become aliases.
2. **Gather.** For each term, take what each note says it is: first the user's own lines
   (Reactions, Stances, Implications), then the note's source text and Key Concepts lines.
   Group the notes by support path (same URL or same author is one path).
3. **Admit.** Read `references/admission.md` and run the checks in order for each term.
   Report all the terms together. The result is admitted, or unresolved with the failed
   check and the support still missing.
   - Unresolved: say which check failed and what is missing, and write nothing for that
     term. "Write it anyway" continues, and holds for later terms in this session.
4. **Synthesize.** Write one definition, one to three sentences, by the wording rules in
   `references/admission.md`. If notes conflict, ask the user which holds before writing.
5. **Show and ask.** Show each entry exactly as it will be written, in one fenced block
   labeled with its filename. Below the blocks, offer any further heading the notes could
   support, one line each: the heading's name and the note line it would draw from. Then
   ask one open question: "what's missing or wrong?" Revise once on the answer.
6. **Write.** Write a file only when the user asks, into a folder they name. A heading the
   user takes up from the offer is theirs to write; the file holds the definition.

## Hard rules

- Every sentence comes from the user's notes. A detail with no note behind it stays out.
- The definition says what the term is. The user's agreement or disagreement with the author
  stays in the source note.
- The entry holds no source-by-source dossier and no new recommendation.
- Link a term in the prose at its first mention when a Reference note for it exists or is in
  this batch: `[[Harness|harness]]`, keeping the sentence's wording. Never link the entry to
  itself. List the folder of Reference notes for this; their text is no source.
- A part of a larger term opens by saying so when the notes do: "Part of [[Harness|harness]],
  a reusable capability…".
- Filename: `<term>.md`, dropping `\ / * ? " < > |`, turning `:` into ` -`, avoiding
  `# ^ [ ]`. The `# heading` is the term. A name clash stops and asks.

## Format

```
---
sources:
  - "[[Source note title]]"
aliases:
  - alternate name
---
# Term

<definition, one to three sentences>
```

- A definition template in the vault, named by its AGENTS.md or found in its templates
  folder, sets the filename and frontmatter in place of this layout. The body stays the
  definition.
- `sources` lists the source notes of the deduplicated sources. `aliases` lists the alternate
  names the user gave; omit it if none.
