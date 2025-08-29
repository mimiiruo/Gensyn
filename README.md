# Gensyn Node Setup Guide

## Overview
Gensyn is a layer-1 trustless protocol for deep learning computation that rewards compute providers via smart contracts. This guide walks you through setting up a Gensyn node.

## Prerequisites
- Linux VPS with sufficient resources
- Minimum 100GB available storage for swap
- Root or sudo access

## Quick Setup

### 1. Create Swap Space
```bash
wget https://raw.githubusercontent.com/ezlabsnodes/autoinstall/main/optimize2.sh && chmod +x optimize2.sh && sudo ./optimize2.sh
```
- Press ENTER for 6x swap size or choose manually (min 100GB recommended)

### 2. Install Dependencies
```bash
rm -rf depedency-nodejs.sh && wget https://raw.githubusercontent.com/ezlabsnodes/autoinstall/main/depedency-nodejs.sh && chmod +x depedency-nodejs.sh && sudo ./depedency-nodejs.sh
```

### 3. Reboot System
```bash
sudo reboot
```

### 4. Setup Node
```bash
cd && rm -rf rl-swarm.zip && wget https://raw.githubusercontent.com/ezlabsnodes/gensyn/main/rl-swarm.zip && unzip rl-swarm.zip && cd rl-swarm
```

### 5. Start in Screen Session
```bash
screen -S gensyn
python3 -m venv .venv
source .venv/bin/activate
chmod +x run_rl_swarm.sh
./run_rl_swarm.sh
```

### 6. Login & Detach
1. Login with Google credentials when prompted
2. Press `Ctrl + A + D` to detach screen

## Management

**Check node status:**
```bash
screen -r gensyn
```

**Stop node:**
```bash
# Attach to screen first, then:
Ctrl + C
```

**Restart after reboot:**
```bash
cd ~/rl-swarm && screen -S gensyn
source .venv/bin/activate
./run_rl_swarm.sh
```

## Optional: Systemd Service

Convert to system service for auto-restart:
```bash
wget -O systemd.sh https://raw.githubusercontent.com/ezlabsnodes/gensyn/main/systemd.sh && chmod +x systemd.sh && ./systemd.sh
```

Check service logs:
```bash
journalctl -u gensyn -f
```

## Troubleshooting

- **Insufficient space**: Ensure adequate disk space for swap creation
- **Installation fails**: Check internet connectivity and permissions
- **Node won't start**: Verify all dependencies installed correctly
- **Screen session lost**: Use `screen -list` to find sessions

## Security Notes

⚠️ **Always verify scripts before execution**
- Review script contents from trusted sources
- Use official repositories when possible
- Monitor system resources after installation

---
*Based on community guides - verify all commands before execution*
