---
description: Transcribe a recording with Scriptivox (a link, or a file on this computer)
argument-hint: <link or file path> [language]
---

Transcribe "$ARGUMENTS" with Scriptivox.

- If it is a Google Drive, Dropbox or social-media link, call `transcribe_url` (pass the language if one was given). A progress card shows in apps that support it and posts a message when the transcript is ready; otherwise call `transcribe_status` with `wait_seconds: 25` until it is completed. Then read it with `get_transcript`.
- If it is a path to a file on this computer, the hosted Scriptivox connection cannot read it directly: call `upload_link` with the path and run the `curl` command it returns, then call `start_transcription` with the `transcription_id` it gave you (nothing is transcribed until then), or, where you cannot run commands, show the upload box with `upload_file`. In Claude chat, for a file attached to the message, call `upload_file` at once with the file's name as `file_name`, not `upload_link` or your code sandbox.

Show the transcript with timestamps and speaker labels, and offer minutes, show notes or subtitles next.
