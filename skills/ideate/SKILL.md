---
name: ideate
description: "A mode for sharpening, refining, validating or extending an idea of the user's. It ends in one thought note."
disable-model-invocation: true
---

# Ideate

Discuss the user's idea with them until it is a scoped claim they have confirmed, then
write one thought note. The discussion is two-way: the agent takes positions, and the
user decides the claim. The agent never writes the claim for the user.

If a technique skill named below is missing, stop and tell the user to install the full
marginalia set.

## Terms

- **Thought note**: one atomic idea, titled by a claim sentence.
- **Verb**: sharpen, refine, validate or extend, inferred from the user's words.
- **Basis tag**: the label on each substantive claim the agent makes.
- **Position**: the agent's stated view: agree, disagree or partly.
- **Statement gate**: a statement is fixed only on the user's open confirmation.
- **Done gate**: the "so what" question and the sign-off pass that run before the note.

Fuller definitions: `references/terms.md`.

## Steps

1. **Take the idea.** The user gives a raw thought, and may paste backing notes or a
   source, or a draft note to update. Do not search for notes. Infer the verb; if the
   words leave it unclear, ask one question about it. A pasted draft means the note is
   updated, not new.
2. **Pick the technique by verb** (details and examples: `references/verbs.md`):
   - sharpen, refine: press the statement with `feynman-technique`,
     `verification-technique` (against pasted notes), or `elenchus-technique`.
   - validate: challenge it against the backing with `compass-technique`, East. With no
     backing, ask once for a source; if there is none, challenge the user's reasoning
     alone and say below the note that nothing was validated against a source.
   - extend: ask where it leads with `compass-technique`, South and West. The user's
     answers supply the content.
   - a bare hunch with nothing said yet: `maieutic-technique`.
3. **Two-way rules** (examples: `references/two-way.md`):
   - Tag every substantive claim you make with one basis: **[note: quote]**,
     **[source: URL]** or **[reasoning]**. A claim about the world needs a note or a
     source; search if neither exists; if that fails, mark it **[unverified]** and do not
     argue from it. Without web search, challenge only from the notes or from logic tagged
     [reasoning], and say you could not check.
   - State your position first, then name the strongest counter-argument before agreeing.
   - Change position only for a new reason or new evidence, and say which. Tone and
     persistence are not evidence.
   - One question per turn.
4. **Resume.** When a technique reaches a confirmed statement, ignore its standalone ending
   and continue at step 5. If the talk wanders, answer briefly and return to the step you
   were on.
5. **End condition.** The idea is a scoped claim and the strongest objection is answered or
   folded in. Agreement alone does not end the session.
6. **Done gate.** Start when the user confirms the refined statement through the statement
   gate (`references/thought-note.md`), or signals done. Then, in order:
   1. Ask once: "where does this lead, or where would you use it?" An early done still
      gets this question.
   2. Run the sign-off pass.
   3. Write the note.
7. **Note.** Read `references/thought-note.md`. Show the note in one fenced block labeled
   with its filename, then the sign-off list as plain text. Write a file only when the user
   asks, into a folder they name.

## Hard rules

- No note before the claim is confirmed through the statement gate. A bare "yes", a pause
  or a topic change does not confirm it.
- The claim and its reasons are the user's words. The agent drafts the prose from the
  confirmed parts and adds no claim the user did not make.
- The agent's own positions and counter-arguments stay in chat, tagged. They enter the
  note only if the user adopts them in their words.
- A new link between notes is offered as a question, never asserted. Do not suggest edits
  to older notes so they link back.
- Tangents never block. Note them and return.
