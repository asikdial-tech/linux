# 🐧 Fedora First-Time Setup Script

![Fedora Linux Logo](https://upload.wikimedia.org/wikipedia/commons/thumb/4/41/Fedora_icon_%282021%29.svg/240px-Fedora_icon_%282021%29.svg.png)

## 📝 Why This Exists
Every fresh Fedora installation requires the same setup steps. This repository ensures I never miss anything and can get productive immediately.

```bash
# One-command installation (recommended)
curl -sL https://raw.githubusercontent.com/yourusername/fedora-setup/main/setup.sh | bash

# Update everything
sudo dnf upgrade --refresh -y
sudo dnf autoremove -y

# Add RPM Fusion repositories
sudo dnf install -y \
  https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm \
  https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm

# Media & Creativity
sudo dnf install -y \
  vlc \
  obs-studio \
  gimp \
  inkscape \
  kdenlive

# System Tools
sudo dnf install -y \
  gnome-tweaks \
  gnome-extensions-app \
  gnome-shell-extension-dash-to-dock \
  timeshift \
  htop

# Faster application loading
sudo dnf install -y preload
sudo systemctl enable --now preload

# Better battery life
sudo dnf install -y tlp tlp-rdw
sudo systemctl enable --now tlp

# Multimedia codecs
sudo dnf install -y \
  gstreamer1-plugins-* \
  gstreamer1-libav \
  gstreamer1-vaapi \
  ffmpeg \
  libdvdcss

# Node.js via NVM
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.2/install.sh | bash
source ~/.bashrc
nvm install --lts
nvm install node

# Python setup
sudo dnf install -y \
  python3-pip \
  python3-virtualenv \
  python3-devel

# Additional dev tools
sudo dnf install -y \
  git \
  vim \
  podman \
  buildah

# Create theme directories
mkdir -p ~/.themes ~/.icons ~/.local/share/backgrounds

# Dock behavior (click to minimize)
gsettings set org.gnome.shell.extensions.dash-to-dock click-action 'minimize'

# Dark mode preference
gsettings set org.gnome.desktop.interface color-scheme 'prefer-dark'

# Install local RPM packages
sudo dnf install -y ./package.rpm

# Clean package cache
sudo dnf clean all

# Check for broken dependencies
sudo dnf repoquery --unsatisfied

# Install local RPM packages
sudo dnf install -y ./package.rpm

# Clean package cache
sudo dnf clean all

# Check for broken dependencies
sudo dnf repoquery --unsatisfied
