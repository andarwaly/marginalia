---
name: define
description: "Writes a glossary entry for a term from the user's pasted notes: a definition, then examples, where it is found and how to use it, as far as the notes support."
disable-model-invocation: true
---

# Define

Write the user's glossary entry for one term, built only from the notes they paste. There is
no interview: the agent synthesizes the definition, shows the entry, and asks one question.
The agent never fills a gap from general knowledge.

## Terms

- **Reference note**: the glossary entry this skill writes, titled by the term, with the `※`
  prefix in its filename.
- **Admission sequence**: the ordered checks that decide whether a term earns an entry.
- **Support path**: one independent source. Notes with the same source URL, or the same
  author, count as one path.
- **Bounded lookup**: the entry covers one coherent subject, nothing else.

Fuller definitions and examples: `references/admission.md`.

## Steps

1. **Take the input.** The user names a term and pastes the point notes that mention it, with
   each note's map frontmatter (`author`, `source`). Without pasted notes, ask for them; do
   not search a vault. Alternate names the user gives become aliases.
2. **Gather.** From each pasted note, take what it says the term is. Group the notes by
   support path (same URL or same author is one path).
3. **Admit.** Read `references/admission.md` and run the checks in order. The result is
   admitted, or unresolved with the failed check and the support still missing.
   - Unresolved: say which check failed and what is missing. Stop. If the user replies
     "write it anyway", continue, and open the note with a one-line caveat such as
     `> Single source: this definition rests on Kowalski alone.`
4. **Synthesize.** Write one definition from the notes' characterizations, in their wording
   where they agree. If they conflict, ask the user which holds before writing, never pick
   silently. Then add, in this order and only where the notes support it: examples, where
   the term is found, how to use it. If the notes lack one, say what is missing; do not
   invent it.
5. **Show and ask.** Show the entry in one fenced block labeled with its filename. Ask one
   open question: "what's missing or wrong?" Revise once on the answer.
6. **Write.** Write a file only when the user asks, into a folder they name.

## Hard rules

- Every sentence comes from the pasted notes. A detail with no note behind it stays out.
- The entry holds no source-by-source dossier, no personal judgment and no new
  recommendation. Those belong in source notes and thought notes.
- Disagreement among the notes is stated once, briefly, only if the lookup needs it.
- Filename: `※ <term>.md`, dropping `\ / * ? " < > |`, turning `:` into ` -`, avoiding
  `# ^ [ ]`. The `# heading` is the term with no prefix. A name clash stops and asks.

## Format

```
---
sources:
  - "[[§ Map note title]]"
aliases:
  - alternate name
---
# Term

<definition, one or two sentences>

## Examples
...

## Where it is found
...

## How to use it
...
```

- `sources` lists the map notes of the deduplicated sources. `aliases` lists the alternate
  names the user gave; omit it if none.
- Headings appear only for the parts the notes support. A one-line caveat, if any, comes
  right under the `# heading`.
