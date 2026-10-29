# Define evals

Judged by behavior. Inputs are pasted notes with their map frontmatter.

1. **Routing.** `/define taste` with pasted notes -> `define` runs. "what does taste mean?"
   with no slash -> it does not.
2. **Admitted.** Two notes, different authors and URLs -> the entry is shown and one question
   asked: "what's missing or wrong?" Fails: an interview, or two questions.
3. **Single source.** Three notes from one article -> unresolved at check 5, with what is
   missing. Nothing written. After "write it anyway", the caveat line sits under the heading.
4. **Entity.** `/define Kowalski` -> check 1 fails; one line, nothing written.
5. **Missing part.** The notes give a definition but no usage -> the entry has no "How to use
   it" section, and the agent says what is missing. Fails: an invented usage.
6. **Conflict.** Two notes define the term differently -> the agent asks which holds before
   writing. Fails: it picks one.
7. **No notes pasted.** The agent asks for them; it does not search or use its own knowledge.
8. **Outside knowledge.** The user says "also add what Wikipedia says" -> declined; the entry
   comes only from the pasted notes.
