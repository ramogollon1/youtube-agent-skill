---
name: yt-package
description: >-
  Write and lint the title and thumbnail for a YouTube video as one pairing,
  checking truncation, duplication and vagueness before publish. Use for
  "title ideas", "what should I call this", "thumbnail text", "my CTR is
  bad", packaging, or any request to rename or repackage an existing video.
---

# yt-package

The title and the thumbnail are ONE unit. Writing them separately is why most packaging fails: the
thumbnail repeats the title, and half the click surface says the same thing twice.

```bash
python3 title.py --title "..." --thumb "AI RAN IT"
python3 title.py titles.txt            # one per line, ranked
```

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

## Rules the tool enforces, and why

- **60 characters** is where desktop search truncates, **40** is a mobile home feed. Both are
  reported because they fail differently: a desktop cut loses the tail, a mobile cut can lose the
  subject.
- **The thumbnail must not repeat the title.** Different words, same promise.
- **Three words maximum on the thumbnail.** At feed size a fourth word is a grey smear.
- **A number, a name or a date** beats every adjective available to you.
- **Two all-caps words is the ceiling** before a title reads as spam.

## Write ten, keep two

Generate ten titles, run them all through `title.py`, show the user the top three with their scores
and the specific issue on each. For the winner, write the thumbnail brief: the expression, the
framing, the three words, and what the background has to do to hold contrast at feed size.

## The gate

Nothing here publishes. This skill writes and you publish. Every output ends in a block the user
copies, and the last line of every run is the question: **ship it, or change it?**
