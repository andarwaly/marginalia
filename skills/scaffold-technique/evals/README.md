# Scaffold evals

1. **Settle offer.** The user gives a tentative claim about a passage.
   - Expect: one example, opening with "From my own knowledge, not <Author>'s", in the
     first person, then one question that tests the claim against it.
   - Fails: the agent restates or rewrites the user's claim.
2. **Cap.** A second settle moment in the same thread.
   - Expect: the mode continues with its next step, with no second example.
3. **Ladder start, close.** The user has said half a claim ("it's about care, but I can't
   say how"), then "I'm stuck on this".
   - Expect: rung 1 only: the passage named by its opening words, with no quote and no
     explanation.
4. **Ladder, blank twice.** Two answers in a row with no content.
   - Expect: rung 2: the author's exact words, introduced by name, then one question.
5. **Ladder, explicit ask.** The user says "just explain it".
   - Expect: rung 3: a plain explanation with an example, marked, ending on one question.
6. **One rung per turn.** After rung 1 the user answers with content of their own.
   - Expect: no further rung; the mode continues.
7. **Hand back.** Any rung.
   - Expect: every turn ends on a question, and the wording of the user's claim appears only
     in the user's turns.
8. **Unvouched example.** The user asks for a citation the agent cannot check.
   - Expect: the agent says it is not certain, or chooses another example.
9. **Scaffold stays out of notes.** An offer was made and the user adopted none of it.
   - Expect: the example appears in no source point or claim line.
10. **Both triggers.** The user wants to move on and says they are stuck in one message.
    - Expect: the ladder runs, with no example offer.
11. **Video source.** The clip is a video transcript.
    - Expect: rung 1 names the passage by its timestamp.
12. **Standalone start.** The user types "/scaffold-technique" with nothing stated.
    - Expect: the agent asks what the user is working on and which source.
13. **Standalone, no source.** The user has only a thought, with no source.
    - Expect: no quote rung; scaffolds open with "From my own knowledge:".
