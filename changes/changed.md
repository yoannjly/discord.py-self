---
layout: default
title: Changed
parent: Changes
nav_order: 3
---

# Changed
While a lot of things are identical with the bot and user APIs, there are some subtle differences.  
Some things work the "bot" way, but the official client does them differently. These create easy ways for Discord to detect account automation (these are mostly internal so users generally shouldn't care).  
Below are all the changes in existing items.

**Note:** Internal changes that don't affect functionality are not listed.

--------

## Misc.
<!--- Removed `reason` parameter from everything except `kick()` and `ban()` as the X-Audit-Log-Reason header doesn't appear to work.-->
- Removed `@utils.deprecated` decorator from all existing user-only methods.
- Updated docstrings to remove deprecation notices.
- Updated docstrings to remove mentions of bot/self-bot differences and bot limitations.
- Removed all mentions of shards from logs and errors.

## `__main__()`
- Removed *--sharded* option as sharding was removed.

## `~abc.GuildChannel`
- Removed *reason* parameter from `delete()`, `set_permissions()`, `clone()`, and `create_invite()` as it doesn't work.
- Added *validate* and *target_type* to `create_invite()`. Their purposes are currently unknown.

## `~Channel`
- Removed *reason* parameter from `edit()`, `clone()`, `create_webhook()`, and `follow()` as it doesn't work.
- Removed *bulk* from `purge()` as bots can't use the bulk delete endpoint.

## `~VoiceChannel`
- Removed *reason* parameter from `clone()` and `edit()` as it doesn't work.

## `~StageChannel`
- Removed *reason* parameter from `clone()` and `edit()` as it doesn't work.

## `~CategoryChannel`
- Removed *reason* parameter from `clone()`, `edit()`, `create_text_channel()`, `create_voice_channel()`, and `create_stage_channel()` as it doesn't work.

## `~StoreChannel`
- Removed *reason* parameter from `clone()` and `edit()` as it doesn't work.

## `~Client`
- Removed the *shard_id*, *shard_count*, *intents*, and *guild_subscriptions* parameters from `__init__()` as they aren't used.
- Added a *guild_subscription_options* parameter to `__init__()`. It takes a `~GuildSubscriptionOptions`.
- Removed the *shard_id* parameter from `before_identify_hook()` and changed the default implementation to do nothing.
- Removed the *bot* parameter from `login()`, `start()`, and `run()`.
- Added a *logout* parameter to `close()`. This adds a POST to `/auth/logout` at the end of the process.
- Removed all parameters from `fetch_guilds()` as they're useless.
- Removed the region parameter from `create_guild()` as it isn't used anymore.
- Added a *with_expiration* parameter to `fetch_invite()`. This fills in the `~Invite.expires_at` attribute.
- Removed `on_member_remove()` and `on_member_join()` as they can't be reliably used most of the time. May revisit in the future.
- Added *with_mutuals* and *fetch_note* parameters. The former adds *mutual_guilds* and *mutual_friends* parameters to the `~Profile` object, and the latter pre-fetches `~Profile.note`.

## `~Emoji`
- Removed the *reason* parameter from `delete()` as it doesn't work.
- Removed the *reason* and *roles* parameter from `edit()` as they don't work.

## `~Guild`
- Removed the *reason* parameter from `create_text_channel()`, `create_voice_channel()`, `create_stage_channel()`, `create_category()`, `edit()`, `prune_members()`, `create_role()`, `edit_role_positions()`, `unban()` as it doesn't work.
- Added a *with_applications* parameter to `integrations()`. It determines if the returned list includes applications.
- Removed the *reason* and *roles* parameter from `create_custom_emoji()` as they don't work.
- Added the requirement for the manage guild permission to `chunk()`.
- Added a *preferred_region* parameter to `change_voice_state()`. It is recommended to leave this as default.

## `~Invite`
- Added an *expires_at* attribute. This is a `datetime.datetime` available through `~Client.fetch_invite()` and only when *with_expiration* is set to `True`.
- Removed the *reason* parameter from `delete()` as it doesn't work.

## `~Member`
- Added a *guild_avatar* attribute. This is the member's guild avatar, if applicable.
- Removed the *reason* parameter from `unban()`, `edit()`, `move_to()`, `add_roles()`, and `remove_roles()` as it doesn't work.

## `~Message`
- Removed the *reason* parameter from `pin()` and `unpin()`as it doesn't work.

## `~Relationship`
- Added a *nickname* attribute. This is the friend's nickname.

## `~Role`
- Removed the *reason* parameter from `edit()` and `delete()`as it doesn't work.

## `~Profile`
- Added *banner*, *bio*, and *note* attributes. The *note* attribute is a `~Note`.
- Renamed `hypesquad_houses` to `hypesquad_house` and changed it to return a `~HypeSquadHouse`.

## `~ClientUser`
- Added *banner*, *bio*, *phone*, *settings*, and *note* attributes. The *note* attribute is a `~Note` (**not pre-fetched**). The *settings* attribute is a `~Settings`.
- Added *discriminator*, *banner*, *accent_colour*, and *bio* parameters to `edit()`.
- Added a bunch of new parameters to `edit_settings()`, and made it return a `~Settings`.
