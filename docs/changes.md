# Fork changes
This fork of `discord.py` aims to be as close to the original as possible. However, this isn't always feasible. 
Below are the changes.

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

{% include navigation.html %}

<script src="http://code.jquery.com/jquery-1.4.2.min.js"></script> <script> var x = document.getElementsByClassName("site-footer-credits"); setTimeout(() => { x[0].remove(); }, 10); </script>
