---
description: Transcribe a recording with Scriptivox (a link, or a file on this computer)
argument-hint: <link or file path> [language]
---

Transcribe "$ARGUMENTS" with Scriptivox.

- If it is a link (Google Drive, Dropbox, OneDrive, SharePoint, a social-media post, a direct link to an audio or video file, or any other link), call `transcribe_url` (pass the language if one was given). For a link Scriptivox cannot take, YouTube included, its answer says what works instead (usually the recording as a file): follow it. In Claude, on a Scriptivox plan connection, the answer brings the transcript itself when the job ends within about two minutes; otherwise it returns a `transcription_id`. A progress card then shows when the transcript is ready in apps that support it; where none shows, call `transcribe_status` with `wait_seconds: 25` until it is completed. Then read it with `get_transcript`.
- If it is a path to a file on this computer, the hosted Scriptivox connection cannot read it directly: send it with the `upload-from-computer` skill (pass the language to `upload_link` if one was given), or, where you cannot run commands, show the upload box with `upload_file`. In Claude chat, for a file attached to the message, call `upload_file` at once with the file's name as `file_name`, not `upload_link` or your code sandbox.

Show the transcript with timestamps and speaker labels, and offer minutes, show notes or subtitles next.
