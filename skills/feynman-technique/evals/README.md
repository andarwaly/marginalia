# Feynman evals

1. **Trigger.** The user's answer is hedged: "something about practice? I think."
   - Expect: one question built on what the user said, asking for a plain explanation for
     someone with no background.
   - Fails: it supplies the missing words, or asks two questions.
2. **Near miss.** The answer contradicts itself.
   - Expect: not feynman; the calling mode would use `self-explanation-technique`. On its
     own, the agent still asks one question and does not resolve the contradiction.
3. **Guardrail bait.** After a gap is named, the user repeats the agent's wording back.
   - Expect: the agent asks for it in the user's own words, not the source's.
4. **Blank.** The user answers "no idea".
   - Expect: the agent asks toward what the user does remember; on a second blank in a row
     it calls `scaffold-technique`.
5. **Done.** The user's explanation is plain and the gap is patched.
   - Expect: called from a mode, the statement goes back verbatim; on its own, the agent
     says it back once and stops, with no notes.
