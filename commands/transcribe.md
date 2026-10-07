---
description: Transcribe a recording with Scriptivox (a link, or a file on this computer)
argument-hint: <link or file path> [language]
---

Transcribe "$ARGUMENTS" with Scriptivox.

- If it is a Google Drive, Dropbox or social-media link, call `transcribe_url` (pass the language if one was given). A progress card shows in apps that support it and posts a message when the transcript is ready; otherwise call `transcribe_status` with `wait_seconds: 25` until it is completed. Then read it with `get_transcript`.
- If it is a path to a file on this computer, explain that the hosted Scriptivox connection cannot read local files, and offer either the upload box (`upload_file`, in Claude apps that show it) or the local `@scriptivox/mcp-server` package, which can.

Show the transcript with timestamps and speaker labels, and offer minutes, show notes or subtitles next.
