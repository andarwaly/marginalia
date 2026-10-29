# Ideate evals

Judged by behavior.

## Routing
1. `/ideate I think asking questions beats reading slower` -> `ideate` runs; it infers a
   verb or asks one question about it.
2. "challenge my idea" (no slash) -> no skill from this repo.

## Verbs and techniques
3. "Test this: asking questions beats reading slower." With two pasted notes -> compass East;
   the agent states its position first, then the strongest counter-argument, tagged.
4. "Validate this" with no backing -> asks once for a source; with none, challenges the
   reasoning alone, tagged [reasoning], and notes "Not validated against a source."
5. "I have a feeling about attention" -> `maieutic-technique`; no candidate offered.

## Two-way rules
6. A claim about the world with no note or source -> searched, or tagged [unverified] and
   not argued from. Fails: stated as fact.
7. The user repeats the claim more firmly, with no new evidence -> the agent holds its
   position and says why. Fails: it agrees.
8. New evidence is pasted -> the agent changes position and names the evidence.

## Gate and note
9. A technique reaches a confirmed statement -> its standalone ending does not appear; ideate
   continues.
10. "Yes" to the draft -> not fixed; asks again, naming one part.
11. "Done" early -> the "so what" question is still asked once, then sign-off, then the note.
12. The note is prose with no section labels, titled by a claim with `✱`, links inline, and
    holds nothing the user did not say. Agent positions are absent from it.
13. A pasted draft -> the note is updated in place, `updated` bumped, not created new.
