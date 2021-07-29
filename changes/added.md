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

## `~GuildSubscriptionOptions`
Controls the library's auto-subscribing feature

**Options**:  
*auto_subscribe*   : Whether to enable the auto-subscribing.  
                     Defaults to true.  
*concurrent_guilds*: The amount of guilds to subscribe at once. Higher = more ratelimits.  
                     Defaults to 2.  
*max_online*       : The threshold of online members that determins whether to auto-subscribe it.  
                     Defaults to 12,000.

**Class Methods:**
`default()` : Returns a `~GuildSubscriptionOptions` with the default options.
`disabled()`: Returns a `~GuildSubscriptionOptions` with auto-subscribing off.

## `~Client.join_guild()`
Joins a guild.

**Parameters:**  
*invite*: The Discord invite ID, URL (must be a discord.gg URL), or `~Invite`.

**Raises:**  
`~HTTPException`: Joining the guild failed.  
`~InvalidArgument`: Tried to join a guild you're already in.

**Returns:**  
`~Guild`: The guild joined. This is not the same guild that is added to cache.

## `~Client.leave_guild()`
Leaves a guild.

**Parameters:**  
*guild_id*: The ID of the guild you want to leave.

**Raises:**  
`~HTTPException`: Leaving the guild failed.

## `~Client.fetch_applications()`
Retrieves a list of all your applications.

**Raises:**  
`~HTTPException`: Fetching applications failed.

**Returns:**  
`List[~AppInfo]`: All your applications.

## `~Client.fetch_application()`
Retrieves an application.

**Parameters:**  
*app_id*: The ID of the application to retrieve.

**Raises:**  
`~HTTPException`: Fetching the application failed.

**Returns:**  
`~AppInfo`: The application.

## `~Client.fetch_notes()`
Retrieves a list of all your notes.

**Raises:**  
`~HTTPException`: Fetching notes failed.

**Returns:**  
`List[~Note]`: All your notes.

## `~Client.fetch_note()`
Retrieves a note.

**Parameters:**  
*user_id*: The ID of the user to retrieve the note from.

**Raises:**  
`~HTTPException`: Fetching the note failed.

**Returns:**  
`~Note`: The note.
