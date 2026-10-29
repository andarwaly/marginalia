# Source notes

Read before drafting the notes. One fenced block per note. Put the filename on a plain line
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
```

- `published-at` is `YYYY-MM-DD`, empty when the clip lacks it, never guessed. A video uses
  its upload date.
- `author` is a bare wikilink; for a video, the channel name.
- Omit Prior belief and Intention when the user gave none.
- Whole-source Open Questions and Implications may sit on the map, under their own headings.

## Source point

```
---
source: "[[§ Title of the source]]"
---
# Claim sentence

<Author> says <claim line, built from the user's words>.

> "exact quote"
> locator

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
  and covers only what the quote supports. First-person phrasing goes to Implications; a
  claim the quote does not cover is its own source point or is left out.
- Quote: one contiguous run within a single paragraph, no ellipsis. Narrow the claim line to
  what that paragraph supports; any other part is its own source point only if the user
  discussed it. Matching ignores markdown emphasis, link URLs, footnote markers like `[^1]`,
  whitespace and line breaks, and curly versus straight quotes; the words and their order
  must be identical. Never quote boilerplate (sign-in banners, "Press enter or click to view
  image").
- Locator: the nearest heading for an article, or the source title when no heading sits
  above the quote; a linked `[mm:ss]` timestamp for a video.
- Key Concepts: abstract concepts, methods or frameworks the point leans on. Mentioned:
  concrete named people, places, organizations, works, tools or events. Open Questions:
  gaps the source leaves, flagged by the user only. Key Concepts and Mentioned live on
  source points only. Omit a section that is empty, Implications included when the user said
  nothing.
- An item goes on the source point whose quote it is about; a user-flagged item with no
  quote goes on the map.
- Implications: first-person bullets in the user's words, word for word with spelling fixed,
  never reworded, never written by the agent. The user's guess at an answer to an Open
  Question becomes an Implication that names the question.

## After the blocks

A short plain-text list: every thread as shown at step 4, marked as written, untouched, or
started but not finished, and the result of the quote check (each quote found verbatim in
the clip, or flagged with the reason it was not).
