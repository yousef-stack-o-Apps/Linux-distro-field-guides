# Linux-distro-field-guides
I figure out Diffrent Ways To Install Or Customize Linux Distros
# Distro Field Guides

A collection of practical, battle-tested installation notes and workarounds for running Linux distributions on real hardware.

---

## What This Repo Does

This repository provides simple, step-by-step guides for deploying custom Linux distributions on bare metal. It focuses on solving real-world hurdles that official documentation usually leaves out—like fixing missing network drivers in live environments and working around rigid installation scripts.

---

## Featured Guide: Installing ML4W OS

ML4W OS is an awesome Arch-based setup, but it is typically designed for virtual machines. Here is how to install it directly on your physical computer.

<Callout type="warning" title="Drive Wipe Warning">
The automated installer will try to wipe your entire drive. Back up your important files before you start!
</Callout>

### Step 1: Fix the Wi-Fi in the Live Environment
If you boot up and notice the Wi-Fi isn't working or the tray icon won't let you connect, open a terminal and run:

```bash
nmcli
If it tells you NetworkManager isn't running, start it manually with:
```bash
sudo systemctl start NetworkManager
Once it starts, your Wi-Fi icon will wake up. Click it, connect to your network, and you are ready to install.
### Step 2: Handle the Full-Disk Install & Reclaim Your Space

The installer script demands the whole drive. Let it finish its setup so it doesn't break, and then shrink the partition afterward:
1.Open a terminal after installation and install Gparted:
```bash
sudo pacman -S gparted
2.Launch Gparted, find your massive new ML4W partition, and shrink it down to your desired size (for example, 170 GB).
3.Use the newly freed unallocated space to set up your other operating systems or multi-boot tools.
### Want to Help?
Got a fix for a tricky driver or a workaround for a stubborn installer? Contributions and field notes are welcome! Open an issue or submit a pull request to add your own guides.
