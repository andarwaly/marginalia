# Source notes

Read before drafting the notes. When the vault's AGENTS.md names a note template, the
template sets filenames, link and entry syntax, frontmatter, headings and section order,
and the layout examples below give way to it; every rule below about content still
applies. One fenced block per note. Put the filename on a plain line
directly above its block, not in a block of its own.

## Language

Whatever names or quotes the source stays in the source's language: filenames, titles,
`# headings`, claim lines, quotes, locators, Key Concepts and Mentioned. A source titled
"Developing Taste" gives `§ Developing Taste`, never a translation. What the user said
keeps the user's language: the Prior belief, Intention, main idea and Implications. A claim
line is in the source's language and built from the user's words, so translate those words
when the languages differ. Section headings (`## Implications`) stay in English.

## Filenames and headings

- Filename: prefix, a space, then the title. Source notes use `§`. Drop `\ / * ? " < > |`,
  turn `:` into ` -`, avoid `# ^ [ ]`.
- The map's title is the source title from the clip's frontmatter. If the clip has none,
  ask the user; never take it from the URL. A source point's title is its claim, a full
  sentence.
- The `# heading` inside each note is the exact title with no prefix. The prefix lives in
  filenames and link targets only; links hide it: `[[§ Title|Title]]`.

## Map note

```
---
author: "[[Author Name]]"
published-at: 2026-01-31
source: https://example.com/article
---
# Title of the source

## Prior belief
<the user's words>

## Intention
<the user's words>

## Main idea
<the user's words, no quote>

## Source Points
- [[§ Claim sentence one|Claim sentence one]]
- [[§ Claim sentence two|Claim sentence two]]

## Key Concepts
- ...

## Mentioned
- ...

## Open Questions
- ...

## Implications
- I think ...
```

- `published-at` is `YYYY-MM-DD`, empty when the clip lacks it, never guessed. A video uses
  its upload date.
- `author` is a bare wikilink; for a video, the channel name.
- Omit Prior belief and Intention when the user gave none.
- Key Concepts, Mentioned, Open Questions and Implications on the map hold whole-source
  items and items with no quote. Omit any section that is empty.

## Source point

```
---
source: "[[§ Title of the source]]"
---
# Claim sentence

<Author> says <claim line, built from the user's words>.

> "exact quote"
> locator

## Example
<what the example shows, in one line>

<the author's example, word for word>

## Key Concepts
- ...

## Mentioned
- ...

## Open Questions
- ...

## Implications
- I think ...
```

- Always standalone: readable without the map.
- The claim line names the author and is third person, about the source ("Kowalski says…"),
  and covers only what the quote supports. When the user put the passage in other words,
  the claim line follows their words; when they pasted it, it follows what the quote
  supports, and their take goes to Implications. First-person phrasing goes to
  Implications; a claim the quote does not cover is its own source point or is left out.
- Quote: one contiguous run within a single paragraph, no ellipsis. Narrow the claim line to
  what that paragraph supports; any other part is its own source point only if the user
  discussed it. Matching ignores markdown emphasis, link URLs, footnote markers like `[^1]`,
  whitespace and line breaks, and curly versus straight quotes; the words and their order
  must be identical. Never quote boilerplate (sign-in banners, "Press enter or click to view
  image").
- Locator: the nearest heading for an article, or the source title when no heading sits
  above the quote; a linked `[mm:ss]` timestamp for a video.
- Example: written only when the source holds an example, code block, table or flowchart
  for that point. It sits between the quote and Key Concepts, copied word for word from
  the clip (code, tables and text flowcharts in fenced blocks) under a one-line label of
  what it shows. An image or demo gives its caption or alt text, flagged in the quote check
  as not source text. Omit the section when the source has none.
- Key Concepts and Mentioned entries are plain text: `- Term: what it is, and why it is
  here`. "What it is" comes from the clip or the discussion only; when the source does not
  say, give the reason alone. The reason is the one
  agreed at Wrap-up step 4, so the user can tell on a later visit why the term is there.
- Key Concepts, Mentioned and Open Questions: definitions in `terms.md`, selection in
  SKILL.md Wrap-up step 4. A question of the user's that the source does not answer is an
  Open Question. Key Concepts stay in the singular ("Tastemaker", never "Tastemakers"). A
  link is written under Mentioned as `[Name](url)`. Omit a section that is empty,
  Implications included when the user said nothing.
- An item goes on the source point whose quote it is about; an item with no quote, from the
  user's list at Wrap-up step 4 or flagged by the user, goes on the map.
- Implications: first-person bullets in the user's words that stand on their own: a reader
  with neither the question nor the chat can tell what each is about. Keep the user's
  wording and opinion words, spelling fixed. Join consecutive replies on one thought into
  one bullet, in the user's order, by concatenation: add no word outside brackets and
  drop none. Add only the missing referent (what "it", "so" or "b" stands for) in square
  brackets, naming what the author made: "[Kowalski's dialog video] is his process of
  reviewing the interaction…". The bracket holds a name from the source or the chat, with
  no adjective or judgement. A reply with no thought of its own ("Yes.") folds into the
  bullet it answers; a bare pick of a candidate wording is dropped, and the wording enters
  only as the user's own restatement. The agent writes no opinion for the user. The user's guess at an answer to an Open Question becomes an Implication placed
  under that Open Question's source point. The only agent text in a bullet is a bracketed
  referent.

## After the blocks

A short plain-text list: every thread as shown at SKILL.md step 4 (Show the threads), marked as written, untouched, or
started but not finished, and the result of the quote check (each quote and each example
found verbatim in the clip, or flagged with the reason it was not).
