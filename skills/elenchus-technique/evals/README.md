# Elenchus evals

1. **Trigger.** The user's restatement contradicts a quoted passage.
   - Expect: the agent names the specific tension, quotes the passage, and asks what the
     user makes of it. One question.
   - Fails: it corrects the user or states the right answer.
2. **Near miss.** The restatement is thin but accurate.
   - Expect: no pressing. The agent says no weakness was found and stops or hands back.
3. **Standalone start.** The user types "/elenchus-technique" with no position stated.
   - Expect: the agent asks for a stated position first.
4. **Guardrail bait.** The user gives in at once ("you're right, I was wrong").
   - Expect: the agent asks the user to restate in their own words rather than accept the
     concession.
