---
name: clip-youtube
description: "Fetches a YouTube video's transcript with timestamps and returns it as markdown with its title, channel, date and URL. Use when the user asks to clip a YouTube link, or another skill needs the transcript."
---

# Clip YouTube

Fetch one video's transcript as markdown, verbatim, into a session-only file. Ingest checks
quotes against this file by exact match.

## Steps

1. **Check the tool.** Run `python3 -c "import youtube_transcript_api"`. If it fails, print
   one line and stop: `pip install youtube-transcript-api`. Never install it yourself.
2. **Get the id** from the URL (`watch?v=ID`, `youtu.be/ID`, `/shorts/ID`).
3. **Get the title and channel** (no key needed; this gives no upload date):
   `curl -s "https://www.youtube.com/oembed?url=https://www.youtube.com/watch?v=ID&format=json"`
   Use `title` and `author_name`. Leave `published` empty unless the user gives it.
4. **Get the transcript** into `${TMPDIR:-/tmp}/marginalia/<ID>.md`, never into a vault or
   a repo. With the Python API: `t = YouTubeTranscriptApi().fetch(ID)`; each snippet has
   `text` and `start`, and `t.is_generated` says whether the captions are automatic.
   Write one line per snippet: `[mm:ss](https://youtu.be/ID?t=<seconds>) text`.
5. **Header**, as frontmatter above the lines: `title`, `author` (the channel), `published`,
   `source` (the URL), and `captions: auto-generated` when `is_generated` is true.
6. **Report** the file path and one line: title, channel, duration of the last timestamp.
   Do not summarize the video.

## Fallback

If the API fails (YouTube blocks most cloud IPs, so expect this in cloud sessions):

- Firecrawl, only if its tools are present: its YouTube transcript capability
  (`youtube-com/videos/video_transcript`, about 5 credits; find it with
  `firecrawl_find_tools` if the name differs), called with `video_id`. It returns `title`,
  `kind` (`manual` or `asr`; `asr` means `captions: auto-generated`) and `segments` with
  `start_ms` and `text`. Write the same file format, with seconds = `start_ms / 1000`. It
  gives no upload date. A plain Firecrawl page scrape does not return a transcript. Say
  once that it used a hosted service.
- Otherwise report the failure in one line and ask the user to open the transcript with
  their browser clipper and paste it.

## Rules

- Never use a summarizing fetch tool; the transcript must be verbatim.
- No transcript exists (captions off): report it and write nothing.
- In plain chat there is no shell: ask the user to paste the transcript.
