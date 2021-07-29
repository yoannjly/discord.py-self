---
layout: default
title: Removed
parent: Changes
nav_order: 2
---

# Removed
This fork of `discord.py` aims to be as backwards-compatible to the original as possible. However, some things are *simply* bot only.  
Below are the public methods that were removed.

**Note:** Internal changes that don't affect functionality are not listed.

--------

## `~AutoShardedClient` & `~ShardInfo`
Users cannot (and don't need to) use sharding.  
Additionally, all mentions of shards were removed from logs and errors.

## `~Intents` & `~PrivilegedIntentsRequired`
In the past, intents worked when used with users; they even altered the gateway's functionality to more mimic the bot gateway.  
Now, they still do "function", however you no longer receive message content and embeds for users other than yourself.

They also have the added disadvantage of alerting discord to the fact that you're automating your account.

## `~Client.request_offline_members()`
This completely bypasses the check for `Permissions.manage_guild` in `~Guild.chunk()`.  
It's also already deprecated so not too much of a problem functionality-wise.

## `~Client.application_info()`
This was used to return the current application's information.  
Users are not attached to applications.

## `~Client.intents`
Intents were removed for reasons explained above, so this property is now useless.

## `~Guild.self_role()`
Same situation as `~Client.application_info()`. Users don't have a role attached to themselves.

## `~Guild.fetch_members()`
Uses a bot-only endpoint and unfortunately has no user alternative.

To make matters worse, attempting to use this endpoint phone-locks your account (most bot-only endpoints don't do this).

## `~Guild.shard_id`
Another remnant of shards (see [this](#autoshardedclient--shardinfo))

## `~TextChannel.delete_messages()`
Another bot-only endpoint.

In this case, there is an alternative (deleting messages one=by-one).  
However, this is already implemented in `~TextChannel.purge()`.  
The only point of this method was to wrap the bot-only endpoint.

## `~User.mutual_guilds`
Introduces inconsitency and isn't as accurate as `~Profile.mutual_guilds`.

## `~Utils.oauth_url()`
Users cannot be added to guilds with an OAuth2 URL.
