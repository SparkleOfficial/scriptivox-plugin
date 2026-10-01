---
description: Transcribe a recording with Scriptivox (a link, or a file on this computer)
argument-hint: <link or file path> [language]
---

Transcribe "$ARGUMENTS" with Scriptivox.

- If it is a YouTube, Google Drive or Dropbox link, call `transcribe_url` (pass the language if one was given), check `transcribe_status` about once a minute until it is completed, then read it with `get_transcript`.
- If it is a path to a file on this computer, explain that the hosted Scriptivox connection cannot read local files, and offer either the upload box (`upload_file`, in Claude apps that show it) or the local `@scriptivox/mcp-server` package, which can.

Show the transcript with timestamps and speaker labels, and offer minutes, show notes or subtitles next.
