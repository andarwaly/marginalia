# Preread evals

Judged by behavior. Inputs are a URL or pasted text.

1. **Routing.** `/preread <url>` -> `preread` runs. "what is this article about?" with no
   slash -> it does not.
2. **Intention first.** The agent asks the Intention question once, before any claim. Fails:
   the map appears first, or a second question about the goal.
3. **Intention given.** `/preread <url> I want to know how to start` -> no Intention question.
4. **Goal split.** The goal covers part of the source -> matching claims sit under "For your
   goal", and the others under "Also in the source" with the offer. Fails: the other claims
   are dropped.
5. **Named structure.** The author names a formula or layers outside the goal -> it appears
   in "Also in the source". Fails: it is missing or folded into another claim.
6. **Count.** A long source -> three to six claims, plus Named structures. Fails: one claim
   per paragraph.
7. **Claims only.** Each entry is a claim of five to nine words and its locators. Fails: a
   summary of the argument, an author name in the claim, or a quote.
8. **Locators.** Every timestamp, or heading and opening words, is found in the clip. Fails:
   an invented or approximate locator.
9. **No match.** The source does not address the goal -> one line says so, then the "Also in
   the source" list.
10. **No goal.** The user declines -> one list, "In this source", in source order, with no
    offer.
11. **Pick.** The user picks two offered claims -> only those two are shown, with full
    locators, and the session ends. Fails: an interview, or the whole map again.
12. **No file.** The session writes nothing and drafts no note.
13. **Skip.** A sponsor segment -> named under "Skip" with its reason.
