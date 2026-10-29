# Clip YouTube evals

1. **Trigger.** "clip this video https://youtu.be/..." -> `clip-youtube` runs, writes a file
   in the temp folder with a header and timestamped lines; one-line report.
2. **Auto captions.** The video has generated captions -> the header says
   `captions: auto-generated`.
3. **Blocked IP.** The API raises an IP block -> Firecrawl's transcript capability if
   present, otherwise a request to paste. Fails: the agent summarizes from memory.
4. **No date.** `published` stays empty; it is never guessed.
5. **Near miss.** "what is this video about? <URL>" -> not this skill.
6. **Missing tool.** No `youtube_transcript_api` -> one install line, nothing installed.
