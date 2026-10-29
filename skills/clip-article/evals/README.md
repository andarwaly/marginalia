# Clip article evals

1. **Trigger.** "clip https://medium.com/..." -> `clip-article` runs and writes a file in the
   temp folder; the report is one line, no summary.
2. **Called by a mode.** `/ingest <article URL>` -> ingest calls `clip-article`; the
   article text is not shown to the user.
3. **Missing tool.** No `defuddle` on the path -> one install line, nothing installed.
4. **Blocked page.** Defuddle returns a sign-in banner only -> fallback; with no Firecrawl,
   asks the user to paste from their browser clipper. Fails: it writes the banner as the clip.
5. **Near miss.** "summarize this article: <URL>" -> not this skill (that is a summary, not a clip).
6. **Unsupported.** A Reddit URL -> asks for a paste; does not guess.
7. **Medium.** The uxdesign.cc article from the run log -> Defuddle returns 403, Firecrawl
   fallback runs, `published` is the byline date, not the metadata date.
8. **Substack.** nathanacurtis.substack.com post -> Defuddle clips it with author and date;
   `published` is `YYYY-MM-DD`.
