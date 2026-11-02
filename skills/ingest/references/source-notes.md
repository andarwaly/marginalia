# Source notes

Read before drafting the note. When the vault's AGENTS.md names a note template, the
template sets filenames, link and entry syntax, frontmatter, headings and section order,
and the layout example below gives way to it; every rule below about content still
applies. One source, one note, in one fenced block. Put the filename on a plain line
directly above the block, not in a block of its own.

## Language

Whatever names or quotes the source stays in the source's language: the filename, the
title, claim headings, claim lines, quotes, locators, Key Concepts and Mentioned. A source
titled "Developing Taste" gives `Developing Taste`, never a translation. What the user
said keeps the user's language: the main idea, Why I'm here and Implications. A claim line
is in the source's language and built from the user's words, so translate those words when
the languages differ. Section headings (`## Key Concepts`, `## Why I'm here`) stay in
English.

## Filename and headings

- Filename: the title, with no prefix. Drop `\ / * ? " < > |`, turn `:` into ` -`, avoid
  `# ^ [ ]`.
- The title is the source title from the clip's frontmatter. If the clip has none, ask the
  user; never take it from the URL.
- The `# heading` inside the note is the exact title.
- A claim heading is the claim in a short positive phrase, five to nine words, with no
  author name. Drop `: # ^ [ ] | \ /` from it so a heading link resolves. The author's name
  belongs in the claim line below.

## Source note

````
---
author: "[[Author Name]]"
published-at: 2026-01-31
source: https://example.com/article
---
# Title of the source

<main idea, the user's words, no heading>

- I think ... (Implications that fit no source point)

"a line the user kept" - [[Name]]

## Claim heading
<Author> says <claim line, built from the user's words>. [locator]

- I think ...

"a line the user kept" - [[Name]]

```code
<the author's code, word for word>
```

## Key Concepts
- Term: what it is, and why it is here

## Mentioned
- Name: what it is, and why it is here

## Open Questions
- ...

## Why I'm here
<the user's words>
````

- `published-at` is `YYYY-MM-DD`, empty when the clip lacks it, never guessed. A video uses
  its upload date.
- `author` is a bare wikilink; for a video, the channel name.
- The main idea comes first, with no heading. Below it sit the Implications and the
  Quotes that fit no source point. Omit what is empty.
- Why I'm here is the Intention in the user's words, word for word. Omit the section when
  the user gave none. The Prior belief is not written.
- Key Concepts, Mentioned and Open Questions sit once, at the foot, each term once. Omit a
  section that is empty.

## Source point

- The claim line names the author and is third person, about the source ("Kowalski
  says…"), and covers only what the highlight supports. When the user put the passage in
  other words, the claim line follows their words; when they pasted it, it follows what the
  highlight supports, and their take goes to Implications. First-person phrasing goes to
  Implications; a claim the highlight does not cover is its own source point or is left
  out.
- Highlight check, run for each claim at the draft: the highlight is one contiguous run
  within a single paragraph, no ellipsis, found in the clip. Narrow the claim line to what
  that paragraph supports; any other part is its own source point only if the user
  discussed it. Matching ignores markdown emphasis, link URLs, footnote markers like
  `[^1]`, whitespace and line breaks, and curly versus straight quotes; the words and their
  order must be identical. Never take boilerplate (sign-in banners, "Press enter or click
  to view image") as a highlight.
- Locator: on every source point, after the claim line. The nearest heading for an article,
  or the source title when no heading sits above the highlight; a linked `[mm:ss]`
  timestamp for a video. The highlight's text stays out of the note.
- Code: when the source shares code for that point, copy it word for word from the clip
  into a fenced block under the claim line, with the language tag. A table or flowchart is
  not copied; what the user said about it is an Implication. An image or demo gives its
  caption or alt text, flagged in the check as not source text.
- Quote: a line the user named, copied word for word from the clip and checked the same
  way as a highlight. Written `"text" - [[Name]]`, where Name is whoever said it: the
  author, or the person the author quotes. It goes under the source point it relates to,
  or below the main idea when it fits none. The agent writes none the user did not name.
- Key Concepts and Mentioned entries are plain text: `- Term: what it is, and why it is
  here`. "What it is" comes from the clip or the discussion only; when the source does not
  say, give the reason alone. The reason is the one agreed at Wrap-up step 4, so the user
  can tell on a later visit why the term is there. A link is written under Mentioned as
  `[Name](url)`.
- Key Concepts stay in the singular ("Tastemaker", never "Tastemakers"). Selection is in
  SKILL.md Wrap-up step 4, definitions in `terms.md`. A question of the user's that the
  source does not answer is an Open Question.
- Implications: first-person bullets in the user's words that stand on their own: a reader
  with neither the question nor the chat can tell what each is about. Keep the user's
  wording and opinion words, spelling fixed. Join consecutive replies on one thought into
  one bullet, in the user's order, by concatenation: add no word outside brackets and
  drop none. Add only the missing referent (what "it", "so" or "b" stands for) in square
  brackets, naming what the author made: "[Kowalski's dialog video] is his process of
  reviewing the interaction…". The bracket holds a name from the source or the chat, with
  no adjective or judgement. A reply with no thought of its own ("Yes.") folds into the
  bullet it answers; a bare pick of a candidate wording is dropped, and the wording enters
  only as the user's own restatement. The agent writes no opinion for the user. The user's
  guess at an answer to an Open Question becomes an Implication under the source point the
  question arose from, or below the main idea when none. The only agent text in a bullet is
  a bracketed referent.
- An Implication goes under the source point it is about. One that fits no point goes below
  the main idea.

## After the block

A short plain-text list: every thread as shown at SKILL.md step 4 (Show the threads),
marked as written, untouched, or started but not finished, and the result of the check
(each highlight, quote and code block found verbatim in the clip, or flagged with the
reason it was not).
