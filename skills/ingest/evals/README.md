# Ingest evals

Judged by behavior, not keywords. Each case: the setup, the expected behavior, and what
fails it. Source for all cases: a short article, "Developing Taste", clipped to the session.

## Routing

1. `/ingest https://emilkowal.ski/ui/developing-taste`
   - Expect: `clip-article` runs, then step 3 opens with topic labels and the two questions.
   - Fails: the agent summarizes the article, or shows quotes at the opening.
2. "summarize this article: <URL>" (no slash)
   - Expect: ingest does not run (it is user-invoked).
3. "explain this simply" / "challenge my idea"
   - Expect: no skill from this repo runs.

## Switching

4. Hesitant. The user answers a point with "something about practice? I think."
   - Expect: `feynman-technique`; one question; no quote yet.
5. Confused. The user says taste is innate and also built by practice.
   - Expect: `self-explanation-technique` names the two claims; does not resolve them.
6. Blank. The user says "no idea."
   - Expect: one-line acknowledgment, no choice offered, then `guided-reading-technique`
     begins with a passage.
7. Mismatch. The user says only experts have taste; the source says anyone can.
   - Expect: `elenchus-technique` quotes the passage and asks; does not correct the user.
8. Reaction. The user says "this reminds me of cooking."
   - Expect: `maieutic-technique`; the result becomes an Implication, not a point.

## Resuming and the gate

9. After a technique reaches a confirmed statement, the standalone ending ("say it in chat
   and stop") does not appear; ingest moves to the next point.
10. The user answers the open confirmation with "yes".
    - Expect: not fixed. The agent asks again, naming one part.
11. The user says "done" with two points unconfirmed.
    - Expect: no nudge; density check, main idea question and closing question still run;
      then partial notes.

## Intention and language

15. At the opening the user answers the second question with "I want to apply this to my
    design reviews".
    - Expect: the topics that answer it are interviewed first; the agent offers no way to
      apply them.
    - Fails: the agent suggests how to apply a point, or infers a topic the answer does not
      point to.
16. The user writes in Indonesian ("Barusan lewat di threads tentang taste… bisa aku
    terapin nanti di workflow").
    - Expect: the agent's questions are in Indonesian; quotes, titles, filenames (with the
      `§` prefix, e.g. `§ Developing Taste`) and point claims stay in English; the main
      idea, Intention and Implications keep the user's Indonesian words.
17. At step 6.4 the intention was given.
    - Expect: the question recalls the user's exact words; the answer is an Implication; the
      map carries `## Intention` unchanged from step 3.

18. At the opening the agent asks "What do you want from this source?" as its own
    question, apart from the other-points question.
    - Fails: it adds a second ask ("and what will you do with it?").
19. The agent asks the user to explain a point.
    - Expect: the question names only the topic.
    - Fails: it states what the source says ("how do you build taste through environment
      and references?").

20. The user answers a point with a hedge, so a technique asks the follow-up.
    - Expect: that question has one ask and does not hint at what the source says.
    - Fails: "and how does it differ from …?", or a contrast the source itself draws.
21. A technique is chosen after the user's answer.
    - Expect: the user sees only the question, never "blank → guided-reading-technique" or
      a state name.

## Notes

12. The notes contain no Implication the user did not say, and every quote appears verbatim
    in the clip. The coverage list repeats the opening topic labels character for character.
13. The agent's own disagreement appears only in chat, labeled "My own view, not the
    article's:", at most once per point, and not in any note.
14. A technique skill is missing (one-folder install). Expect: stop with "install the full
    marginalia set", no improvised interview.
