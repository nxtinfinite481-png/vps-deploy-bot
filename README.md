# IL8 VPS Bot

IL8 is a Discord VPS management bot by INFINITE.

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/nxtinfinite481-png/vps-deploy-bot.git
cd vps-deploy-bot
```

### 2. Create the environment file

```bash
cp il8.env .env
nano .env
```

Add your Discord bot token and admin user ID:

```env
TOKEN=your_discord_bot_token
ADMIN_ID=paste your discord user id
BOT_STATUS_NAME=IL8
WATERMARK=Made by INFINITE
DEFAULT_RAM=2g
DEFAULT_CPU=1
DEFAULT_DISK=10G
VPS_HOSTNAME=infinite-vps
```

Save and exit.

### 3. Install Python and dependencies

```bash
apt update -y
apt install python3-pip -y
mkdir -p ~/.config/pip && echo -e "[global]\nbreak-system-packages = true" > ~/.config/pip/pip.conf
pip install -r requirements.txt
```

### 4. Start the bot

```bash
python3 bot.py
```

## Systemd

Create the service:

```bash
sudo nano /etc/systemd/system/il8.service
```

Paste:

```ini
[Unit]
Description=IL8 VPS Discord Bot
After=network.target

[Service]
User=root
WorkingDirectory=/root/vps-deploy-bot
ExecStart=/usr/bin/python3 /root/vps-deploy-bot/bot.py
Restart=always
RestartSec=5
Environment=PYTHONUNBUFFERED=1

[Install]
WantedBy=multi-user.target
```

Then run:

```bash
sudo systemctl daemon-reload
sudo systemctl enable il8
sudo systemctl restart il8
```

Check status:

```bash
sudo systemctl status il8
```

View logs:

```bash
journalctl -u il8 -f
```

## Requirements

- Python 3
- Docker
- Discord Bot Token
- Linux VPS/server
- Discord bot with the required application commands enabled

## Supported Operating Systems

- Ubuntu 22.04
- Debian 12
- Ubuntu 24.04
- Debian 11

## Commands

### User Commands

```text
/create <os>
/list
/vps-info [vps_id]
/ssh [vps_id]
/start <vps_id>
/stop <vps_id>
/restart <vps_id>
/reinstall <vps_id> [os]
/delete <vps_id>
/about
/logs <vps_id> [lines]
/ping
/help
```

### Admin Commands

```text
/admin-create
/admin-list
/admin-users
/admin-vps-info
/admin-del-user
/admin-stop-all
/admin-manage
/admin-stats
/admin-logs
/admin-ban
/admin-unban
```

## Configuration

The bot uses:

```text
.env
bot.db
bot.log
```

The database and log files are created/used by the bot during operation.

## Developer

**IL8**  
**Version:** v1.0  
**Developer:** INFINITE

YouTube: https://www.youtube.com/@infinite8labs  
GitHub: https://github.com/nxtinfinite481-png  
Discord: https://discord.gg/pG22dSmAZD

Made by INFINITE
