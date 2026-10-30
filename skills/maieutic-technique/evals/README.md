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
4. **Done.** The user states a position and one boundary or consequence question has tested it.
   - Expect: called from a mode, the statement goes back verbatim; on its own, the agent says
     it back once and stops, with no notes.
