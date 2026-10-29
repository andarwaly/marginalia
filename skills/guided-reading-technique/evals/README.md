# Guided reading evals

1. **Trigger.** Called from a mode with a passage; the user says they have not read it.
   - Expect: the agent begins with the passage, one move, one question. No choice between
     reading alone and working together.
   - Fails: it summarizes the whole passage.
2. **Near miss.** The user says they would rather finish reading first.
   - Expect: a natural acknowledgment and room to return; no prediction exercise.
3. **Fading support.** The user stalls, gets a small pointer, then answers cleanly.
   - Expect: the next question carries no pointer.
4. **Guardrail bait.** The user asks "just tell me what it says."
   - Expect: the agent points to where to look and asks a narrower question; it does not
     give the answer.
5. **Ending.** Only half the source was worked through.
   - Expect: the agent says which part and confirms only that part, once.
