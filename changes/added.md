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

## `~GuildFolder`
Represents a guild folder.

**Note**:  
Discord puts all guilds not in folders in their own invisible folders, because Discord.

**Attributes**:  
*id* `int`: The folder ID.  
*name* `str`: The folder name.  
*color/colour* `~Colour`: The folder colour.  
*guilds* `List[~Guild]`: The guilds inside the folder.

## `~GuildSubscriptionOptions`
Controls the library's auto-subscribing feature

You construct a class by either passing attributes to `__init__()` or utilizing a class method.

**Attributes**:  
*auto_subscribe* `bool`: Whether to enable the auto-subscribing.  
Defaults to True.  
*concurrent_guilds* `int`: The amount of guilds to subscribe at once. Higher = more ratelimits.  
Defaults to 2.  
*max_online* `int`: The threshold of online members that determines whether to auto-subscribe it. Higher = slower startup.  
Defaults to 12,000.

**Class Methods:**  
`default()`: Returns a `~GuildSubscriptionOptions` with the default options.  
`disabled()`: Returns a `~GuildSubscriptionOptions` with auto-subscribing off.

## `~Note`
Represents a note on a user.

**Attributes:**  
*note* `str`: The actual note (this raises a `~ClientException` if the note isn't fetched).  
*user* `~User`: The `~User` attached to the note (will be an `~Object` if the user is not in the cache).

### `fetch()`
Fetches the note (and fills the note attribute).

**Raises:**  
`~HTTPException`: Fetching the note failed.

**Returns:**  
`str`: The note.

### `edit()`
Edits the note.

**Raises:**  
`~HTTPException`: Changing the note failed.

**Parameters:**  
*note* `str`: The new note.

### `delete()`
Deletes the note.

**Raises:**  
`~HTTPException`: Deleting the note failed.

## `~Settings`
Represents the user's settings.

Has way too many attributes to list here. Look at the docstring if you're interested.

## `~Client.join_guild()`
Joins a guild.

**Parameters:**  
*invite* `Union[~Invite, str]`: The Discord invite ID, URL (must be a discord.gg URL), or `~Invite`.

**Raises:**  
`~HTTPException`: Joining the guild failed.  
`~InvalidArgument`: Tried to join a guild you're already in.

**Returns:**  
`~Guild`: The guild joined. This is not the same guild that is added to cache.

## `~Client.leave_guild()`
Leaves a guild.

**Parameters:**  
*guild_id* `int`: The ID of the guild you want to leave.

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
*app_id* `int`: The ID of the application to retrieve.

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
*user_id* `int`: The ID of the user to retrieve the note from.

**Raises:**  
`~HTTPException`: Fetching the note failed.

**Returns:**  
`~Note`: The note.

## `~Guild.mute()`
Mutes the guild.

**Parameters:**  
*duration* `int`: The duration (in hours) of the mute. Defaults to None for an indefinite mute.

**Raises:**  
`~HTTPException`: Muting failed.

## `~Guild.unmute()`
Unmutes the guild.

**Raises:**  
`~HTTPException`: Unmuting failed.

## `~Member/guild_avatar_url`
Same as `avatar_url` but for guild avatars.
Returns the avatar url if the member doesn't have a guild avatar.

## `~Member/is_guild_avatar_animated()`
Same as `is_avatar_animated()` but for guild avatars.

## `~Member/guild_avatar_url_as()`
Same as `avatar_url_as()` but for guild avatars.
Returns the avatar url if the member doesn't have a guild avatar.

## `~Profile/ClientUser.banner_url`
Same as `avatar_url` but for banners.

## `~Profile/ClientUser.is_banner_animated()`
Same as `is_avatar_animated()` but for banners.

## `~Profile/ClientUser.banner_url_as()`
Same as `is_avatar_animated()` but for banners.

## `~Profile/ClientUser.accent_colour`
Returns a `~Colour` of the user's accent (banner) colour.

## `~ClientUser.disable()`
Disables the currently logged-in account.  
This will disconnect you.

**Parameters:**  
*password* `str`: The current password.

**Raises:**  
`~HTTPException`: Disabling the account failed.

## `~ClientUser.delete()`
Deletes the currently logged-in account.  
This will disconnect you.

**Parameters:**  
*password* `str`: The current password.

**Raises:**  
`~HTTPException`: Deleting the account failed.

## `~User.mutual_guilds()`
Returns all mutual guilds with this user.

**Note:**  
This is just a shortcut to `~User.profile.mutual_guilds()`

## `~Guild.subscribe()`
Abuses the member sidebar to scrape all members*.

*Discord doesn't provide offline members for "large" guilds.  
*If a guild doesn't have a channel (of any type) @everyone can view,  
the subscribing currently fails. In the future, it'll pick the next  
most-used role and look for a channel that role can view.  

You can only request members from the sidebar in 100 member ranges, and  
you can only specify up to 2 ranges per request.  

This is a websocket operation and can be extremely slow.

**Parameters:**  
*delay* `Union[int, float]`: Amount of time (in seconds) to wait before requesting the next 2 ranges.  
Note: By default, we wait for the GUILD_MEMBER_LIST_UPDATE to arrive before  
continuing. However, those arrive extremely fast so we need to add an extra  
delay to try to avoid rate-limits.

**Returns:**
`bool`: Whether the subscribing was successful.

## `~Guild.online_count`
Like `~Guild.member_count` but for online members.  
Only populated after a GUILD_MEMBER_LIST_UPDATE has been received (always happens if auto-subscribing is enabled).

## `~Guild.subscribed`
Like `~Guild.chunked` but for subscription status. See [this](#guildsubscribe).

## `~Invite.use()`
Uses the invite and joins the guild.  
Has an alias of `~Invite.accept()`.

**Raises:**  
`~HTTPException`: Using the invite failed.
`~InvalidArgument`: Tried to join a guild you're already in.

## `~Message.invites()`
Retreives all valid invites in a message.

**Raises:**  
`~HTTPException`: Fetching the invites failed.

**Returns:**
`List[~Invite]`: All valid invites contained in the message.

## `~Relationship.change_nickname()`
Changes a relationship's nickname. Only applicable for friends.

**Parameters:**
*nick* `str`: The new nickname.

**Raises:**  
`~HTTPException`: Changing the nickname failed.
