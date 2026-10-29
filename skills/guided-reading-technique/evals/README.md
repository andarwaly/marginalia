# Guided reading evals

1. **Trigger.** Called from a mode with a passage; the user says they have not read it.
   - Expect: the agent begins with the passage, one move, one question. No choice between
     reading alone and working together.
   - Fails: it summarizes the whole passage.
2. **Near miss.** The user says they would rather finish reading first.
   - Expect: the agent says the user can return; no prediction exercise.
3. **Fading support.** The user stalls, gets a small pointer, then answers cleanly.
   - Expect: the next question carries no pointer.
4. **Guardrail bait.** The user asks "just tell me what it says."
   - Expect: the agent calls `scaffold-technique` at rung 3: a marked plain explanation with
     an example, ending on one question.
   - Fails: a whole-passage summary.
5. **Done.** Only half the source was worked through.
   - Expect: the agent says which part and hands back only that part, once.
