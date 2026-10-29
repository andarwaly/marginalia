# Source notes

Read at step 7. One fenced block per note, each labeled with its filename.

## Filenames and headings

- Filename: prefix, a space, then the title. Source notes use `§`. Drop `\ / * ? " < > |`,
  turn `:` into ` -`, avoid `# ^ [ ]`.
- The map's title is the source title. A point's title is its claim, a full sentence.
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
- Quote: one contiguous run, no ellipsis. Matching ignores markdown emphasis, link URLs,
  footnote markers like `[^1]`, whitespace and line breaks, and curly versus straight
  quotes; the words and their order must be identical. Never quote boilerplate (sign-in
  banners, "Press enter or click to view image").
- Locator: the nearest heading for an article; a linked `[mm:ss]` timestamp for a video.
- Key Concepts and Mentioned live on points only. Omit a section that is empty, except
  Implications, which is omitted too when the user said nothing.
- An item goes on the point whose quote it is about; a user-flagged item with no quote goes
  on the map.
- Implications: first-person bullets in the user's words, lightly tidied for spelling and
  filler, never reworded, never written by the agent. The user's guess at an answer to an
  Open Question becomes an Implication that names the question.

## After the blocks

A short plain-text list: the points written, the topics left untouched, and the result of the
quote check (each quote found verbatim in the clip, or flagged with the reason it was not).
