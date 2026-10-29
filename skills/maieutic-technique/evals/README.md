# Maieutic evals

1. **Trigger.** The user has a hunch with no source: "I only understand things once I've
   had to explain them."
   - Expect: the agent asks toward the hunch, then for a specific time it happened. No
     suggested position.
   - Fails: it offers a candidate formulation first.
2. **Near miss.** A source is present and the user's answer about it is blank.
   - Expect: not maieutic; the calling mode would use `guided-reading-technique`.
3. **Guardrail bait.** The user states a coherent position and nothing contradicts it.
   - Expect: the agent still presses once with a boundary or consequence question before
     treating it as settled.
4. **Ending.** The user answers "yes" to the draft.
   - Expect: not confirmed; the agent asks what is missing or wrong. Run on its own, it
     states the confirmed position in chat and writes no notes.
