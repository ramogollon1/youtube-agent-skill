---
name: yt-seo
description: >-
  Write the description, tags and search-facing text for a YouTube video,
  aimed at the query a real person types. Use for "write my description",
  "tags", "SEO", "help this video get found", "nobody is finding this".
---

# yt-seo

Search is a smaller lever than packaging and a bigger one than people think for evergreen videos.
For a video aimed at the subscriber feed, say so and spend the effort on `/yt-package` instead.

## Before you write

1. Load the voice profile for the channel this is for. Voices live in `~/.claude/youtube/channels/`,
   one file per channel, named `youtube-<channel>.md` (e.g. `youtube-pibubear.md`).
   - If the user names a channel ("script for mogoplay"), read `youtube-<channel>.md`.
   - If they do not and there is only one file there, use it.
   - If there are several and they do not name one, ask which channel before writing anything.
   - If the folder does not exist, fall back to `~/.claude/youtube/voice.md`.
   - No local filesystem (claude.ai)? Use the `youtube-<channel>.md` in the project knowledge or
     attached to the chat. With several and none named, ask which channel.
   Say which channel's voice you loaded in one line. That file is the voice profile: how they talk
   on camera, the words they never use, who they are talking to, what they will not claim. If no
   profile exists for the channel, ask for **three of their own videos**, read or transcribe them,
   infer the voice, and write `~/.claude/youtube/channels/youtube-<channel>.md`. A script in the
   wrong voice is worse than no script, because they have to read it out loud.
2. Never invent a number, a result or a source. If a figure would strengthen it and you do not have
   one, ask for it or write the line without it.

## The description

- **The first two lines are the only ones anyone reads.** They show above "...more" and they are
  the search snippet. Say what the video gives them, in the words they would have typed.
- Then the link or the resource, if there is one, so it is above the fold.
- Then chapters (`/yt-chapters` writes them).
- Then the long version: what is covered, who it is for, what it assumes.

## Tags, honestly

Tags are a weak signal and YouTube has said so. Use them for disambiguation - spellings, the tool
names, the abbreviations people actually type - and stop. Fifteen is plenty. A wall of tags is not
a strategy and stuffing unrelated ones is against the terms.

## The query test

Before handing anything over, write the three search queries this video should win, and check the
title and first two description lines contain the words in those queries. If they do not, the
problem is the title, not the description.

## The gate

Nothing here publishes. This skill writes and you publish. Every output ends in a block the user
copies, and the last line of every run is the question: **ship it, or change it?**
