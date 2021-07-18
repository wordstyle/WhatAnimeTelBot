# trace.moe-telegram-bot

[![License](https://img.shields.io/github/license/soruly/trace.moe-telegram-bot.svg?style=flat-square)](https://github.com/wordstyle/WhatAnimeTelBot/blob/master/LICENSE)
[![GitHub Workflow Status](https://img.shields.io/github/workflow/status/soruly/trace.moe-telegram-bot/Node.js%20CI?style=flat-square)](https://github.com/wordstyle/WhatAnimeTelBot/actions)
[![Docker](https://img.shields.io/docker/pulls/soruly/trace.moe-telegram-bot?style=flat-square)](https://hub.docker.com/r/soruly/trace.moe-telegram-bot)
[![Docker Image Size](https://img.shields.io/docker/image-size/soruly/trace.moe-telegram-bot/latest?style=flat-square)](https://hub.docker.com/r/soruly/trace.moe-telegram-bot)
[![Discord](https://img.shields.io/discord/437578425767559188.svg?style=flat-square)](https://discord.gg/K9jn6Kj)

This Telegram Bot can tell the anime when you send an screenshot to it

https://telegram.me/WhatAnimeBot

https://user-images.githubusercontent.com/1979746/125893110-1d3db957-23fb-4944-ae56-b9f45f98c35f.mp4

## Features

- Show anime titles in multiple languages
- Telegram group support
- Image, GIF, Video, URL support (stickers are not supported)
- Video preview

## How to use

1. Start chatting with the bot https://telegram.me/WhatAnimeBot
2. Send anime screenshots (images, gif or video) directly to the bot
3. You may also forward images from other chats to the bot
4. The bot will tell you the anime, episode, and time code of it
5. It will also send you a video preview of that scene

## How to use (in group)

1. Add the bot `@WhatAnimeBot` to your group
2. Reply to any group image, mention the bot with `@WhatAnimeBot`
3. Wait for the bot to reply

_Note that the bot has no access to your messages before it is added to your group_

## How to host the bot on your own

If you have privacy concern, you can host the bot on your own.

Please read [Telegram's official tutorial to create a Bot](https://core.telegram.org/bots) first.

You need to disable [Privacy Mode](https://core.telegram.org/bots#privacy-mode) if you want to use your bot in group chat.

### Host with docker

Docker Image available on [Docker Hub](https://hub.docker.com/repository/docker/soruly/trace.moe-telegram-bot) or [GitHub Container Registry](https://github.com/wordstyle/WhatAnimeTelBot/pkgs/container/trace.moe-telegram-bot)

```
docker run -it --rm --init --name trace-moe-tg-bot \
  -e TELEGRAM_WEBHOOK=https://your.host.com/ \
  -e TELEGRAM_TOKEN=111111111:AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA \
  -p 443:3000 \

```

Note that you need to configure a reverse proxy if you need HTTPS.

### Environment Variables

```
TELEGRAM_TOKEN=       # e.g. 111111111:AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
TELEGRAM_WEBHOOK=     # e.g. https://your.host.com/
PORT=                 # (optional) Default: 3000
TRACE_MOE_KEY=        # (optional)
REDIS_HOST=           # (optional) e.g. 127.0.0.1 or just leave blank to disable rate limit
ANILIST_API_URL=      # (optional) Default: https://graphql.anilist.co/
```

### Use Node.js

Install Node.js 14.x, then:

```
git clone https://github.com/wordstyle/WhatAnimeTelBot.git
cd WhatAnimeTelBot
npm install
```

- Copy `.env.example` to `.env`
- Edit `.env` as you need

```
node server.js
```

### Use Node.js with pm2

You also can use [pm2](https://pm2.keymetrics.io/) to run this in background in cluster mode.

Use below commands to start / restart / stop server.

```
npm run start
npm run stop
npm run reload
npm run restart
npm run delete
```

To change the number of nodejs instances, edit ecosystem.config.json
