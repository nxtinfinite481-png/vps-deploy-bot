# IL8 VPS Deploy Bot

A powerful Discord bot for deploying and managing Docker-based VPS instances with multiple Linux OS options.

## Features

* Docker-based VPS deployment
* Ubuntu 22.04
* Ubuntu 24.04
* Debian 11
* Debian 12
* VPS management through Discord
* VPS reinstall support
* Admin VPS creation
* Resource management
* Automatic container management
* Persistent VPS database
* Systemd service support

## Requirements

* Ubuntu/Debian VPS
* Python 3
* Docker
* Root access
* Discord Bot Token
* Discord User ID for admin access

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/nxtinfinite481-png/vps-deploy-bot
cd vps-deploy-bot
```

### 2. Create the environment file

```bash
cp il8.env .env
```

Edit the `.env` file and add your Discord Bot Token and Admin ID:

```bash
nano .env
```

### 3. Install Python pip

```bash
apt install python3-pip -y
```

### 4. Allow system-wide pip installation

```bash
mkdir -p ~/.config/pip && echo -e "[global]\nbreak-system-packages = true" > ~/.config/pip/pip.conf
```

### 5. Install Python dependencies

```bash
pip install -r requirements.txt
```

## Run the Bot with Systemd

Create the systemd service:

```bash
sudo nano /etc/systemd/system/bot.service
```

Add:

```ini
[Unit]
Description=Vps Discord Bot
After=network.target

[Service]
User=root
WorkingDirectory=/root
ExecStart=/usr/bin/python3 /root/bot.py
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
sudo systemctl restart bot
```

### Enable the Bot on Boot

```bash
sudo systemctl enable bot
```

### Check Bot Status

```bash
sudo systemctl status bot
```

### View Bot Logs

```bash
journalctl -u bot -f
```

## Environment Configuration

The `.env` file should contain your bot configuration.

Example:

```env
TOKEN=YOUR_DISCORD_BOT_TOKEN
ADMIN_ID=paste your discord user id
BOT_STATUS_NAME=IL8
WATERMARK=Made by INFINITE
```

Keep your `.env` file private and never upload it to GitHub.

## Default VPS Configuration

| Setting          | Value        |
| ---------------- | ------------ |
| Default RAM      | 2GB          |
| Default CPU      | 1 Core       |
| Default Disk     | 10GB         |
| VPS Limit / User | 1            |
| Total VPS Limit  | 50           |
| Hostname         | infinite-vps |

## Supported Operating Systems

* Ubuntu 22.04
* Ubuntu 24.04
* Debian 11
* Debian 12

## Developer

**INFINITE**

Full-Stack Developer, DevOps Enthusiast and Content Creator focused on developer tools, server infrastructure, VPS systems, automation and Discord bots.

### Links

* YouTube: https://www.youtube.com/@infinite8labs
* GitHub: https://github.com/nxtinfinite481-png
* Discord: https://discord.gg/pG22dSmAZD

---

Made by INFINITE
