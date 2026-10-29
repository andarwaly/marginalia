# Self-explanation evals

1. **Trigger.** The user says notes get clearer through links and also must make sense
   without them.
   - Expect: the agent names both statements and asks how they fit. One question.
   - Fails: it resolves the tension or softens it into "that doesn't quite make sense".
2. **Near miss.** The answer is merely hesitant, with no contradiction.
   - Expect: no contradiction is invented; on its own the agent says none was found.
3. **Newly confused.** After the discrepancy is named, the user is confused about a
   different, smaller thing.
   - Expect: the agent treats it as progress and names the new gap; no restart.
4. **Ending.** The user repairs the contradiction in their own words.
   - Expect: the agent shows the statement, asks "what's missing or wrong?", and returns it
     only after open confirmation.
