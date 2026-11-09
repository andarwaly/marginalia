# Plain question frames; quote first unless the question needs no passage text

Status: accepted. Supersedes the take-first rule: "show each ask passage after the user's take".

In the "Agents with Taste" session (2026-11-07), the owner asked for clarification four times in 37 questions, and the agent called two of its own questions vague. The owner reads English as a second language and said "what do you make of that?" does not resonate: the words do not say what is asked. The causes sat in the skill. `SKILL.md` and `passages.md` named "What do you make of…" as the model question (twelve of the 37 questions began with it). The take-first rule kept each highlight unseen until the owner answered, so the agent described the passage without its words: "that step", "something about the person doing it", "that last line".

Changes:

- Every question is one frame in `references/questions.md`. Each states what it asks and what kind of answer it wants, names its object in the same sentence, takes fifteen words or fewer plus the shown object, and avoids idiom. The phrases the frames replace are listed there.
- Order is hybrid. A topic question (frame 0) needs no passage text, so the owner answers before meeting the author's words, as before. Any question about a passage shows the author's line first, then frame 1 ("In your own words, what does this line say?") or frame 2 ("Do you agree? Tell me why.").
- **Seen** no longer says "after the user's take": the agent may show the words before or after.
- A request to clarify counts for the whole session: show the object, ask the plainer question, and from then on show the author's line before every question.
- A question that changes topic opens with a short quoted phrase from the owner's last reply, then the link.
- The same idiom is removed from `scaffold-technique` and `verification-technique`.

Considered: always quote first (rejected: the owner may echo the author before forming a view, and frame 0 worked in the session without help); keep take-first and fix only the wording (rejected: any question that must describe hidden text can still come out vague); detect the owner's English level from their replies (rejected: grammar is an unreliable signal and talks down to the user; plain frames help every reader). Risk: a shown line before the question can prime the answer; frame 2 asks for a reason to keep the answer the owner's own.
