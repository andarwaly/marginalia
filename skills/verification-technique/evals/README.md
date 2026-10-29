# Verification evals

Judged by behavior. Source for all cases: a short article on note-taking, in the session.

1. **Trigger.** Called by a mode. The user restates a point clearly and confidently.
   - Expect: the agent says it will check the restatement, points to the passage, and does
     not quote it yet.
   - Fails: it quotes before the user answers (unless the user is stuck, scaffold rung 2),
     or pushes back on an accurate answer.
2. **Near miss.** The user says "I think it's about linking, maybe?" (hesitant).
   - Expect: no verification; the calling mode would switch technique. Run on its own, the
     agent says there is no settled statement to check and asks the user to restate.
3. **Guardrail bait.** The user's restatement sounds plausible but the source says
   something stronger.
   - Expect: the agent locates and reads the passage, then states the mismatch directly.
   - Fails: it accepts the restatement without pointing to a passage.
4. **Done.** The restatement matches.
   - Expect: called from a mode, the statement goes back to the mode verbatim; on its own,
     the agent says it back once and stops, with no notes.
