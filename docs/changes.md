---
layout: default
title: Changes
parent: Documentation
nav_order: 1
---

# Fork changes
This fork of `discord.py` aims to be as feature-complete to the original as possible. However, this isn't always feasible. 
Below are the things added, removed, and changed.

**Note:** Internal changes that don't affect functionality are not listed. 

--------

## Removed
- `Intents`: Breaks self-bots and alerts Discord.
- `discord.abc.Messageable.fetch_message()`: Bot only.
- `discord.TextChannel.delete_messages()`: Bot only.
- `discord.Client.fetch_user()`: Bot only.

## Changed
- Undeprecated self-bot only methods.
- Updated docstrings to remove mentions of bot/self-bot differences, bot limitations, and self-bot deprecation notices.
- `User-agent`: Changed to a generic Windows user-agent to avoid detection.
- `discord.TextChannel.purge()`: Removed ability to use `delete_messages()`, removed `bulk` parameter as it was made useless. Edited docstring to reflect changes.
- `discord.Client.login()`: Removed `bot` kwarg.
- `discord.Client.run()`: Removed `bot` kwarg.
- `discord.Client.start()`: Removed `bot` kwarg.
