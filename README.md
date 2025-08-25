# Gensyn Node Setup Guide

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub issues](https://img.shields.io/github/issues/username/gensyn-node-setup)](https://github.com/username/gensyn-node-setup/issues)
[![GitHub stars](https://img.shields.io/github/stars/username/gensyn-node-setup)](https://github.com/username/gensyn-node-setup/stargazers)

A comprehensive setup guide for running a Gensyn Protocol node with automated installation scripts.

## 📋 Table of Contents

- [About Gensyn Protocol](#about-gensyn-protocol)
- [System Requirements](#system-requirements)
- [Quick Start](#quick-start)
- [Installation Steps](#installation-steps)
- [Configuration](#configuration)
- [Management](#management)
- [Systemd Service](#systemd-service)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

## 🌟 About Gensyn Protocol

Gensyn is a layer-1 trustless protocol for deep learning computation that rewards compute providers instantly via smart contracts without administrative oversight. The protocol solves the key challenge of verifying ML work without infinite replication using a method that is 1,350% more efficient than traditional replication, preventing unnecessary verification chains.

## 💻 System Requirements

- **VPS**: Sufficient computational resources
- **Storage**: Minimum 100GB swap space recommended
- **OS**: Linux-based operating system (Ubuntu 20.04+ recommended)
- **Network**: Stable internet connection
- **Memory**: 8GB+ RAM recommended


## 📦 Installation Steps

### Step 1: Create Swap Space

```bash
wget https://raw.githubusercontent.com/ezlabsnodes/autoinstall/main/optimize2.sh && chmod +x optimize2.sh && sudo ./optimize2.sh
```

**Options:**
- Press `ENTER` for 6x swap size
- Or choose swap size manually (minimum 100GB swap recommended)

### Step 2: Install Dependencies

```bash
rm -rf depedency-nodejs.sh && wget https://raw.githubusercontent.com/ezlabsnodes/autoinstall/main/depedency-nodejs.sh && chmod +x depedency-nodejs.sh && sudo ./depedency-nodejs.sh
```

### Step 3: Reboot System

```bash
sudo reboot
```

### Step 4: Download & Extract Repository

```bash
cd && rm -rf rl-swarm.zip && wget https://raw.githubusercontent.com/ezlabsnodes/gensyn/main/rl-swarm.zip && unzip rl-swarm.zip && cd rl-swarm
```

### Step 5: Create Screen Session

```bash
screen -S gensyn
```

### Step 6: Execute RL Swarm

```bash
python3 -m venv .venv
source .venv/bin/activate
chmod +x run_rl_swarm.sh
./run_rl_swarm.sh
```

### Step 7: Configuration

1. **Login**: Log in using your Google credentials when prompted
2. **Detach Screen**: Press `Ctrl + A + D` to detach the screen session

## ✅ Installation Complete!

Your Gensyn node should now be running successfully.

## 🔧 Configuration

The node will prompt you for configuration during the initial setup:

- Google account authentication
- Network configuration (automatic)
- Compute resource allocation

## 📊 Management

### Screen Session Management

```bash
# Check screen session
screen -r gensyn

# List all screen sessions
screen -ls

# Stop the node
# Attach to screen and use Ctrl + C
```

### Manual Restart

If you need to restart the node manually:

```bash
cd ~/rl-swarm
screen -S gensyn
source .venv/bin/activate
./run_rl_swarm.sh
```

## 🔄 Systemd Service

For production environments, you can migrate to a systemd service:

```bash
wget -O systemd.sh https://raw.githubusercontent.com/ezlabsnodes/gensyn/main/systemd.sh && chmod +x systemd.sh && ./systemd.sh
```

### Service Management

```bash
# Start service
sudo systemctl start gensyn

# Stop service
sudo systemctl stop gensyn

# Check status
sudo systemctl status gensyn

# View logs
journalctl -u gensyn -f

# Enable auto-start on boot
sudo systemctl enable gensyn
```

## 🛠️ Troubleshooting

### Common Issues

1. **Insufficient Disk Space**
   ```bash
   df -h  # Check available space
   ```

2. **Installation Failures**
   - Check internet connectivity
   - Verify system requirements
   - Check firewall settings

3. **Screen Session Issues**
   ```bash
   # If screen session is lost
   screen -ls
   screen -r gensyn
   ```

4. **Systemd Service Issues**
   ```bash
   # Check service logs
   journalctl -u gensyn -f --no-pager
   
   # Restart service
   sudo systemctl restart gensyn
   ```

### Performance Optimization

- Ensure adequate swap space (minimum 100GB)
- Monitor system resources regularly
- Keep the system updated

## 📝 Logs

Application logs are stored in:
- Screen session: Use `screen -r gensyn` to view real-time logs
- Systemd service: Use `journalctl -u gensyn -f` for service logs

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Setup

```bash
git clone https://github.com/username/gensyn-node-setup.git
cd gensyn-node-setup
# Make your changes and test thoroughly
```

## 🐛 Issues

If you encounter any issues, please:

1. Check the [Troubleshooting](#troubleshooting) section
2. Search existing [GitHub Issues](https://github.com/username/gensyn-node-setup/issues)
3. Create a new issue with detailed information:
   - Operating system and version
   - Error messages
   - Steps to reproduce

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## ⚠️ Disclaimer

This guide is based on community tutorials. Always verify commands and sources before execution. Use at your own risk and ensure you understand the implications of running blockchain infrastructure.

## 🔗 Useful Links

- [Gensyn Official Website](https://gensyn.ai)
- [Gensyn Documentation](https://docs.gensyn.ai)
- [Community Discord](https://discord.gg/gensyn)

## 📞 Support

For additional support:
- GitHub Issues: [Create an issue](https://github.com/username/gensyn-node-setup/issues)
- Community: Join the Discord server
- Documentation: Check official Gensyn docs

---

*⭐ If this guide helped you, please give it a star!*

*📋 Guide originally based on FasoNodez tutorial*
