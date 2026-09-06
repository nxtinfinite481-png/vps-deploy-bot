# IL8 Discord VPS Bot

Discord VPS management bot branded for INFINITE.

## Setup

1. Install Docker on the host.
2. Create a Python virtual environment.
3. Install dependencies with `pip install -r requirements.txt`.
4. Copy `.env.example` to `.env`.
5. Add your Discord bot token and Discord User ID to `.env`.
6. Run `python bot.py`.

## Supported OS Images

- Ubuntu 22.04 — `ubuntu:22.04`
- Debian 12 — `debian:bookworm`
- Ubuntu 24.04 — `ubuntu:24.04`
- Debian 11 — `debian:11`

## Important

The image URLs currently configured for `/about` are `blob:` URLs from Kommodo. Those are temporary browser-local URLs and generally will not work as Discord embed images when the bot runs on a server. Replace them with publicly accessible HTTPS image URLs before deployment.
