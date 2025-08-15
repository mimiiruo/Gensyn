# 🚀 Gensyn Node Setup Guide

## 📋 Overview

Gensyn Protocol is a layer-1 trustless protocol for deep learning computation that rewards compute providers instantly via smart contracts — without administrative oversight. The key innovation is verifying ML work without infinite replication using a method that's 1,350% more efficient than traditional replication.

---

## ⚙️ Installation Steps

### Step 1: Optimize VPS

```bash
wget https://raw.githubusercontent.com/ezlabsnodes/autoinstall/main/optimize.sh && chmod +x optimize.sh && sudo ./optimize.sh
```

### Step 2: Create Swap Memory

```bash
wget https://raw.githubusercontent.com/ezlabsnodes/autoinstall/main/create-swap.sh && chmod +x create-swap.sh && sudo ./create-swap.sh
```

### Step 3: Install Dependencies

```bash
wget https://raw.githubusercontent.com/ezlabsnodes/autoinstall/main/depedency-nodejs.sh && chmod +x depedency-nodejs.sh && ./depedency-nodejs.sh
```

### Step 4: Download & Extract Repository

```bash
rm -rf rl-swarm.zip && sudo apt-get install -y unzip && wget https://github.com/ezlabsnodes/gensyn/raw/refs/heads/main/rl-swarm.zip && unzip rl-swarm.zip && cd rl-swarm
```

### Step 5: Create Screen Session

```bash
screen -S gensyn
```

### Step 6: Execute the RL Swarm

```bash
python3 -m venv .venv
source .venv/bin/activate
chmod +x run_rl_swarm.sh
./run_rl_swarm.sh
```

### Step 7: Login Configuration

#### Authentication Steps:
1. **Login**: Use your Google credentials when prompted
2. **Password**: Use your server's IP address
3. **Return to VPS** to complete the setup

#### Configuration Prompts:

**Prompt 1**: Would you like to push models you train in the RL swarm to the Hugging Face Hub? [y/N]
- **Answer**: `n`

**Prompt 2**: Enter the name of the model you want to use in huggingface repo/name format, or press [Enter] to use the default model.
- **Answer**: Press `Enter` (use default)

#### Screen Management:
- **Detach from screen**: `Ctrl + A + D`

### Step 8: Setup Monitoring Cronjob

```bash
cd && sudo apt install cron && rm -rf setup_monitoring.sh && wget https://raw.githubusercontent.com/ezlabsnodes/gensyn/main/setup_monitoring.sh && chmod +x setup_monitoring.sh && sudo ./setup_monitoring.sh
```

**Function**: Automatically restarts your Gensyn node if it crashes and the screen session closes.

### Step 9: Backup Configuration Files

```bash
wget https://raw.githubusercontent.com/ezlabsnodes/gensyn/main/backup-gensyn.sh && chmod +x backup-gensyn.sh && ./backup-gensyn.sh
```

**Purpose**: This copies three essential files (`swarm.pem`, `userApiKey.json` & `userData.json`) to the `/root/ezlabs/` directory for backup.

---

## ✅ Installation Complete!

Your Gensyn node is now set up and running. The monitoring system will automatically restart your node if any issues occur.

---

## 🔧 Useful Commands

| Command | Description |
|---------|-------------|
| `screen -ls` | Check screen sessions |
| `screen -r gensyn` | Reattach to Gensyn screen |
| `ls /root/ezlabs/` | Check backup files |

---

## 📁 Important Files

The following files are automatically backed up to `/root/ezlabs/`:

- `swarm.pem` - Authentication certificate
- `userApiKey.json` - API key configuration
- `userData.json` - User data configuration

---

## 🆘 Troubleshooting

### Common Issues:

1. **Screen session not found**: 
   - Check with `screen -ls`
   - Create new session: `screen -S gensyn`

2. **Node stopped running**:
   - The monitoring cronjob should auto-restart
   - Manually restart: `screen -r gensyn` and re-run step 6

3. **Backup files missing**:
   - Re-run step 9 to recreate backups
   - Verify with `ls /root/ezlabs/`

---

*Guide created by FasoNodez*
