# Define evals

Judged by behavior. Inputs are notes with their frontmatter.

1. **Routing.** `/define taste` with pasted notes -> `define` runs. "what does taste mean?"
   with no slash -> it does not.
2. **Admitted.** Two notes, different authors and URLs -> the entry is shown and one question
   asked: "what's missing or wrong?" Fails: an interview, or two questions.
3. **Single source.** Three notes from one article -> unresolved at check 5, with what is
   missing. Nothing written. After "write it anyway", the entry is written with no caveat
   line, and `sources` names the one source.
4. **Entity.** `/define Kowalski` -> check 1 fails; one line, nothing written.
5. **Definition only.** The notes also give examples and usage -> the entry holds the
   definition alone. Fails: an agent-written `## Examples` or other section.
6. **Offer.** The notes hold a line that could support a heading -> below the entry, one line
   names the heading and that note line, and the agent writes no heading. Fails: an offer
   with no note line behind it, or a heading added to the file.
7. **The user's words, neutral.** A note holds the user's Stance on the term and the author's
   wording -> the definition uses the user's vocabulary, with no author name, "he" or "I".
   The user's disagreement stays out. Fails: "Marchese treats it as…", or an opinion.
8. **Conflict.** Two notes define the term differently -> the agent asks which holds before
   writing. Fails: it picks one.
9. **No notes.** No paste, no source note in this session, none named -> the agent asks for
   them; it does not search or use its own knowledge.
10. **Session note.** `/define harness` right after `ingest` drafted a note -> the agent uses
    that note and does not ask for a paste.
11. **Outside knowledge.** The user says "also add what Wikipedia says" -> declined; the entry
    comes only from the notes.
12. **Several terms.** `/define a, b, c` -> the checks are reported together and one question
    is asked for the batch. "Write it anyway" also covers later terms in the session.
14. **Links.** A definition mentions a term with a Reference note, or one in the batch -> the
    first mention is `[[Term|as written]]`. Fails: a link to a note that does not exist, a
    self-link, or a sentence reworded to fit a link.
13. **Vault template.** The vault has a definition template -> the shown entry already uses
    its frontmatter and filename, and the file matches what was shown. Fails: properties
    added after the preview.
