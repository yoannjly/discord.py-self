---
layout: about
name: About
nav_order: 2
---

# About
What is this project all about, anyway?

I'm aiming to provide a 1:1 alternative to **discord.py** for self-bots. Obviously this isn't possible, but I'm trying to be as close as I can.

## When
This project began when Discord made an internal change on April 31st, 2021 that stopped self-bots from receiving `message.content` and `message.embeds` if they sent Intents when logging on to the gateway. This affected many libraries, such as **discord.py**.

## Why
**discord.py** wouldn't fix the issue, as they deprecated self-bot support in the latest version, and support was completely removed in the next version.

I forked the project and started experimenting with things; after trying a few things, I found out the issue was the Intent sending and removed the code. I thought that was it, but it definitely wasn't. The APIs for bots and users have been diverging rapidly, and there are tons of issues in **discord.py** regarding self-bots. 

One thing lead to another, and now I'm stuck maintaining a library dedicated to self-bots 😭.

## What
What's next?

What I'm going to do next is keep fixing and maintaining the library.

I'm also going to add more undocumented Discord APIs and Discord features available only to users. 
