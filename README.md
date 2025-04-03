# 🐧 Fedora Linux Setup Guide

![Fedora Linux Logo](https://upload.wikimedia.org/wikipedia/commons/thumb/4/41/Fedora_icon_%282021%29.svg/240px-Fedora_icon_%282021%29.svg.png)

## 📝 Why This Exists
Every fresh Fedora installation requires the same setup steps. This repository ensures I never miss anything and can get productive immediately.

## Introduction
This guide provides a streamlined approach to setting up Fedora Linux with all necessary tools and configurations to ensure a smooth and efficient workflow.

---
## 1. Installation
### Steps:
1. **Download Fedora ISO:** Get the latest version from [Fedora's official website](https://getfedora.org/).
2. **Create a bootable USB:** Use `dd` or **Rufus** to flash the ISO.
3. **Boot and Install:**
   - Boot from the USB and follow the Fedora installer.
   - Select disk partitions (Recommended):
     - `/` (root) - 70GB (OS and apps)
     - `/home` - 100GB (User files and projects)
     - `swap` - 30GB (Virtual memory, adjust as needed)
   - Complete the installation and reboot.
4. **Update System:**
   ```bash
   sudo dnf update -y
   ```
---

## 2. Desktop Environment
### Recommended:
- **XFCE (Lightweight & Fast)**
  ```bash
  sudo dnf install @xfce-desktop
  ```
- **GNOME (Modern Look)**
  ```bash
  sudo dnf groupinstall "GNOME Desktop Environment"
  ```
- **MacOS Look:**
  ```bash
  sudo dnf install plank
  ```
  - Install `gtk-theme-whitesur` and `whitesur-icon-theme` for a MacOS-like aesthetic.
---

## 3. Essential Software Installation
Install core tools using `dnf`:
```bash
sudo dnf install -y \
  libreoffice \
  firefox \
  obs-studio \
  kdenlive \
  gimp \
  vlc \
  synaptic \
  gnome-tweaks \
  gnome-shell-extensions \
  gnome-shell-extension-manager
```

### Development Tools:
```bash
sudo dnf install -y \
  git \
  vscodium \
  platformio \
  python3-pip \
  thonny \
  miniconda
```

### ESP32 & MicroPython Setup:
```bash
vscodium --install-extension platformio.platformio-ide
```
---

## 4. System Optimization
### Enable Preload for Faster App Launch:
```bash
sudo dnf install preload
sudo systemctl enable preload
sudo systemctl start preload
```

### Improve Laptop Battery Life:
```bash
sudo dnf install tlp tlp-rdw
sudo systemctl enable tlp
sudo systemctl start tlp
```

### GNOME Taskbar Click to Open:
```bash
gsettings set org.gnome.shell.extensions.dash-to-dock click-action 'minimize'
```

---

## 5. Folder Organization
Create structured directories for efficient file management:
```bash
mkdir -p ~/Projects ~/Archives ~/Media ~/Docs
```
Automate backups using `rsync`:
```bash
rsync -av ~/Projects ~/Archives
```

---

## 6. Additional Setup
### Install Node.js (Latest & LTS):
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.2/install.sh | bash
nvm install node
nvm install --lts
```

### Install Custom Software:
```bash
sudo dnf install ./package-name.rpm
```

---

## Conclusion
This guide ensures a clean, optimized Fedora setup tailored for development and multimedia tasks. Follow these steps to maximize efficiency and performance on your system. 🚀

