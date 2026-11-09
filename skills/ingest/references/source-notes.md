# Source notes

Read before drafting the note. The note is a draft the user refines into their own notes:
it records the source's points, the user's words, the author's examples and quoted people,
and the terms and names the discussion used. When the vault's AGENTS.md names a note
template, the template sets filenames, link and entry syntax, frontmatter, headings and
section order, and the layout example below gives way to it; every rule below about content
still applies. One source, one note, in one fenced block. Put the filename on a plain line
directly above the block, not in a block of its own.

## Language

Whatever names or quotes the source stays in the source's language: the filename, the
title, claim headings, block quotes, examples and their labels, Quoted lines, quotes,
locators, Key Concepts and Mentioned. A source titled "Developing Taste" gives
`Developing Taste`, never a translation. What the user said keeps the user's language:
Reactions, Stances, Offshoots and Implications. A claim line, written only on request, is
in the source's language and built from the user's words, so translate those words when the
languages differ. Section headings (`## Beyond the source`, `## Key Concepts`,
`## Mentioned`) stay in English.

## Filename and headings

- Filename: the title, with no prefix. Drop `\ / * ? " < > |`, turn `:` into ` -`, avoid
  `# ^ [ ]`.
- The title is the source title from the clip's frontmatter. If the clip has none, ask the
  user; never take it from the URL.
- The `# heading` inside the note is the exact title.
- A claim heading is the claim in a short positive phrase, five to nine words, with no
  author name. Drop `: # ^ [ ] | \ /` from it so a heading link resolves. The author's name
  belongs in the attribution of the block quote below.
- An example label is the short name the thread display gave it, two to five words
  ("Decision tree", "Scenario + Solution"), written as a `####` heading under its source
  point.

## Source note

````
---
author: "[[Author Name]]"
published: 2026-01-31
url: https://example.com/article
---
# Title of the source

- Is ... ? (a doubt or question of the user's that fits no source point)

"a line the user kept" - [[Name]]

## Claim heading
> <the highlight, word for word from the clip> - [[Name]]
[locator]

#### Short example label
Example: <the author's case, word for word from the clip>
<the user's Reaction, in their words>

#### Short code example label
```code
<the author's code, word for word>
```
<the user's Reaction, in their words>

Quoted: <Person> says "<their words, word for word from the clip>"
<the user's Reaction, in their words>

Stance: <the user's one sentence>

- Is ... ? (a question of the user's the source does not answer)

"a line the user kept" - [[Name]]

## Beyond the source
- <the user's Offshoot, one standalone sentence>. From: <claim heading>

## Key Concepts
- Term: what it is, and why it is here

## Mentioned
- Name: what it is, and why it is here
````

- `published` is `YYYY-MM-DD`, empty when the clip lacks it, never guessed. A video uses
  its upload date.
- `author` is a bare wikilink; for a video, the channel name. It, the attribution names of
  block quotes and the Quote names are the only wikilinks the agent writes.
- Below the title sit the Implications and Quotes that fit no source point. Omit what is
  empty.
- `## Beyond the source` sits after the last source point and holds one bullet per
  Offshoot. Omit it when none was held or asked for.
- The Intention and the Prior belief are asked and not written.
- Key Concepts and Mentioned sit once, at the foot, each term once. Omit a section that is
  empty. The user writes any section of their own, such as `## What I think`, after the
  note; the agent writes none.

## Source point

- The author's stand is the highlight, written as a block quote directly under the claim
  heading: `> <words> - [[Name]]`, where Name is whoever said it (the author, or the person
  the author quotes). It covers one claim. A claim the highlight does not cover is its own
  source point or is left out. One claim, one source point: when two threads touch the
  same claim, the draft merges them under one heading and writes the highlight once. A
  claim line, `<Author> says …` in the third person built from the user's words, is
  written only when the user asks for one at the End review.
- Highlight check, run for each claim at the draft: the highlight is one contiguous run
  within a single paragraph, no ellipsis, found in the clip. Narrow the block quote to
  that paragraph; any other part is its own source point only if the user discussed it.
  Matching ignores markdown emphasis, link URLs, footnote markers like `[^1]`, whitespace
  and line breaks, and curly versus straight quotes; the words and their order must be
  identical. Never take boilerplate (sign-in banners, "Press enter or click to view image")
  as a highlight. A line the user also names as a Quote is written once, as the Quote, in
  place of the block quote.
- Locator: on every source point, on the line after the block quote. The nearest heading
  for an article, or the source title when no heading sits above the highlight; a linked
  `[mm:ss]` timestamp for a video.
- Example: a concrete case the author gives to show what the claim means. Written for each
  example the user has seen, under its own `####` label inside the source point it
  illustrates; an example the user never engaged with is left out. A prose case is the
  run of the clip that carries it, word for word, and passes the highlight check, written
  after `Example:`. Code is copied word for word into a fenced block with the language
  tag. A table or flowchart the source shows as a code block is a code block and is
  copied; one shown any other way is not copied, and what the user said about it is a
  Reaction. An image or demo gives its caption or alt text after `Example:`, flagged in the
  check as not source text. The user trims a long example at the End review.
- Reaction: the user's words, directly under the Example, Quoted line or block quote the
  question was about, as plain lines with no bullet and no label (the `Example:` and
  `Quoted:` prefixes and the code fence mark the source's text; an unmarked line is the
  user's). Keep the user's wording and opinion words, spelling fixed. Join consecutive
  replies on one thought into one line, in the user's order, by concatenation: add no word
  and drop none. A reply with no thought of its own ("Yes.") folds into the line it answers;
  a bare pick of a candidate wording is dropped, and the wording enters only as the user's
  own restatement. A reply that spans several passages goes under the passage the question
  named. The answer to a thread's topic question goes under the thread's first source
  point, below its block quote. The agent writes no opinion for the user and adds no tag or
  link.
- Stance: one line, `Stance: <the user's sentence>`, after the point's Examples and Quoted
  lines. It is the reply to the Stance check (SKILL.md step 6), in the user's words with
  spelling fixed; a re-ask that names the subject replaces the first reply. A declined
  point has no Stance line.
- Offshoot: a bullet under `## Beyond the source`, the user's one sentence from Wrap-up step
  2 in their words with spelling fixed, then `From: <claim heading>` as plain text, naming
  the source point the Offshoot arose from. The user may drop any at Wrap-up; a dropped
  Offshoot is not written.
- Quoted: a person the author quotes in a passage the user has seen. Written
  `Quoted: <Person> says "<words>"`, with the words word for word from the clip and
  checked the same way as a highlight, under the source point the passage supports. A line
  the user also names as a Quote is written once, as the Quote.
- Quote: a line the user named, copied word for word from the clip and checked the same
  way as a highlight. Written `"text" - [[Name]]`, where Name is whoever said it: the
  author, or the person the author quotes. It goes under the source point it relates to,
  or below the title when it fits none. The agent writes none the user did not name. The
  block quotes, Examples and Quoted lines are the only source text the agent places on its
  own.
- Key Concepts and Mentioned entries are plain text: `- Term: what it is, and why it is
  here`. "What it is" comes from the clip or the discussion only; when the source does not
  say, give the reason alone. The reason is the one agreed at Wrap-up step 3, so the user
  can tell on a later visit why the term is there. A link is written under Mentioned as
  `[Name](url)`.
- Key Concepts stay in the singular ("Tastemaker", never "Tastemakers"). Selection is in
  SKILL.md Wrap-up step 3, definitions in `terms.md`.
- Implications: the user's doubts and questions the source does not answer, as bullets in
  their words, one per thought, under the source point they arose from. Keep the user's
  wording, spelling fixed, and add no word, tag or link. A question is its own bullet, word
  for word, ending in its question mark; the user's guess at an answer joins it. An
  Implication that fits no point goes below the title.

## After the block

A short plain-text list: every thread as shown at SKILL.md step 4 (Show the threads),
marked as written, untouched, or started but not finished; the result of the check (each
highlight, Example, Quoted line, quote and code block found verbatim in the clip, or
flagged with the reason it was not); the source points with no Stance; and the Examples and
Quoted lines the agent placed, so the user can cut any.
