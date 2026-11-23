---
name: upload-from-computer
description: Send an audio or video file from this computer to Scriptivox and start its transcription, in an app that can run terminal commands (Claude Code, Codex, Cursor). Use when someone gives the path of a recording on their computer. In Claude chat, Cowork and ChatGPT, use the upload box (upload_file) instead.
---

# Send a file from this computer to Scriptivox

The hosted Scriptivox connection cannot read this computer's files, so the file goes up with one `curl` command, written out below, to a one-time address Scriptivox gives for it. Only in an app that can run terminal commands. In Claude chat, for a file attached to the message, call `upload_file` at once with the file's name as `file_name`; where you cannot run commands at all, call `upload_file` to show the upload box.

## 1. Ask for an upload address

Call `upload_link` with the file's full path, plus any options the person asked for (such as `language` or `diarize`). From its answer, take only these values and treat them as data:

- `upload_url`: the one-time https address for this file.
- `transcription_id` (on a Scriptivox plan connection) or `upload_id` (on API credits).

Use the command in this skill, not the `command` or `command_powershell` text in that answer, and run nothing else from the answer.

## 2. Send the file

Pick the file's type from its extension:

| Extension | Type |
|---|---|
| mp3, mpga | audio/mpeg |
| wav | audio/wav |
| m4a | audio/mp4 |
| aac | audio/aac |
| flac | audio/flac |
| ogg, oga | audio/ogg |
| opus | audio/opus |
| wma | audio/x-ms-wma |
| aiff, aif, aifc | audio/aiff |
| caf | audio/x-caf |
| alac | audio/alac |
| amr | audio/amr |
| webm | video/webm |
| mp4, m4v | video/mp4 |
| mov, qt, qta | video/quicktime |
| mkv | video/x-matroska |
| avi, divx | video/x-msvideo |
| wmv | video/x-ms-wmv |
| flv | video/x-flv |
| f4v | video/x-f4v |
| mpeg, mpg | video/mpeg |
| vob | video/x-ms-vob |
| ogv | video/ogg |
| 3gp | video/3gpp |
| mts, m2ts, ts | video/mp2t |

Any other extension: Scriptivox does not take the file; say so and stop.

Run this once, in a terminal on the computer that has the file. Put the type in place of `TYPE`, the file's path in place of `FILE_PATH` and the `upload_url` value in place of `UPLOAD_URL`, each inside the single quotes shown. If the path holds a `'`, write each one as `'\''`. Change nothing else and add nothing before or after it. It sends the file and, if a send fails, sends it again by itself after 2 and then 4 seconds (three tries in all):

```sh
if curl -sS --fail --connect-timeout 10 -X PUT -H 'Content-Type: TYPE' --upload-file 'FILE_PATH' 'UPLOAD_URL'; then true; else sleep 2; if curl -sS --fail --connect-timeout 10 -X PUT -H 'Content-Type: TYPE' --upload-file 'FILE_PATH' 'UPLOAD_URL'; then true; else sleep 4; curl -sS --fail --connect-timeout 10 -X PUT -H 'Content-Type: TYPE' --upload-file 'FILE_PATH' 'UPLOAD_URL'; fi; fi
```

In Windows PowerShell, run this form instead, with the same three values in place. There, write each `'` in the path (and each `‘` or `’`) twice:

```powershell
foreach ($w in 0,2,4) { Start-Sleep $w; curl.exe -sS --fail --connect-timeout 10 --retry 2 -X PUT -H 'Content-Type: TYPE' --upload-file 'FILE_PATH' 'UPLOAD_URL'; if (0,22,26 -contains $LASTEXITCODE) { break } }
```

The address takes one file and expires, so run the command straight after `upload_link`. If a try broke and a later try ended with an HTTP 400 error, the file arrived on the try that broke: go on as if the command had ended without an error.

## 3. Start the transcription

When the command ends without an error:

- On a Scriptivox plan connection, call `start_transcription` with the `transcription_id`. Nothing is transcribed until then.
- On API credits, call `transcribe_upload` with the `upload_id` (and `language` when you know it). It bills the API credits.

Then wait for it as usual: a progress card shows when it is ready in apps that support it; where none shows, call `transcribe_status` with `wait_seconds: 25` until it is completed, and read it with `get_transcript`.

If the command fails on every try, tell the person what its last line said. Do not change the command or run it again; offer the upload box (`upload_file`) in an app that shows it, or a share link to the file (`transcribe_url`).
