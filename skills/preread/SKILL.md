---
name: preread
description: "Shows what a source claims and which passages to read for the user's goal, so they can write the note themselves. Use when the user runs /preread with a URL or pasted text."
disable-model-invocation: true
---

# Preread

Give the user a Reading map: the claims one source makes and where to read each, led by what
they came for. The user does the reading and writes the note. The agent supplies the claims,
the locators and one offer of what else the source holds.

If `clip-article` or `clip-youtube` is missing, stop and tell the user to install the full
marginalia set.

## Terms

- **Reading map**: the one message this skill produces: claims, locators, what else the
  source holds, what to skip.
- **Intention**: why the user came to this source and what they want to understand.
- **Claim**: what the source argues, as a short positive phrase of five to nine words, with
  no author name.
- **Locator**: where a passage sits. A `[mm:ss]` timestamp or range for a video; for an
  article, the nearest heading plus the paragraph's opening words.
- **Named structure**: a formula, layers, framework or list the author names.

## Steps

1. **Get the source.** A URL goes through `clip-article` or `clip-youtube`; pasted text is
   used as is. In plain chat, ask for the pasted text. Read all of it. If the clip says
   `captions: auto-generated`, warn once that the wording may carry transcription errors.
2. **Ask the Intention.** Ask once: "What do you want from this source, and what do you want
   to understand?" When the user already said so while invoking the skill, use that. Done
   after one reply or a decline.
3. **Draft the claims.** Walk the source from the first sentence to the last. Draft three to
   six claims: what the source would still say with everything else removed, weighed by what
   the rest depends on and what the author returns to. Add every Named structure on top of
   those, as a claim of its own. Merge a claim that repeats another. Mark what to skip, with
   the reason: sponsor segments, navigation, boilerplate, repeats.
4. **Sort by the Intention.** A claim goes under "For your goal" when reading it would help
   answer the Intention; every other claim goes under "Also in the source". Order the goal
   list by how directly each claim answers it. With no Intention, all claims go in one list
   titled "In this source", in source order.
5. **Check the locators.** Each one must resolve in the clip: the timestamp exists, or the
   heading and opening words are found. Each claim's locator points at the passage that
   states it. Done when every locator resolves.
6. **Show the Reading map.** One message, in this shape:

   ```
   For your goal:
   1. <claim>
      Read <locator>, then <locator>.

   Also in the source:
   - <claim> <locator>

   Want any of these as well?

   Skip: <what, and why>.
   ```

   A goal entry gets one to three locators. When no claim serves the Intention, say so in one
   line, then show "Also in the source". Leave out the question when that list is empty.
7. **Add and stop.** Add the claims the user picks to the goal list and show only those, with
   their full locators. The session ends after that reply or a decline.

## Hard rules

- Each entry is a claim and its locators. The explanation of the claim stays in the source,
  for the user to read.
- The two questions in steps 2 and 6 are the only ones.
- Write nothing to a file. The user writes the note.
