# Source notes

Read at step 7. One fenced block per note. Put the filename on a plain line directly above
its block, not in a block of its own.

## Language

Whatever names or quotes the source stays in the source's language: filenames, titles,
`# headings`, point claims, quotes, locators, Key Concepts and Mentioned. A source titled
"Developing Taste" gives `§ Developing Taste`, never a translation. What the user said
keeps the user's language: the main idea, the restatement, Intention, Implications.

## Filenames and headings

- Filename: prefix, a space, then the title. Source notes use `§`. Drop `\ / * ? " < > |`,
  turn `:` into ` -`, avoid `# ^ [ ]`.
- The map's title is the source title from the clip's frontmatter. If the clip has none,
  ask the user; never take it from the URL. A point's title is its claim, a full sentence.
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

<main idea, the user's confirmed words, no quote>

## Source Points
- [[§ Claim sentence one|Claim sentence one]]
- [[§ Claim sentence two|Claim sentence two]]
```

- `published-at` is `YYYY-MM-DD`, empty when the clip lacks it, never guessed. A video uses
  its upload date.
- `author` is a bare wikilink; for a video, the channel name.
- The intention sits on the map under `## Intention`, kept like Implications (below) and
  apart from them. It is not put through the statement gate. Omit it when the user gave
  none.
- Whole-source Open Questions and Implications may sit on the map, under their own headings.

## Point note

```
---
source: "[[§ Title of the source]]"
---
# Claim sentence

<short restatement, source-owned: what the source says, in the user's confirmed words>

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
- The restatement is third person, about the source ("the author says…"), and covers only
  what the quote supports. First-person phrasing goes to Implications; a claim the quote
  does not cover is its own point or is left out.
- Quote: one contiguous run within a single paragraph, no ellipsis. Narrow the restatement
  to what that paragraph supports; any other part is its own point only if the user
  picked and confirmed it. Matching ignores markdown emphasis, link URLs, footnote markers
  like `[^1]`, whitespace and line breaks, and curly versus straight quotes; the words and
  their order must be identical. Never quote boilerplate (sign-in banners, "Press enter or
  click to view image").
- Locator: the nearest heading for an article, or the source title when no heading sits
  above the quote; a linked `[mm:ss]` timestamp for a video.
- Key Concepts: abstract concepts, methods or frameworks the point leans on. Mentioned:
  concrete named people, places, organizations, works, tools or events. Open Questions:
  gaps the source leaves, flagged by the user only. Key Concepts and Mentioned live on
  points only. Omit a section that is empty, Implications included when the user said
  nothing.
- An item goes on the point whose quote it is about; a user-flagged item with no quote goes
  on the map.
- Implications: first-person bullets in the user's words, lightly tidied for spelling and
  filler, never reworded, never written by the agent. The user's guess at an answer to an
  Open Question becomes an Implication that names the question.

## After the blocks

A short plain-text list: every topic from the opening labels, copied character for
character from the step 3 message, as written, untouched, or started but not confirmed, and the result of the quote check (each quote found verbatim
in the clip, or flagged with the reason it was not).
