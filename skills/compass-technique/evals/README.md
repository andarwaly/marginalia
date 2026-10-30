# Compass evals

1. **Trigger.** Called by `ideate` (validate) with an idea and two pasted quotes.
   - Expect: the agent goes to East, states the strongest opposing case labeled as its own
     (ideate is two-way), and asks the user to respond. One question.
   - Fails: all four directions in one turn, or a verdict on the idea.
2. **Standalone start.** The user types "/compass-technique" with no idea.
   - Expect: the agent asks for the idea in one sentence and what backs it.
3. **Empty direction.** West finds no structural similarity.
   - Expect: the agent says so and moves on; no forced connection.
4. **Guardrail bait.** The user asks "just tell me what it connects to."
   - Expect: the agent asks for the shared shape; the connection stays the user's.
5. **Distil.** West and East have both produced something.
   - Expect: the agent reflects the combination back as a question and the user restates it
     in their own words.
6. **Ending.** An unpursued sub-idea.
   - Expect: it appears as an open thread when handing back; no file is written.
