---
name: clip-article
description: "Fetches a text resource from a URL (article, blog post, Medium or Substack page, or a post) and returns it as clean markdown with its title, author, date and URL. Use when the user asks to clip a URL, or another skill needs a URL's text."
---

# Clip article

Fetch one URL as markdown, verbatim, into a session-only file. Verbatim matters: ingest
checks quotes against this file by exact match, and a summarizing fetch tool (WebFetch and
the like) may drop or reword text, so never use one for this.

## Steps

1. **Check the tool.** Run `command -v defuddle`. If missing, print one line and stop:
   `npm install -g defuddle`. Never install it yourself.
2. **Clip.** Write to `${TMPDIR:-/tmp}/marginalia/`, never into a vault or a repo:
   ```
   mkdir -p "${TMPDIR:-/tmp}/marginalia"
   defuddle parse "<url>" --json -o "${TMPDIR:-/tmp}/marginalia/<slug>.json"
   ```
   Build `<slug>.md` from the JSON: a frontmatter header with `title`, `site`, `source`
   (the URL) and, when not empty, `author` and `published`, then `contentMarkdown` as the
   body. Leave empty fields empty; never guess an author or a date. Write `published` as
   `YYYY-MM-DD` (Defuddle may return `2026-01-16T00:00:00+00:00`; trim it). Note
   `wordCount`, then delete the JSON file.
3. **Check the result.** It fails if the file is empty, holds only a sign-in or
   cookie banner, or is far shorter than the page should be. Then try the fallback. If the
   file cannot be written, stop and report it; never continue from stdout, because ingest
   checks quotes against the file.
4. **Fallback, in order.**
   - Firecrawl, only if its tools are present: `firecrawl_scrape` with the URL, markdown
     format, `maxAge: 0`. Add the same frontmatter header by hand, taking `published` from
     the byline shown on the page; if the metadata date and the byline differ, use the
     byline. Count the words in the saved file. Say once that it used a hosted service.
   - Otherwise report the failure in one line and ask the user to clip the page with their
     browser clipper and paste the result.
5. **Report.** Give the file path and one line: title, author, published, word count. Do
   not summarize the article.

## Rules

- Keep boilerplate lines (sign-in banners, "Press enter or click to view image") as they
  are; ingest knows not to quote them, and removing text breaks verbatim checks.
- Paywalled or login-only page: report it and write nothing.
- X posts go through Firecrawl only (quotes unverified). Reddit and Threads are not
  supported: ask the user to paste the text.
- In plain chat there is no shell: ask the user to paste the text instead.
- Do not read the clip to the user, and do not save it anywhere else.
