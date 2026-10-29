# marginalia

Status: design in progress. Nothing here is usable yet. See [DECISIONS.md](./DECISIONS.md).

Skills that turn a source into notes that keep your own implications apart from the
source's points, and turn your own ideas into refined thought notes. For Claude Code and
Codex; the chat route comes later.

## Planned skills

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
