# IL8 VPS Deploy Bot

A powerful Discord bot for deploying and managing Docker-based VPS instances with multiple Linux OS options.

## Features

- Docker-based VPS deployment
- Ubuntu 22.04
- Ubuntu 24.04
- Debian 11
- Debian 12
- VPS management through Discord
- VPS reinstall support
- Admin VPS creation
- Resource management
- Automatic container management
- Persistent VPS database
- Systemd service support

## Requirements

- Ubuntu/Debian VPS
- Python 3
- Docker
- Root access
- Discord Bot Token
- Discord User ID for admin access

## Installation

### 1. Install Docker

If Docker is not already installed:

```bash
apt update -y
apt install docker.io -y
systemctl enable docker
systemctl start docker
```

Check Docker:

```bash
docker --version
```

### 2. Clone the repository

```bash
git clone https://github.com/nxtinfinite481-png/vps-deploy-bot.git
cd vps-deploy-bot
```

### 3. Create the environment file

```bash
cp il8.env .env
```

Edit the `.env` file:

```bash
nano .env
```

Add your Discord Bot Token and Admin ID:

```env
TOKEN=YOUR_DISCORD_BOT_TOKEN
ADMIN_ID=paste your discord user id
BOT_STATUS_NAME=IL8
WATERMARK=Made by INFINITE
DEFAULT_RAM=2g
DEFAULT_CPU=1
DEFAULT_DISK=10G
VPS_HOSTNAME=infinite-vps
```

Save and exit.

### 4. Install Python pip

```bash
apt install python3-pip -y
```

### 5. Allow system-wide pip installation

```bash
mkdir -p ~/.config/pip && echo -e "[global]\nbreak-system-packages = true" > ~/.config/pip/pip.conf
```

### 6. Install Python dependencies

```bash
pip install -r requirements.txt
```

## Run the Bot with Systemd

Create the systemd service:

```bash
sudo nano /etc/systemd/system/il8.service
```

Add:

```ini
[Unit]
Description=IL8 VPS Discord Bot
After=network.target docker.service

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

Save and exit.

### Start the Bot

```bash
sudo systemctl daemon-reload
sudo systemctl restart il8
```

### Enable the Bot on Boot

```bash
sudo systemctl enable il8
```

### Check Bot Status

```bash
sudo systemctl status il8
```

### View Bot Logs

```bash
journalctl -u il8 -f
```

## Environment Configuration

The `.env` file should contain your bot configuration.

Example:

```env
TOKEN=YOUR_DISCORD_BOT_TOKEN
ADMIN_ID=paste your discord user id
BOT_STATUS_NAME=IL8
WATERMARK=Made by INFINITE
DEFAULT_RAM=2g
DEFAULT_CPU=1
DEFAULT_DISK=10G
VPS_HOSTNAME=infinite-vps
```

Keep your `.env` file private and never upload it to GitHub.

## Default VPS Configuration

| Setting | Value |
| --- | --- |
| Default RAM | 2GB |
| Default CPU | 1 Core |
| Default Disk | 10GB |
| VPS Limit / User | 1 |
| Total VPS Limit | 50 |
| Hostname | infinite-vps |

## Supported Operating Systems

- Ubuntu 22.04
- Ubuntu 24.04
- Debian 11
- Debian 12

## User Commands

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

## Admin Commands

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

## Developer

**INFINITE**

Full-Stack Developer, DevOps Enthusiast and Content Creator focused on server infrastructure, VPS systems, Linux, hosting, automation, Discord bots and Minecraft server technologies.

### Links

- YouTube: https://www.youtube.com/@infinite8labs
- GitHub: https://github.com/nxtinfinite481-png
- Discord: https://discord.gg/pG22dSmAZD

---

Made by INFINITE
