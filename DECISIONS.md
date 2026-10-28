# marginalia: decisions

**Status: OPEN.** This is a discussion record, not a spec. Only a stub scaffold exists:
`.claude-plugin/plugin.json`, `.claude-plugin/marketplace.json`, `.codex-plugin/plugin.json`,
empty stubs `skills/{ingest,ideate,reference}/SKILL.md`, and a README. Stubs for
`clip-article`, `clip-youtube` and `grounding` do not exist yet. Items marked Settled were
answered explicitly by the owner. Items marked Provisional or Default may change. Items
under Open are the next session's frontier. Do not write skill bodies until the owner
confirms shared understanding.

Last updated: 2026-10-28

## Goal

New public repo, ported and simplified from slipbox (`andarwaly/slipbox`). Not over-engineered.

- Targets Claude Code (local and cloud), Codex, Cowork cloud (planned, setup untested), and
  plain chat.
- Skills must also work pasted into a plain chat (ChatGPT, Claude chat).
- Output is markdown in chat for the owner to copy.
- The owner keeps their own implications in the notes, which slipbox literature notes lack.

## Journey

The owner's flow has two shapes: notes taken from a source, and thoughts from the owner's
own head that they want to refine, optionally backed by a source. The steps below are the
notes shape.

1. The owner reads an article or video and brings it in as a clip (md), a URL, or pasted text.
2. A grounding session comes first, to understand the source's context and points. The
   technique used follows how the owner answers.
3. The owner receives copyable markdown notes, to keep or to consult when writing their own.

## Workflow

```
URL                 -> clip-article | clip-youtube -> clip (session only)
clip, or pasted text -> ingest (with grounding)    -> source notes (map + points)
thought (+ backing) -> ideate (refine)             -> thought note
concept + notes     -> reference                   -> Reference note
```

Skill names in this file are working names. Renaming stays open.

## Settled

**Environment and distribution**
- Audience: public from day one.
- Harnesses: Claude Code (local and cloud), Codex, Cowork cloud, plain chat. Cloud sessions
  are treated as CLI sessions: same skills, subject to the environment's network policy and
  setup script.
- Distribution: a `skills/` folder plus plugin manifests for both. Install in the owner's
  note vault, or point the agent at the vault repo (cloud = GitHub repo). The ingest and
  grounding skills may be installed outside the vault.
- Every input has a paste fallback. Notes are read from the vault when the harness can,
  else pasted. A URL goes through a clip skill (a summarizing fetch tool is not trusted for
  verbatim text), else the text is pasted.
- Plain chat: every path that needs a CLI or file access (clip skills, vault reads, file
  writes, progressive technique loading) has a pasted-content fallback. In chat the agent
  checks quotes against the pasted text; no file exists.
- No validator script (a fixed constraint from the owner).
- No subagents anywhere in the repo.
- Name and repo: `marginalia` at `andarwaly/marginalia`. Flat layout, one plugin, no
  marketplace wrapper.
- Skill source: port from slipbox (reference only, never edit). All ten grounding
  technique files port verbatim, unedited: verification, elenchus, feynman,
  self-explanation, guided-reading, maieutic, compass, connect, challenge, distil.

**Skills (six, working names)**
- `clip-article` (Defuddle), `clip-youtube` (`youtube-transcript-api`), `grounding`,
  `ingest`, `ideate`, `reference`.
- Clip skills need a CLI tool; in plain chat the owner pastes the text instead. Firecrawl
  and TinyFish are dropped. A blocked fetch is reported with an ask to paste. Each checks
  for its tool, prints one install line, never auto-installs. The README carries a
  cloud-setup section.
- Clips are session-only: written to the harness's temp location, never saved in the
  vault, never committed. They let each quote be checked by exact match.
- `grounding` is one skill holding the ten technique files. Each calling skill's SKILL.md
  names which technique files it uses, one level deep.
  - ingest (source-bound; source notes in Luhmann's bibliographic tradition): the
    reading dispatch (verification, feynman, self-explanation, guided-reading), elenchus
    on a mismatch, maieutic for Implications.
  - ideate (the agent is held to the owner's notes; the owner is free): compass with
    connect, challenge, distil; maieutic for a bare hunch; the same dispatch for the
    owner's answers.
- `ideate`: refining the owner's idea at most. It starts from the owner's raw thought; a
  source may back it. Backing sources are pasted or named by the owner; there is no vault
  search. Modes inferred from input (no draft = new, draft = refine); validate folds into
  refine as the challenge step. Keeps the purity check (slipbox called the idea a Take)
  and the five sign-off criteria. Trigger names in the description (provisional): ideate,
  refine-idea, validate-idea.
- `reference`: a separate output, built last because it sits outside the owner's two-part
  flow. The owner names a concept and supplies the notes that mention it. Keeps the
  admission sequence and bounded lookup. No grounding interview.
- Conventions: the agent does not need to know the owner's conventions; the owner brings
  them. Defaults are Obsidian flavor and filename prefixes (`§` source notes, `※`
  reference, `✱` thought notes).
- Vocabulary: "source notes" and "thought notes" replace the slipbox terms literature note,
  evergreen note and Take in the docs. The Terms section maps them.

**Grounding behavior**
- Default reading state is "at least skimmed". No upfront reading-state question. If the
  owner says they have not read it fully, run guided-reading.
- The agent picks a technique from how the owner answers (confident, hesitant, blank,
  confused).
- Opening: the agent shows the topics or points it found and asks whether the owner has
  other points or what brought them to the source. It asks once per source.
- The agent builds a candidate frontier, each point with an exact verbatim quote, so
  the discussion stays honest. Notes carry quotes only for points the owner picked.
  Unpicked points leave no trace; a partial note is valid.
- Off-script remark: the agent finds the nearest passage and asks, e.g. "The article says
  'x' is 'y'. Is that what you said, or did you have something else in mind?" If the owner
  misread, return to that point. If it is their own read, record it as an Implication in
  their words. If no passage exists, re-check the source before saying so, then ask.
- Depth, for each point the owner picks: interview when it is central to the stated
  inquiry; the agent drafts and source-verifies when it is supporting. Implications are
  always interviewed. Tangents never block.
- Technique loading: progressive in the CLIs. In plain chat the last fallback is pasted
  content: SKILL.md asks the owner to paste the named technique file.

**Output**
- One fenced block per note, each labeled with its filename. Notes are written to files
  only when the owner asks, into a folder they name, after review in chat. Nothing is
  written automatically.
- Map note: frontmatter `author`, `published-at`, `source`; the main idea in the owner's
  confirmed words (no quote); Source Point links. Whole-source Open Questions and
  Implications may sit on the map. Key Concepts and Mentioned are point-only.
- Source Point note: always standalone. Frontmatter `source: [[map]]`; title stated as a
  claim; short source-owned restatement; verbatim quote; Key Concepts; Mentioned; Open
  Questions; Implications.
- An item goes on the point whose quote it is about; an owner-flagged item with no quote
  goes on the map.
- Implications: the owner's own words only, marked reader-owned, in their own section,
  never inside the point statement. Never authored by the agent; the agent only
  transcribes the owner's words. Captured during the session. Replaces slipbox's "parked
  take ideas" list.
- Terms: each SKILL.md carries a short "terms used here" block. No shared glossary file.
- Chat apps: ChatGPT and Claude chat are the intended apps; to verify.
- Thought notes:
  - An atomic idea. The title and filename are a full claim sentence, with the `✱` prefix.
  - The body explains in prose, in the order claim, then why, then where it applies. It has
    no section labels; a heading appears only where a small topic could grow into an
    article. The no-label rule is for thought notes only; source notes keep their labeled
    sections.
  - Links are inline, the display text reading as part of the sentence:
    `[[✱ target|clause of the sentence]]`. The prefix stays in the link target.
  - The agent drafts the prose from the owner's confirmed parts, in the owner's wording
    where possible, and the owner approves it through the open Gate. The agent adds no claim
    the owner did not say. A new link is offered as a question, never asserted.
  - Sign-off is one pass at the end, never mid-session. Too broad (more than one idea):
    offer a second note. Too narrow: ask "where else would this hold?" The remaining
    criteria appear as a short plain-text list below the block.
  - The agent does not suggest edits to older notes so they link back. Backlinks cover it,
    and connection-finding is deferred.

**Dropped:** setup-slipbox, using-slipbox, write-checks, clip-resource (replaced by the
two clip skills), ground-me (folds into grounding), the evergreen backlog.

**Deferred, not designed:** connection-finding across notes.

## Provisional

- Thought-note frontmatter: `created` and `updated`; no `type` field (the prefix marks the
  type). The owner was unsure. `related` is dropped because links live in the prose.
- Quote locator: nearest heading for an article, a linked `[mm:ss]` timestamp for a video.
  The owner said "might be located".
- A plain-text coverage and quote-check list below the note blocks.
- A one-line fallback in each dispatch row, used when the technique file is not pasted.

## Default (not explicitly confirmed)

- Topics are shown as neutral labels; the quote appears after the owner answers.
- Filenames: prefix, a space, then the title (the source title for the map, the claim for
  a point).
- An ingest session ends when the owner says so or the energy winds down. The agent nudges
  once for points drafted but unconfirmed, asks the main-idea question openly, and then
  produces the notes (slipbox practice).
- Refine mode may fully rewrite an existing thought note and bumps `updated`.
- Authoring rules for SKILL.md bodies:
  - Be strict on the gates that protect fidelity (verbatim quote, Implications in the
    owner's words, quote shown only after the owner answers). Stay adaptive in the
    conversation (technique choice, tangents). Pair each "never" with its positive target.
  - A rule that is not obvious carries a one-clause reason.
  - Cut any line that does not change what the agent does; the agent already knows the
    generic parts.
  - Use concrete limits, not soft words ("one question per turn", not "keep questions
    short").

## Open

1. **Skill names.** All six are working names. Rename if a better name turns up.
2. **Implications guard.** Slipbox's glossary rejected a Take and a Reaction field in the
   literature note (2026-07-23). This design reverses that on purpose through a separate,
   marked Implications section. Confirm the guard holds in the ported skill.
3. **Reference skill inputs.** Point notes are pasted; the `source` link gives a dedupe
   key; admission verdict placement; the vault-read route.
4. **Skills.** A per-skill type table; distinct descriptions; SKILL.md under 500 lines;
   where the dispatch table lives (grounding or each caller); a small eval list as plain
   markdown (a handful of golden prompts per skill and one end to end).
5. **Frontmatter values.** The `published-at` format; what `author` means for a video;
   filename sanitization.
6. **Plain-chat access to technique files.** How the owner gets them (raw repo URLs).
7. **To test on a laptop.**
   - the skills folder each harness reads (`npx skills add andarwaly/marginalia`, Codex,
     cloud repo skills);
   - plugin manifest paths;
   - Codex cloud and Cowork setup scripts and network allowlists;
   - the temp location for clips;
   - YouTube blocking cloud IPs.

## Terms

- **Source notes:** the notes taken from one source: a map note plus point notes
  (slipbox: literature note).
- **Thought note:** a refined idea of the owner's own, optionally backed by sources
  (slipbox: the nearest relative is the evergreen note; the Take is its central claim).
- **Map note:** one per source; the main idea plus links to its point notes.
- **Point note (Source Point):** one standalone, independently citable proposition from the
  source, with its verbatim quote.
- **Main idea:** what the source chiefly argues, in one sentence (slipbox: Core Idea).
- **Frontier:** the agent's candidate set of points, each with an exact quote, used for the
  discussion.
- **Implications:** the owner's own reactions, kept apart from the source's points.
- **Key Concepts:** abstract concepts, methods or frameworks a point leans on.
- **Mentioned:** concrete named people, places, organizations, works, tools or events.
- **Open Questions:** gaps the source leaves, flagged by the owner only.
- **Dispatch:** choosing a grounding technique from the quality of the owner's answer.
- **Techniques:** verification checks a restatement against the source; elenchus presses a
  claim from several angles after a mismatch; feynman has the owner explain it plainly and
  patches the gap; self-explanation surfaces a contradiction in a confused answer;
  guided-reading works through a source not yet read; maieutic draws a first statement out
  of nothing; compass orients a synthesis (north origin, west similar via connect, south
  where it leads, east what competes via challenge); distil combines connect and challenge
  into one new claim.
- **Purity check:** every sentence of a thought note must say something no single cited
  note said alone.
- **Five sign-off criteria:** title is a claim; standalone; about one thing; every link has a
  reason; answers or spawns a "so what".
- **Admission sequence / bounded lookup:** the ordered checks that decide whether a concept
  earns a Reference note, and the rule that a Reference note stays one coherent subject.
- **Defuddle:** a CLI that extracts clean markdown from a web page.

## Port notes (from reading slipbox)

- About 41% of slipbox SKILL.md lines are runtime plumbing and do not port.
- The evergreen backlog was the only cross-session state. Implications and pasted notes
  replace it.
- Reference admission needs two independent sources unless one is an authoritative
  standard, so a single-source ingest rarely admits a Reference note. Concepts get a
  one-line characterization inside a point note's Key Concepts.
- Slipbox clip-resource: Defuddle as a direct binary (not npx), `youtube-transcript-api`
  directly (not the `ytt` wrapper), no Whisper fallback, paywalls reported and nothing
  written. A summarizing fetch tool silently dropped content once.

## Research pointers

- `andarwaly/skill-kojo`, `discussion/slipbox/discussion-topics/`:
  `personal-drift-and-off-source-questions.md`, `grounding-answer-quality-redesign.md`,
  `claim-density-and-compression.md`. `discussion/gems/knowledge/skills/` for skill
  authoring thresholds.
- Anthropic, "When to fold subagents into your main agent loop"
  (claude.com/resources/articles/building-agents-when-to-fold-subagents-into-your-main-agent-loop).
- Emil Kowalski, "How to write good skills" (aiforui.dev/learn/how-to-write-good-skills):
  strict, focused skills; write the why with each rule; every line must change behavior;
  agents can write skills for agents. UI-focused, a paid-course page, install and star
  counts unverified.
- The two pastes that set the thought-note shape: Glukhov, "Evergreen notes" for engineers
  (https://www.glukhov.org/knowledge-management/methods/evergreen-notes/) and Andy
  Matuschak, "Evergreen notes" (notes.andymatuschak.org).
