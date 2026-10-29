# marginalia

Skills that turn a source into notes that keep your own implications apart from the
source's points, and turn your own ideas into refined thought notes. For Claude Code and
Codex. The chat route comes later.

Status: all twelve skills are written; the cross-harness tests are still to run. See
[DECISIONS.md](./DECISIONS.md) for the design record.

## How it works

```
URL                  -> clip-article | clip-youtube -> clip (session only)
clip, or pasted text -> /ingest   (with techniques)  -> source notes (map + points)
thought (+ backing)  -> /ideate                      -> thought note
concept + notes      -> /define                      -> Reference note
```

- `/ingest` interviews you about one source. The source is the only authority; the agent
  checks what you say against exact quotes and never writes the points for you. Your own
  reactions go in an Implications section, in your words.
- `/ideate` is a two-way discussion about an idea of yours. The agent takes tagged
  positions and names the strongest counter-argument; you decide the claim.
- `/define` writes a glossary entry from notes you paste. No interview.
- Notes appear in chat as copyable markdown. Files are written only when you ask.

## Skills

| Skill | Type | Purpose |
| --- | --- | --- |
| `clip-article` | tool wrapper | Clip a text resource from a URL |
| `clip-youtube` | tool wrapper | Clip a YouTube video's transcript |
| `ingest` | mode, user-invoked | Discuss and learn from one source; source notes out |
| `ideate` | mode, user-invoked | Sharpen, refine, validate or extend an idea; thought note out |
| `define` | user-invoked | Glossary entry for a term, from your notes |
| `verification-technique` | interview technique | Check a restatement against the source |
| `elenchus-technique` | interview technique | Press a stated position on its weak point |
| `feynman-technique` | interview technique | Explain plainly, find the gap, patch it |
| `self-explanation-technique` | interview technique | Repair a confused answer |
| `guided-reading-technique` | interview technique | Work through a source together |
| `maieutic-technique` | interview technique | Draw out a hunch, then test it |
| `compass-technique` | interview technique | Orient an idea: origin, similar, leads, competes |

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
