# marginalia

Skills that sharpen your thinking about a source or an idea. Each session ends with a
draft note that keeps your own words apart from the source's points, for you to refine. For
Claude Code and Codex. The chat route comes later.

Status: all fourteen skills are written; the redesigned `ingest` has not been tested yet.
See [CONTEXT.md](./CONTEXT.md) for the terms and [docs/adr/](./docs/adr/) for the decisions;
[DECISIONS.md](./DECISIONS.md) is the earlier record.

## How it works

```
URL                  -> clip-article | clip-youtube -> clip (session only)
clip, or pasted text -> /ingest   (with techniques)  -> source note (draft)
thought (+ backing)  -> /ideate                      -> thought note
concept + notes      -> /define                      -> Reference note
clip, or pasted text -> /sift                     -> Reading map (chat only)
```

- `/ingest` discusses one source with you, thread by thread, and walks the whole source,
  examples and code blocks included. The agent checks your claims against exact quotes,
  answers your own ideas with its marked view and the author's passage that bears on
  them, adds a marked example when you are about to settle or are stuck, and never
  writes your claims for you. The draft source note holds each point, your own thinking
  in your words, the author's examples and quoted people, and the terms and names the
  discussion used.
- `/ideate` is a two-way discussion about an idea of yours. The agent takes tagged
  positions and names the strongest counter-argument; you decide the claim.
- `/define` writes a one-definition glossary entry from your notes. No interview.
- `/sift` asks your goal, then shows the source's claims and which passages to read. You
  write the note.
- Notes appear in chat as copyable markdown. Files are written only after you review the
  notes and name a folder.

## Skills

| Skill | Type | Purpose |
| --- | --- | --- |
| `clip-article` | tool wrapper | Clip a text resource from a URL |
| `clip-youtube` | tool wrapper | Clip a YouTube video's transcript |
| `ingest` | mode, user-invoked | Discuss and learn from one source; source notes out |
| `ideate` | mode, user-invoked | Sharpen, refine, validate or extend an idea; thought note out |
| `define` | user-invoked | Glossary entry for a term, from your notes |
| `sift` | user-invoked | The claims in a source and where to read them |
| `verification-technique` | interview technique | Check a restatement against the source |
| `elenchus-technique` | interview technique | Press a stated position on its weak point |
| `feynman-technique` | interview technique | Explain plainly, find the gap, patch it |
| `self-explanation-technique` | interview technique | Repair a confused answer |
| `guided-reading-technique` | interview technique | Work through a source together |
| `maieutic-technique` | interview technique | Draw out a hunch, then test it |
| `compass-technique` | interview technique | Orient an idea: origin, similar, leads, competes |
| `scaffold-technique` | interview technique | Add one marked example, or help when stuck |

The modes call the technique skills by name. Install the whole repo; a mode without its
techniques cannot run its interview.

## Install

- Claude Code: add the repo as a plugin (`.claude-plugin/`), or copy `skills/` into
  `.claude/skills/`.
- Codex: the plugin manifest is in `.codex-plugin/`. The three modes ship
  `agents/openai.yaml` with implicit invocation off, so they run only when you call them.
- Install in your note vault, or point the agent at the vault repo. The ingest side (the
  clip skills, the technique skills and `ingest`) may live outside the vault.

## Clip tools

The clip skills need a CLI tool, check for it and print one install line, and never install
it themselves. Without them, paste the text.

- `clip-article`: `npm install -g defuddle`
- `clip-youtube`: `pip install youtube-transcript-api`
- Optional second route: the Firecrawl plugin, used only when present (billed in credits).
  It reads Medium when Defuddle is blocked, and YouTube transcripts when YouTube blocks the
  machine's IP.

## Cloud setup

In a cloud session, set up once in the environment:

- Setup script: install `defuddle` and `youtube-transcript-api`.
- Network policy: allow `youtube.com`, the sites you clip (Medium, Substack), `registry.npmjs.org`
  and `pypi.org`.
- YouTube blocks most cloud IPs; expect to use the Firecrawl route or paste the transcript.
- Clips are written to the temp folder, never to your vault.
