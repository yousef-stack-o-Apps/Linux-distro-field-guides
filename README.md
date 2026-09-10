# Linux Distro Field Guides

> Practical installation and customization guides for deploying Linux distributions on bare metal systems.

[![GitHub](https://img.shields.io/badge/GitHub-yousef--stack--o--Apps-blue?logo=github)](https://github.com/yousef-stack-o-Apps)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

## Overview

This repository contains battle-tested installation procedures and workarounds for various Linux distributions. Each guide covers real-world challenges that official documentation often overlooks.

## Table of Contents

- [Supported Distros](#supported-distros)
- [Featured Guides](#featured-guides)
- [Installing Debian (GNOME)](#installing-debian-gnome)
- [Quick Start](#quick-start)
- [Contributing](#contributing)

## Supported Distros

- **ML4W OS** (Arch-based)
- *More guides coming soon*

## Featured Guides

### ML4W OS on Bare Metal

A complete walkthrough for installing ML4W OS directly on physical hardware (typically optimized for VMs).

#### Prerequisites

- USB drive (8GB+)
- Target system with 200GB+ free space
- Backup of important data ⚠️
- [ML4W OS ISO](https://ml4w.com/iso/ml4w-os/ml4w-os-2.15.1-x86_64.iso) (v2.15.1 x86_64)
- [Ventoy](https://sourceforge.net/projects/ventoy/files/v1.1.17/) - A bootable USB solution for creating multi-boot installations

#### Installation Steps

##### Step 1: Enable Wi-Fi in Live Environment

The live environment may have networking issues. Verify NetworkManager is running:

```bash
nmcli
```

If NetworkManager isn't active:

```bash
sudo systemctl start NetworkManager
```

Once started, the Wi-Fi icon will appear in the system tray. Connect to your network and proceed.

##### Step 2: Reclaim Disk Space Post-Install

The installer defaults to a full-disk install. After installation completes, shrink the ML4W partition:

**⏱️ Note:** The ML4W installation will take approximately **3GB+** of disk space once complete.

**Install GParted:**
```bash
sudo pacman -S gparted
```

**Resize the partition:**
1. Launch GParted
2. Locate the ML4W partition
3. Resize to desired size (e.g., 170 GB)
4. Allocate freed space for additional OS installations or data

##### Step 3: Install ML4W Dotfiles (Optional)

To customize your ML4W installation with community dotfiles and configurations, visit the [ML4W Dotfiles Installer](https://github.com/mylinuxforwork/ml4w-dotfiles-installer) repository for setup instructions and usage.

---

## Installing Debian (GNOME)

This section walks through installing Debian with the GNOME desktop and includes an optional installer from the DankLinux project (AvengeMedia/DankMaterialShell).

Step 1: Grab the ISO and Flash It

- Download the official Debian netinst ISO (use the non-free firmware image if your hardware needs it).
- Flash the ISO to a USB drive using Ventoy, Rufus, or dd.

Step 2: Boot Up and Launch the Installer

- Plug the USB into your target machine, reboot, and open your BIOS/UEFI boot menu (F12, F11, Esc, or Del on many systems).
- Select the USB drive, then choose "Graphical install" (or the standard text installer).

Step 3: Language, Region, and Network

- Select your language, country/location, and keyboard layout.
- The installer will attempt to configure your network interface automatically.

  Note: If you are installing over Wi‑Fi and the installer doesn't recognize your wireless card (missing drivers/firmware), plug in an Ethernet cable for the installation phase.

- Enter a hostname for your machine (e.g., `debian-dev`).

Step 4: Users and Passwords

- Root account: Debian will ask if you want to set a root password. Leaving it blank disables root and grants sudo to your primary user (recommended by many).
- Create a user: enter your full name, choose a lowercase username, and set a secure password.
- Set your correct timezone.

Step 5: Partitioning Your Drives

- For beginners, choose Guided → use entire disk (back up first!).
- Select your target drive and the partitioning scheme ("All files in one partition" is fine for most users).
- Review, Finish partitioning, and write changes to disk.

Step 6: Package Manager and Tasksel (Choose GNOME)

- After the base system installs you'll be prompted to choose an APT mirror — pick your country and a reliable mirror.
- When tasksel appears, select the "GNOME" desktop environment to install a full GNOME desktop.

If you missed GNOME during install, after first boot you can add it:

```bash
sudo apt update
sudo apt install tasksel
sudo tasksel install gnome-desktop
```

Step 7: Finish and Reboot

- Install the GRUB bootloader to the primary drive when prompted.
- Finish, remove the USB when instructed, and boot into your new GNOME desktop.

Optional: Install DankMaterialShell (AvengeMedia/DankMaterialShell)

The DankMaterialShell project provides a modern desktop shell and an installer used across many distributions. Their repository is here:

- https://github.com/AvengeMedia/DankMaterialShell

One-line installer used by the project:

```bash
curl -fsSL https://install.danklinux.com | sh
```

Important security note: piping a remote script straight to sh runs code you haven't inspected. It's convenient but risky. If you choose to use it, consider these safer steps first:

1. Download and inspect the script:

```bash
curl -fsSL -o install-danklinux.sh https://install.danklinux.com
less install-danklinux.sh
```

2. Verify checksums or signatures if the project provides them.
3. Run the script in a VM or disposable environment first, or run it as a normal user before using sudo.

If you want, I can add a short, dedicated Debian + GNOME guide file (docs/debian-gnome.md) or commit this README update directly to this repository.

## Troubleshooting

Experiencing issues? Check the relevant guide section or [open an issue](https://github.com/yousef-stack-o-Apps/Linux-distro-field-guides/issues).

## Contributing

We welcome contributions! Whether it's a driver fix, installer workaround, or new distro guide:

1. [Fork the repository](https://github.com/yousef-stack-o-Apps/Linux-distro-field-guides/fork)
2. Create a feature branch (`git checkout -b feature/new-guide`)
3. Commit your changes (`git commit -m 'Add: Debian GNOME install guide and DankMaterialShell reference'`)
4. Push to the branch (`git push origin feature/new-guide`)
5. Open a [Pull Request](https://github.com/yousef-stack-o-Apps/Linux-distro-field-guides/pulls)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Questions or suggestions?** Open an [issue](https://github.com/yousef-stack-o-Apps/Linux-distro-field-guides/issues) or reach out on GitHub.
