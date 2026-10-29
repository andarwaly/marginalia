# Thought note

Read at step 6 and step 7.

## Statement gate

Show the claim drafted from the user's confirmed parts, in their wording. Ask: "Here's
what I have, from what you said: <claim>. What's missing or wrong?" Fixed only when the
user answers and adds nothing that changes it. "Yes" or "sounds right" does not fix it;
ask again, naming one part. Called from a technique, ignore its standalone close and
continue at the next step of `ideate`.

## Sign-off pass

One pass at the end, never mid-session. Check the five criteria against the draft:

1. The title is a claim.
2. The note stands alone.
3. It is about one thing. If more than one idea, offer a second note.
4. Every link has a reason.
5. It answers or spawns a "so what". The user's "so what" answer feeds "where it applies"
   and satisfies this.

Too narrow: ask "where else would this hold?" Skip it when the "so what" answer already
names more than one context. Purity check, when the note cites others: every sentence says
something no single cited note said alone; cut or ask about the ones that do not.

## Format

Filename: `✱ <claim sentence>.md`. Drop `\ / * ? " < > |`, turn `:` into ` -`, avoid
`# ^ [ ]`. The `# heading` carries the exact claim with no prefix.

```
---
created: 2026-10-29
updated: 2026-10-29
---
# Claim sentence

<Claim, in one or two sentences.> <Why it holds.> <Where it applies, from the user's
"so what" answer.> A clause can link inline, as in [[✱ other claim|a clause that reads as
part of the sentence]].
```

- Prose, in the order claim, then why, then where it applies. No section labels; a
  heading appears only where a small topic could grow into an article.
- Links are inline; the display text reads as part of the sentence; the `✱` prefix stays in
  the link target. Link only notes the user named.
- A pasted draft updates the note in place; a full rewrite is allowed; bump `updated`.
- Agent positions and tags stay in chat, not in the note.

## After the block

A short plain-text list of the sign-off criteria that need attention, and "Not validated
against a source." when that applies.
