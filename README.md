# Scriptivox for Claude and ChatGPT

Scriptivox turns recorded audio and video into accurate text: meetings, interviews, lectures, podcasts and videos, in 119 languages, with speaker labels and timestamps. This plugin connects your Scriptivox account to Claude or ChatGPT and adds three skills that turn transcripts into something useful.

## What you can do

- **Transcribe a link** from Google Drive, Dropbox, TikTok, Instagram, Facebook, X or Snapchat.
- **Drop a file** into an upload box in the chat (up to 2 GB), in apps that show interactive screens.
- **Send a bot** to record a Zoom, Google Meet, Teams or Webex call.
- **Read, search and export** transcripts already in your library (TXT, SRT, VTT, CSV).
- **Edit subtitles** in the chat and download SRT or WebVTT.

## Skills

| Skill | What it writes |
| --- | --- |
| `meeting-minutes` | Summary, decisions, action items with owners and due dates, open questions |
| `podcast-show-notes` | Title ideas, summary, chapters with timestamps, quotes, things mentioned |
| `subtitles` | SRT/VTT subtitles, timing fixes, translation with the same timings |

In Claude Code, `/scriptivox:transcribe` and `/scriptivox:minutes` run the first steps for you.

## Account and billing

You sign in to your own Scriptivox account the first time a tool is used. Transcriptions use your Scriptivox plan, with the same minutes and limits as the website. The plugin cannot buy a plan, add credit or create API keys. You can see and disconnect the connection at https://platform.scriptivox.com/keys.

## What it connects to and what it sends

The plugin has one connection: the Scriptivox server at `https://platform.scriptivox.com/mcp/directory`. It runs no code on your computer. Links you ask it to transcribe, files you upload in the chat, and meeting links you send a bot to go to Scriptivox for transcription. Transcript text comes back to the chat so the assistant can work with it, so the chat app's own data policy applies to it as well. Scriptivox's handling of your data is described in its privacy policy: https://www.scriptivox.com/privacypolicy

Meeting bots join calls as a visible participant named after Scriptivox. Tell the other people on the call that it is being recorded.

## Install

- **Claude (claude.ai, desktop, Cowork):** add Scriptivox from the connector and plugin directory.
- **Claude Code:** `/plugin marketplace add SparkleOfficial/scriptivox-plugin`, then `/plugin install scriptivox@scriptivox`.
- **ChatGPT:** add Scriptivox from the plugin directory.

## Support

support@scriptivox.com · https://www.scriptivox.com/docs/mcp
