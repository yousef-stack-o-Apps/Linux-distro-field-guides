# Linux Distro Field Guides

> Practical installation and customization guides for deploying Linux distributions on bare metal systems.

[![GitHub](https://img.shields.io/badge/GitHub-yousef--stack--o--Apps-blue?logo=github)](https://github.com/yousef-stack-o-Apps)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

## Overview

This repository contains battle-tested installation procedures and workarounds for various Linux distributions. Each guide covers real-world challenges that official documentation often overlooks.

## Table of Contents

- [Supported Distros](#supported-distros)
- [Featured Guides](#featured-guides)
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

To customize your ML4W installation with community dotfiles and configurations, visit the [ML4W Dotfiles Installer](https://github.com/mylinuxforwork/ml4w-dotfiles-installer) repository for setup instructions and available configurations.

---

## Troubleshooting

Experiencing issues? Check the relevant guide section or [open an issue](https://github.com/yousef-stack-o-Apps/Linux-distro-field-guides/issues).

## Contributing

We welcome contributions! Whether it's a driver fix, installer workaround, or new distro guide:

1. [Fork the repository](https://github.com/yousef-stack-o-Apps/Linux-distro-field-guides/fork)
2. Create a feature branch (`git checkout -b feature/new-guide`)
3. Commit your changes (`git commit -m 'Add: ML4W wireless fix guide'`)
4. Push to the branch (`git push origin feature/new-guide`)
5. Open a [Pull Request](https://github.com/yousef-stack-o-Apps/Linux-distro-field-guides/pulls)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Questions or suggestions?** Open an [issue](https://github.com/yousef-stack-o-Apps/Linux-distro-field-guides/issues) or reach out on GitHub.
