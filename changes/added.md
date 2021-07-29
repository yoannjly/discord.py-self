---
layout: default
title: Added
parent: Changes
nav_order: 1
---

# Added
In the peacefull lands of a few years ago, the user and bot APIs were virtually identical. However, over the years, they've diverged more and more (especially lately).
Below are all the shiny new things.

**Note:** Internal changes that don't affect functionality are not listed.

--------

## `~Client.join_guild()`
Joins a guild using an invite.

**Parameters:**
*invite*: The Discord invite ID, URL (must be a discord.gg URL), or `~Invite`.

**Raises:**
`~HTTPException`: Joining the guild failed.
`~InvalidArgument`: Tried to join a guild you're already in.

**Returns:**
`~Guild`: The guild joined. This is not the same guild that is added to cache.
