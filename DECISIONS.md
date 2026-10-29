# marginalia: decisions

**Status: OPEN.** This is a discussion record, not a spec. The scaffold is: the plugin
manifests (`.claude-plugin/plugin.json`, `.claude-plugin/marketplace.json`,
`.codex-plugin/plugin.json`), a README, and twelve skill folders.
- Stubs with a working description and a TODO body: `clip-article`, `clip-youtube`,
  `ingest`, `ideate`, `define`, `compass-technique`. `ingest`, `ideate` and `define` also
  have an `agents/openai.yaml` (Codex implicit invocation off). The compass family's four
  original files sit unchanged in `compass-technique/references/`.
- Written: the six technique skills `verification-technique`, `elenchus-technique`,
  `feynman-technique`, `self-explanation-technique`, `guided-reading-technique` and
  `maieutic-technique` (reshaped from the slipbox technique files; see the reshape log).

Items marked Settled were answered explicitly by the owner. Items marked Provisional or
Default may change. Items under Open are the next session's frontier. The owner has
confirmed shared understanding, so bodies are written one skill at a time, in this order:
`ingest` (its six techniques are already written), then the call-by-name test on Claude
Code, Codex and Cowork, then `clip-article` and `clip-youtube`, then `ideate` with the
compass reshape, then `define`. Evals are written alongside each skill.

Last updated: 2026-10-29

## Goal

New public repo, ported and simplified from slipbox (`andarwaly/slipbox`). Not over-engineered.

- Targets Claude Code (local and cloud), Codex, Cowork cloud (planned, setup untested), and
  plain chat.
- Chat support is deferred until the real skills are shaped. The owner notes that Claude
  chat can load skills and ChatGPT cannot (owner-stated, unverified), so the paste route
  matters mainly for ChatGPT.
- Output is markdown in chat for the owner to copy.
- The owner keeps their own implications in the notes, which slipbox literature notes lack.
- Skill text is public and says "the user". This file says "the owner" for the person who
  made these decisions.

## Journey

The owner's flow has two shapes: notes taken from a source, and thoughts from the owner's
own head that they want to refine, optionally backed by a source. The steps below are the
notes shape.

1. The owner reads an article or video and brings it in as a clip (md), a URL, or pasted text.
2. A discussion comes first, to understand the source's context and points. The technique
   used follows how the owner answers.
3. The owner receives copyable markdown notes, to keep or to consult when writing their own.

## Workflow

```
URL                  -> clip-article | clip-youtube -> clip (session only)
clip, or pasted text -> ingest (with techniques)    -> source notes (map + points)
thought (+ backing)  -> ideate                      -> thought note
concept + notes      -> define                      -> Reference note
```

The twelve skill names are confirmed: `clip-article`, `clip-youtube`, `ingest`, `ideate`,
`define`, and the seven `<name>-technique` skills. A better name may still replace one
later.

## Settled

**Environment and distribution**
- Audience: public from day one.
- Harnesses: Claude Code (local and cloud), Codex, Cowork cloud, plain chat. Cloud sessions
  are treated as CLI sessions: same skills, subject to the environment's network policy and
  setup script.
- Distribution: a `skills/` folder plus plugin manifests for both. Install in the owner's
  note vault, or point the agent at the vault repo (cloud = GitHub repo). The ingest side
  (the clip skills, the technique skills and ingest) may be installed outside the vault.
- Install the whole repo. A mode without its technique skills cannot run its interview, so
  each mode says: "If a technique skill is missing, stop and tell the user to install the
  full marginalia set."
- Every input has a paste fallback. Notes are read from the vault when the harness can,
  else pasted. A URL goes through a clip skill (a summarizing fetch tool is not trusted for
  verbatim text), else the text is pasted.
- Plain chat: every path that needs a CLI or file access (clip skills, vault reads, file
  writes) has a pasted-content fallback. In chat the agent checks quotes against the pasted
  text; no file exists. A URL given in chat is answered with a request to paste the text.
  The rest of the chat route is deferred.
- No validator script (a fixed constraint from the owner).
- No subagents anywhere in the repo.
- Name and repo: `marginalia` at `andarwaly/marginalia`. Flat layout, one plugin, no
  marketplace wrapper.
- Skill source: port from slipbox (reference only, never edit). The ten slipbox technique
  files became seven technique skills, reshaped (see the reshape log).

**Skills (twelve)**
- `clip-article` (Defuddle) clips any text resource (an article, blog, Medium or Substack
  page, or a post). `clip-youtube` (`youtube-transcript-api`) clips a YouTube video. Both
  are model-invoked wrappers, so other skills can reach them.
- `ingest` and `ideate` are modes the owner enters, and both are user-invoked. The user
  invokes one with a source or an idea; the agent stays in the mode until the done gate
  (below), and ordinary chat resumes after the notes. `define` is user-invoked too.
- There is no `grounding` skill. The two modes have different mental models: ingest is a
  learning interview where the source is the only authority; ideate is a two-way
  discussion where the agent takes positions. Each mode owns its method.
- Modes are thin. A mode's SKILL.md holds the job, the goal, the hard rules, the technique
  to start with and when to switch, the resume rule, the done state, and a one-line
  definition of every term its rules use. Terms with their fuller explanation, the reading
  states with examples, the statement-gate examples and the note formats live in the
  mode's `references/`, each with a named moment in SKILL.md for when to read it.
- Each mode says: "When a technique reaches a confirmed statement, ignore its standalone
  ending and continue at step N." No harness keeps a call stack, so the resume step lives
  in the mode.
- User-invoked is enforced per harness. Claude Code: `disable-model-invocation: true` in
  the SKILL.md frontmatter. Codex: each of ingest, ideate and define ships an
  `agents/openai.yaml` with `policy: allow_implicit_invocation: false` (the default is
  true; explicit `$skill` invocation still works). Cowork is assumed to read the same
  SKILL.md flag (unverified). Plain chat needs no enforcement.
- SKILL.md size targets: at most 80 lines for each clip skill, 150 for define, 250 for
  ingest and ideate (they should come in well under); a hard cap of 500.
- Clip skills need a CLI tool; in plain chat the owner pastes the text instead. Each checks
  for its tool, prints one install line, never auto-installs. The README carries a
  cloud-setup section.
- Clip fallback order: Defuddle (articles) or `youtube-transcript-api` (video); then
  Firecrawl, an optional second route used only when its tools are present and never a
  dependency; then the owner's browser clipper and a paste. TinyFish is dropped. A failed
  fetch is reported, and the skill asks the owner to clip the page with their browser
  clipper and paste the result. In cloud sessions where YouTube blocks the IP, Firecrawl's
  transcript capability is the route to try.
- Clip v1 covers articles (including Medium and Substack) and YouTube. X goes through
  Firecrawl only, at 30 credits per post, with exact quotes unverified. Reddit and Threads
  are pasted.
- Auto-generated captions: the clip header records `captions: auto-generated`, and ingest
  warns once that quotes may carry transcription errors and quotes them as-is.
- Clips are session-only: written to the harness's temp location, never saved in the
  vault, never committed. They let each quote be checked by exact match.
- `ideate`: the owner enters it with an idea or thought to sharpen, refine, validate or
  extend. It starts from the owner's raw thought; a source may back it. Backing sources
  are pasted or named by the owner; there is no vault search. It is one mode: the verb is
  inferred from the owner's words, with one question if it is unclear. A pasted draft
  means the note is updated, not new; the verb is still inferred. Keeps the purity check
  (slipbox called the idea a Take) and the five sign-off criteria.
  - Technique by verb: sharpen and refine press the owner's statement
    (`feynman-technique`, `verification-technique` against the notes, `elenchus-technique`);
    validate challenges it against the backing quotes (`compass-technique`, east); extend
    asks where it leads (`compass-technique`, south and west), with the owner's answers
    supplying the content; a bare hunch goes to `maieutic-technique`. With no backing
    source, validate asks once for one; if there is none it challenges the owner's
    reasoning alone, and the list below the note says nothing was validated against a source.
  - Two-way rules: every substantive claim the agent makes carries one basis tag, **[note:
    quote]**, **[source: URL]** or **[reasoning]**. A claim about the world must be a note
    or a source; if neither is found the agent searches, and if that fails it marks the
    claim **[unverified]** and does not argue from it. The agent states its position first
    (agree, disagree or partly) and names the strongest counter-argument before agreeing.
    It changes position only for a new reason or new evidence, and says which. Tags go on
    claims, not every sentence. Without web search the agent challenges only from the notes
    or from logic labeled [reasoning], and says it could not check.
  - End condition: the idea is a scoped claim and the strongest objection is answered or
    folded in. Agreement alone does not end the session.
- `define` (was `reference`): a separate output, built last because it sits outside the
  owner's two-part flow. It writes the owner's personal glossary entry: a definition
  first, then examples, where the term is found, and how to use it, each included only
  where the pasted notes support it. If the notes lack one, the agent says what is
  missing and does not invent it. No interview. Keeps the admission sequence and bounded
  lookup.
  - Inputs: the owner names a concept and pastes the point notes that mention it, with
    their maps' frontmatter (author, URL). The skill dedupes sources by URL and author.
    There is no vault scan.
  - Wording: the agent synthesizes one definition from the characterizations in the pasted
    notes, in their wording where they agree, and asks the owner before writing only if
    they conflict. It then shows the entry and asks one open question, "what's missing or
    wrong?" That is one question, not an interview.
  - Ingest gives no admission verdict; admission exists only in `define`.
  - If admission fails, the skill names the failed check and the support still missing. The
    owner may reply "write it anyway", and the note then opens with a one-line caveat such
    as `> Single source: this definition rests on Kowalski alone.` Slipbox never waived the
    gates; this is a deliberate departure.
  - The note is titled with the concept name and uses the `※` prefix. Frontmatter `sources`
    lists the map links; `aliases` lists alternate names the owner gives.
- Conventions: the agent does not need to know the owner's conventions; the owner brings
  them. Defaults are Obsidian flavor and filename prefixes (`§` source notes, `※`
  Reference notes, `✱` thought notes).
- Vocabulary: "source notes" and "thought notes" replace the slipbox terms literature note,
  evergreen note and Take in the docs. The Terms section maps them.

**Technique skills (seven)**
- `verification-technique`, `elenchus-technique`, `feynman-technique`,
  `self-explanation-technique`, `guided-reading-technique`, `maieutic-technique`,
  `compass-technique`. The suffix is `-technique`. Compass owns `connect`, `challenge` and
  `distil` in its `references/`, because compass's own text points at those files.
- Each is model-invoked, so a mode calls it by name through the harness with no `../`
  sibling-path read. Each description opens "Marginalia interview technique, only when a
  marginalia mode calls it or the user names it" and uses no generic verbs, so the skill
  does not fire in ordinary chat.
- Each is self-contained, so it can run on its own. Run on its own, a technique ends with
  the user's confirmed statement in chat and writes no notes. Called from a mode, it
  returns the statement to the mode.
- Each is reshaped from the slipbox file, with ideas kept: a state-based "reach for this
  when" in place of the dispatcher gating, one short pointer to a sibling by skill name at
  most, the same Ending block in all seven (probe before any draft; confirm openly; hand
  back; never finish it for them), a standalone start, and at most about three added lines
  of lessons from real sessions (probe types in feynman, self-explanation and maieutic;
  point but do not quote before the user answers; ask wide before narrow; the
  acknowledgment on its own line). Answer-quality routing (confident, hesitant, blank,
  confused) lives only in `ingest`. The Ending block is kept identical across the seven
  by a manual diff at release.
- Each has an `evals/` folder: 2 or 3 short transcript cases judged by behavior (trigger
  and near-miss, guardrail-bait, the ending). Mode evals focus on switching and resuming.
- The compass family is reshaped when `ideate` is built.

**Ingest behavior**
- Default reading state is "at least skimmed". No upfront reading-state question. If the
  owner says they have not read it fully, run guided-reading.
- Default technique: `verification-technique`, after the owner explains the point in their
  own words. The agent switches by reading state (`ingest/references/reading-the-answer.md`,
  with examples): hesitant → `feynman-technique`; confused → `self-explanation-technique`;
  blank → `guided-reading-technique`; a mismatch with the source → `elenchus-technique`;
  the owner's own reaction → `maieutic-technique`.
- Blank answer: there is no offer to choose between reading and working together. The
  agent acknowledges the blank and works through the passage with guided-reading.
- Opening: see the opening question under Modes and the done gate.
- The agent builds a candidate frontier, each point with an exact verbatim quote, so
  the discussion stays honest. Notes carry quotes only for points the owner picked.
  Unpicked points leave no trace; a partial note is valid.
- Off-script remark: the agent finds the nearest passage and asks, e.g. "The article says
  'x' is 'y'. Is that what you said, or did you have something else in mind?" If the owner
  misread, return to that point. If it is their own read, record it as an Implication in
  their words. If no passage exists, re-check the source before saying so, then ask.
- Depth, for each point the owner picked: interview when it is central to the stated
  inquiry; the agent drafts and source-verifies when it is supporting. Implications are
  always interviewed. Tangents never block.
- The source is the only authority. The agent quotes only after the owner answers, asks one
  question per turn, and writes no note before a statement is confirmed.

**Modes and the done gate**
- Two gates. The statement gate (the Ending block in each technique, and the mode's
  confirmation of its final statement) fixes one statement, only on the owner's open
  confirmation. The done gate (in each mode) decides when the discussion is over and runs
  the closing questions before the notes are produced.
- The opening question is firm. At the start of ingest the agent shows the topics or points
  it found and asks whether the owner has other points and what brought them to the
  source; the answer decides which points are central. In ideate the agent asks one
  question about the verb only when the owner's words leave it unclear.
- Ingest trigger: the owner's signal ("done", "that's everything", or asking for the
  notes). Otherwise, once every point the owner picked is settled, the agent asks once,
  "anything else on this source, or shall we wrap up?" Done at any time yields partial
  notes. A done signal skips step (1); steps (2) to (4) still run once (the assistant's
  reading of "done at any time yields partial notes").
- Ingest closing order: (1) one nudge for points drafted but unconfirmed, then one offer on
  untouched topics; (2) the density check (points resting on the same reasoning merge; a
  list the source presents as a unit becomes one point); (3) the open main-idea question
  ("having been through all of it, what do you think the main idea is?"); (4) the open
  closing question ("what do you think of this article?", adapted to the source: video,
  post), always asked once; a decline ends the questions and the notes still follow;
  (5) the notes, then the coverage and quote-check list (the list is Provisional).
  Whatever the owner adds at (4) becomes an Implication on its point, or on the map if it
  concerns the whole.
- Ideate trigger and done gate: the gate starts when the owner confirms the refined
  statement through the statement gate, or signals done. The agent then asks the "so what"
  question once ("where does this lead, or where would you use it?"), runs the sign-off
  pass, then writes the note. The "so what" answer feeds the body's "where it applies" and
  satisfies sign-off criterion 5; sign-off's "where else would this hold?" is skipped when
  that answer already names more than one context. An early done still gets the "so what"
  question (the assistant's assumptions).

**Output**
- One fenced block per note, each labeled with its filename. Notes are written to files
  only when the owner asks, into a folder they name, after review in chat. Nothing is
  written automatically.
- Map note: frontmatter `author`, `published-at`, `source`; the main idea in the owner's
  confirmed words (no quote); Source Point links. Whole-source Open Questions and
  Implications may sit on the map. Key Concepts and Mentioned are point-only.
- Frontmatter values: `published-at` is ISO `YYYY-MM-DD`, left empty when the clip lacks
  it and never guessed (a video uses its upload date). `author` is a bare wikilink,
  `"[[Name]]"` (for a video, the channel name).
- Filenames and headings: the filename is the prefix, a space, then the title. It drops
  `\ / * ? " < > |`, turns `:` into ` -`, and avoids `# ^ [ ]`. The `# heading` inside
  each note carries the exact title with no prefix; the prefix lives only in filenames and
  link targets, and links hide it with the alias form.
- Quote matching: the words and their order must be identical. These are ignored when
  matching: markdown emphasis, link URLs, footnote markers like `[^1]`, whitespace and
  line breaks, and curly versus straight quotes. A quote is one contiguous run with no
  ellipsis. Boilerplate lines in a clip (sign-in banners, "Press enter or click to view
  image") are never quoted, but the clip skills do not remove them.
- Source Point note: always standalone. Frontmatter `source: [[map]]`; title stated as a
  claim; short source-owned restatement; verbatim quote; Key Concepts; Mentioned; Open
  Questions; Implications.
- An item goes on the point whose quote it is about; an owner-flagged item with no quote
  goes on the map.
- Implications: the owner's own words only, marked reader-owned (the `## Implications`
  heading is the marker), in their own section, never inside the point statement. Bullets
  are first person, lightly tidied for spelling and filler but never reworded. Never
  authored by the agent; the agent only transcribes the owner's words. Captured during the
  session, plus the done gate's open closing question; a decline ends the questions and
  the notes still follow. Replaces slipbox's "parked take ideas" list. Slipbox's
  `*Assumption*` and `*Answered*` bullets are dropped; the owner's guess at an answer
  becomes an Implication bullet that names the question.
- The agent's own view in ingest: it does not fill gaps from general knowledge. When it
  disagrees with or adds to the source, it states so clearly with a fixed label ("My own
  view, not the article's:"), in chat only, after a point is settled and never
  mid-question, at most once per point (the timing is the assistant's assumption). It
  enters a note only if the owner adopts it as an Implication in their words. This
  replaces slipbox's tension-to-backlog feature.
- Terms: each mode keeps `references/terms.md`; its SKILL.md carries a one-line definition
  of each term its rules use. No shared glossary file.
- Chat apps: ChatGPT and Claude chat are the intended apps; to verify. Chat support is
  deferred (see Goal).
- Thought notes:
  - An atomic idea. The title and filename are a full claim sentence, with the `✱` prefix.
  - The body explains in prose, in the order claim, then why, then where it applies. It has
    no section labels; a heading appears only where a small topic could grow into an
    article. The no-label rule is for thought notes only; source notes keep their labeled
    sections.
  - Links are inline, the display text reading as part of the sentence:
    `[[✱ target|clause of the sentence]]`. The prefix stays in the link target.
  - The agent drafts the prose from the owner's confirmed parts, in the owner's wording
    where possible, and the owner approves it through the statement gate. The agent adds
    no claim the owner did not say. A new link is offered as a question, never asserted.
  - Sign-off is one pass at the end, never mid-session. Too broad (more than one idea):
    offer a second note. Too narrow: ask "where else would this hold?" The remaining
    criteria appear as a short plain-text list below the block.
  - The agent does not suggest edits to older notes so they link back. Backlinks cover it,
    and connection-finding is deferred.

**Working descriptions** (what the skill does and when to use it, never its steps; final
wording is fixed when the bodies are written; the technique descriptions are already in
their SKILL.md files):
- `clip-article`: Fetches a text resource from a URL (article, blog post, Medium or
  Substack page, or a post) and returns it as clean markdown with its title, author, date
  and URL. Use when the user asks to clip a URL, or another skill needs a URL's text.
- `clip-youtube`: Fetches a YouTube video's transcript with timestamps and returns it as
  markdown with its title, channel, date and URL. Use when the user asks to clip a YouTube
  link, or another skill needs the transcript.
- `ingest`: A mode for discussing and learning from one source with the user. It ends in
  source notes that keep the source's points apart from the user's implications.
- `ideate`: A mode for sharpening, refining, validating or extending an idea of the
  user's. It ends in one thought note.
- `define`: Writes a glossary entry for a term from the user's pasted notes: a definition,
  then examples, where it is found and how to use it, as far as the notes support.

**Evals** (plain markdown, in each skill's `evals/` folder). Routing table, prompt then
expected skill:
- "clip https://medium.com/..." -> `clip-article`
- "clip this video https://youtu.be/..." -> `clip-youtube`
- "/ingest https://emilkowal.ski/ui/developing-taste" -> `ingest`, which calls `clip-article`
- "/ideate I think asking questions beats reading slower" -> `ideate`
- "/define taste" with pasted notes -> `define`
- "/feynman-technique" naming a topic -> `feynman-technique`, run on its own
- "summarize this article: <URL>", "explain this simply", "challenge my idea", "what does
  this error mean?" -> no skill from this repo (negative cases)

Technique cases are short multi-turn transcripts judged by behavior: one question per turn,
no answer supplied, the right switch, resuming the mode, and "yeah sounds about right" not
closing the run. The old slipbox cases (13, mostly routing, with weak keyword assertions)
seed the ingest routing cases only.

The end-to-end run uses the owner's "Developing Taste" clip: ingest it, ideate a thought
from it, then define "taste".

**Dropped:** setup-slipbox, using-slipbox, write-checks, clip-resource (replaced by the
two clip skills), ground-me and grounding (replaced by the technique skills and the
modes' own methods; the first `grounding/SKILL.md` draft is in git history at 533d522 and
its gate and fidelity text feeds `ingest`), the evergreen backlog.

**Deferred, not designed:** connection-finding across notes.

## Technique reshape log (slipbox file → technique skill)

- All seven: frontmatter added; "Use this when / Don't use this" dispatcher gating became a
  state-based "Reach for this when"; sibling pointers by filename became skill names, at
  most one line; "the Gate" replaced by the shared Ending block; "see SKILL.md's Never
  finish it for them" replaced by that rule inside the Ending block; "user" wording.
- verification: standalone start; "point to the passage, don't quote until they answer".
- elenchus: "never dispatched directly, never an opening move" became "needs a located
  weakness; if none, say so and stop; standalone, ask for a stated position first".
- feynman: refusal on a blank answer became "ask toward what they remember first"; the
  mechanism, boundary and distinction probes; "ask wide before narrow"; acknowledgment line.
- self-explanation: standalone start; probe types; acknowledgment line.
- guided-reading: caller-supplied context became a standalone start; the offer between
  reading alone and working together removed (the user's wish to read first is still
  respected); the gate pointer became the Ending; ask wide before narrow.
- maieutic: also covers the user's own reaction (the Implications use); probe types for
  the test question; acknowledgment line.
- compass family: not reshaped yet. Known fixes for when it is: drop the backlog,
  `derived-from` and database text (an unpursued branch becomes an open thread in the
  closing statement; north is the material in hand); add a start without notes and an
  ending; distil drops its purity-check pointer.

## Provisional

- Thought-note frontmatter: `created` and `updated`; no `type` field (the prefix marks the
  type). The owner was unsure. `related` is dropped because links live in the prose.
- Quote locator: nearest heading for an article, a linked `[mm:ss]` timestamp for a video.
  The owner said "might be located".
- A plain-text coverage and quote-check list below the note blocks.
- Ideate's description trigger names (ideate, refine-idea, validate-idea). The skill is
  user-invoked, so the names serve the slash menu and the owner's memory, not model
  matching.

## Default (not explicitly confirmed)

- Topics are shown as neutral labels; the quote appears after the owner answers.
- Filenames: prefix, a space, then the title (the source title for the map, the claim for
  a point).
- When the owner pastes a draft, the thought note is updated in place; a full rewrite is
  allowed, and `updated` is bumped.
- Authoring rules for SKILL.md bodies:
  - Be strict on the gates that protect fidelity (verbatim quote, Implications in the
    owner's words, quote shown only after the owner answers). Stay adaptive in the
    conversation (technique choice, tangents). Pair each "never" with its positive target.
  - A rule that is not obvious carries a one-clause reason.
  - Cut any line that does not change what the agent does; the agent already knows the
    generic parts.
  - Use concrete limits, not soft words ("one question per turn", not "keep questions
    short").
- Ingest quotes only from the source body. Frontmatter and any AI summary in a clip are
  context, never quoted. A point drawn from material the author quotes is attributed to the
  quoted person (for example "Kowalski quotes Atluru"), never to the author. An empty
  `published` in a clip stays empty rather than guessed.

## Open

1. **Skills.** The final description wording is fixed when the bodies are written. At that
   point, confirm the Implications guard holds in the ported text: slipbox's glossary
   rejected a Take and a Reaction field in the literature note (2026-07-23), and this
   design reverses that on purpose.
2. **Chat route, deferred until the skills are shaped.** The owner says Claude chat can
   load skills and ChatGPT cannot. Chat uploads skills one at a time, which reopens the
   standalone-versus-bundled technique question for that route.
3. **Compass reshape and ideate body,** written together.
4. **To test on a laptop.**
   - the call-by-name path from a mode to a technique on Claude Code, Codex and Cowork
     (a review reported Codex has no Skill tool and opens the SKILL.md path instead;
     unverified). The ingest switching path is tested before the other bodies are written;
   - a one-folder install (the mode should stop and say so, not improvise);
   - routing collisions with the owner's other interview skills (`grounding`, `grilling`,
     `ground-me`) and with ordinary prompts such as "explain this simply";
   - that a technique's standalone ending does not leak when called from a mode;
   - the skills folder each harness reads (`npx skills add andarwaly/marginalia`, Codex,
     cloud repo skills);
   - that `/ingest` still works with the user-invoked flag in Claude Code and Cowork
     (GitHub bug reports say it once failed; unverified). If it fails, fall back to a
     model-invoked skill whose description says it runs only when the user invokes it;
   - the exact path and file name Codex reads for `policy`;
   - plugin manifest paths;
   - Codex cloud and Cowork setup scripts and network allowlists;
   - whether the Firecrawl plugin is available in Codex and Cowork cloud sessions;
   - the temp location for clips;
   - `youtube-transcript-api` from a cloud IP (expected blocked; Firecrawl is the cloud
     route);
   - Firecrawl's main-content filter on Medium;
   - Defuddle on Substack, Reddit, Threads and X (oEmbed and FxTwitter), all untested.

## Terms

- **Source notes:** the notes taken from one source: a map note plus point notes
  (slipbox: literature note).
- **Thought note:** a refined idea of the owner's own, optionally backed by sources
  (slipbox: the nearest relative is the evergreen note; the Take is its central claim).
- **Reference note:** the note `define` writes: the owner's glossary entry for a term
  (slipbox: Reference note).
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
- **Reading state:** how the user's last answer landed: confident, hesitant, blank or
  confused. Ingest routes on it.
- **Statement gate:** the rule that a statement is fixed only on the user's open
  confirmation ("what's missing or wrong?"), never a bare yes. It is the Ending block in
  each technique.
- **Done gate:** each mode's rule for when the discussion ends and the closing questions
  run before the notes are produced.
- **Technique skills:** verification checks a restatement against the source; elenchus
  presses a stated position on a located weakness; feynman has the user explain it plainly
  and patches the gap; self-explanation surfaces a contradiction in a confused answer;
  guided-reading works through a source not yet read; maieutic draws a first statement out
  of nothing and tests it; compass orients a discussion of an idea (north origin, west
  similar via connect, south where it leads, east what competes via challenge; distil
  combines connect and challenge into one new claim).
- **Purity check:** every sentence of a thought note must say something no single cited
  note said alone.
- **Five sign-off criteria:** title is a claim; standalone; about one thing; every link has a
  reason; answers or spawns a "so what".
- **Admission sequence / bounded lookup:** the ordered checks that decide whether a concept
  earns a Reference note, and the rule that a Reference note stays one coherent subject.
- **Defuddle:** a CLI that extracts clean markdown from a web page.
- **Firecrawl:** a hosted scraping service with a plugin; an optional second route for
  clips, billed in credits.
- **Browser clipper:** the owner's Obsidian Web Clipper extension, the final fallback; it
  reads the page and the YouTube transcript through the real browser.

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
- Owner-tested (2026-10-29): Defuddle's CLI cannot read YouTube transcripts without a
  browser, and is blocked on Medium.
- Clip tool findings (2026-10-29, read from source and tested with Firecrawl):
  - Defuddle has extractors for X, Threads, Reddit, Medium, Substack, YouTube and more.
    Medium and Threads read only the HTML they are given; Reddit and X (oEmbed,
    FxTwitter) fetch on their own. Its YouTube transcript fetch uses the unofficial
    InnerTube API and failed in the owner's test.
  - `youtube-transcript-api`'s README says YouTube blocks most cloud-provider IPs.
  - Firecrawl fetched a Medium article (1 credit) and a Substack post (1 credit), returned
    an X post with thread and replies (30 credits), and returned a full timed YouTube
    transcript through `youtube-com/videos/video_transcript` (5 credits), which matched the
    pasted transcript. It refused Reddit and Threads as unsupported. Its YouTube page
    scrape returned no transcript.
  - Reddit: third-party blogs report logged-out `.json` blocked since about May 2026 and
    the official API approval-only. Threads: Meta's oEmbed returns embed markup and
    metadata only, not full text. Neither verified against the platforms' own announcements.
  - Not used: the official clipper CLI (not documented for install and not on npm; needs a
    template JSON), `theharshith/obsidian-clipper-cli` (an older fork reusing the official
    package name), and `harryzhz/webclip-cli` (installs unpinned from GitHub, uses
    Readability, no YouTube).
- Technique design (2026-10-29): three independent Opus reviews. The first recommended
  bundling verbatim technique copies in each mode; the owner rejected it (duplicates, no
  home for evals, cluttered shared references, thin skills want references). The second
  confirmed standalone skills and found the risks recorded above (no call stack, call
  mechanism differs by host, one-folder installs, routing collisions, fragile preface). The
  third, with the technique files and research, found the dispatcher gating, the dangling
  pointers, that "the Gate" was never defined in any technique file, and that the probe
  taxonomy adopted on 2026-08-08 was never built.
- pstack (Cursor): 58 tiny, mostly user-invoked skills; a hub skill reads sibling skills by
  `../<name>/SKILL.md`; no per-skill evals. The sibling-path read is not used here.
- The slipbox research kept the verification/elenchus duplicated guardrail on purpose
  (each technique file readable standalone), and the owner's `grilling` skill was the
  model for the lean interview loop.

## Research pointers

- `andarwaly/skill-kojo`, `discussion/slipbox/discussion-topics/`:
  `personal-drift-and-off-source-questions.md`, `grounding-answer-quality-redesign.md`,
  `claim-density-and-compression.md`, `grounding-probing-taxonomy.md`,
  `ground-my-take-techniques-research.md`, `grounding-verification-elenchus-redundancy.md`,
  `discussion-skill-lean-grilling.md`. `discussion/gems/knowledge/skills/` for skill
  authoring thresholds.
- `andarwaly/slipbox`: `skills/grounding/references/` (the original technique files),
  `tests/grounding/evals.json` (13 old cases).
- Anthropic, "When to fold subagents into your main agent loop"
  (claude.com/resources/articles/building-agents-when-to-fold-subagents-into-your-main-agent-loop).
- Emil Kowalski, "How to write good skills" (aiforui.dev/learn/how-to-write-good-skills):
  strict, focused skills; write the why with each rule; every line must change behavior;
  agents can write skills for agents. UI-focused, a paid-course page, install and star
  counts unverified.
- `cursor/plugins`, `pstack/skills` (the pattern of small skills composed by name).
- The two pastes that set the thought-note shape: Glukhov, "Evergreen notes" for engineers
  (https://www.glukhov.org/knowledge-management/methods/evergreen-notes/) and Andy
  Matuschak, "Evergreen notes" (notes.andymatuschak.org).
- Clip tools: `kepano/defuddle` (README documents `npm install -g defuddle` and
  `npx defuddle parse <url> --markdown`), `jdepoix/youtube-transcript-api` (README section
  on IP bans), `obsidianmd/obsidian-clipper` (contains a CLI), FxTwitter docs
  (docs.fxembed.com). The owner-supplied page deepwiki.com/obsidianmd/obsidian-clipper was
  not readable (network policy).
