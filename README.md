# Scriptivox for Claude and ChatGPT

Scriptivox turns recorded audio and video into accurate text: meetings, interviews, lectures, podcasts and videos, in 119 languages, with speaker labels and timestamps. This plugin connects your Scriptivox account to Claude or ChatGPT and adds six skills that turn transcripts into something useful.

## What you can do

- **Transcribe a link** from Google Drive, Dropbox, OneDrive, SharePoint (including Teams recordings shared with "Anyone with the link"), TikTok, Instagram, Facebook, X or Snapchat, or a direct link to an audio or video file on any public website.
- **Drop a file** into an upload box in the chat (up to 5 GB), in apps that show interactive screens.
- **Send a bot** to record a Zoom, Google Meet, Teams or Webex call.
- **Read, search and export** transcripts already in your library: PDF, Word, TXT, CSV, SRT or VTT, several at once as one ZIP, with the website's export options (words, characters and seconds per caption, timestamps, speakers).
- **Organise your library**: create, rename and delete folders and workspaces, tag transcripts, and delete transcripts. Deleted transcripts go to the website's Trash, where only you can restore them; the assistant cannot see or empty Trash. Deleting a folder, a workspace or several transcripts at once needs your yes in the chat first.
- **Your calendar's meetings**: if you connected a calendar on the website, see your upcoming meetings and turn the recording bot on or off for any of them, or for all ("record all meetings", after your yes). Connecting or disconnecting a calendar is only done on the website.
- **Edit subtitles** in the chat and download SRT or WebVTT.
- **Run your automations** (Claude): list and run the automations you built on the website. Creating and editing them stays on the website.

## Skills

| Skill | What it writes |
| --- | --- |
| `meeting-minutes` | Summary, decisions, action items with owners and due dates, open questions |
| `podcast-show-notes` | Title ideas, summary, chapters with timestamps, quotes, things mentioned |
| `subtitles` | SRT/VTT subtitles, timing fixes, translation with the same timings |
| `interview-analysis` | Themes, quotes with timestamps, how answers compare across interviews |
| `lecture-notes` | Study notes: outline, key terms, worked examples, review questions, each with timestamps |
| `translated-captions` | Subtitles in another language, with every timestamp kept |

In Claude Code, `/scriptivox:transcribe` and `/scriptivox:minutes` run the first steps for you.

## Account and billing

You sign in to your own Scriptivox account when you connect it: in Claude, on the plugin's Connectors tab or in Settings → Connectors; in Claude Code, with `/mcp`. The sign-in page asks what the connection uses: your Scriptivox plan (the same minutes and limits as the website; it cannot buy a plan, add credit or create API keys) or your API credits, and how much it may do. You can see, change and disconnect the connection at https://www.scriptivox.com/account/connections.

## What it connects to and what it sends

The plugin has one connection: the Scriptivox server at `https://platform.scriptivox.com/mcp`. In Claude chat, Cowork and ChatGPT it runs no code on your computer. In Claude Code (or another app with a terminal), to send a file from your computer it can ask the assistant to run one `curl` command that uploads that file over HTTPS to Scriptivox's file storage (Supabase, or Amazon S3 for API-credits uploads), at a one-time address the Scriptivox server gives for that file. Nothing is installed and nothing else runs. Links you ask it to transcribe, files you upload in the chat, and meeting links you send a bot to go to Scriptivox for transcription. Transcript text comes back to the chat so the assistant can work with it, so the chat app's own data policy applies to it as well. Scriptivox's handling of your data is described in its privacy policy (below).

Meeting bots join calls as a visible participant named after Scriptivox. Tell the other people on the call that it is being recorded.

## Privacy policy

https://www.scriptivox.com/privacypolicy

## Install

- **Claude (claude.ai, desktop, Cowork):** add Scriptivox from the connector and plugin directory.
- **Claude Code:** `/plugin marketplace add SparkleOfficial/scriptivox-plugin`, then `/plugin install scriptivox@scriptivox`.
- **ChatGPT:** add Scriptivox from the plugin directory.

## Support

support@scriptivox.com · https://www.scriptivox.com/docs/mcp
