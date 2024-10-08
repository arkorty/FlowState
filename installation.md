# Bootable Environment

### Requirements

- A USB drive (at least 2GB capacity)
- Arch Linux ISO file (latest version)
- A system with a Linux distribution installed (e.g., Ubuntu, Fedora) or Windows with a tool like Rufus.

### Steps for Linux Users

##### Download the Arch Linux ISO

- Go to the [official Arch Linux website](https://www.archlinux.org/download/) and download the latest ISO.

##### Insert your USB drive

- Connect the USB drive to your computer.

##### Identify your USB drive

- Open a terminal and run:
  
  ```bash
  lsblk
  ```

- Find your USB drive (e.g., `/dev/sdX`, where `X` is the drive letter).

##### Create the bootable USB

- Use the `dd` command to write the ISO to your USB:
  
  ```bash
  sudo dd bs=4M if=/path/to/archlinux.iso of=/dev/sdX status=progress oflag=sync
  ```

- Replace `/path/to/archlinux.iso` with the path to your downloaded ISO and `/dev/sdX` with your USB drive (don’t include partition numbers like `/dev/sdX1`).

##### Sync and eject

- Wait for the command to finish, then run:
  
  ```bash
  sync
  ```

- After that, safely eject your USB:
  
  ```bash
  sudo eject /dev/sdX
  ```

## Steps for Windows Users

##### Download the Arch Linux ISO

- Visit the [Arch Linux website](https://www.archlinux.org/download/) and download the latest ISO.

##### Download Rufus

- Go to the [Rufus website](https://rufus.ie/) and download the latest version.

##### Create the bootable USB

- Open Rufus.
- Select your USB drive in the "Device" field.
- In the "Boot selection" field, choose the downloaded Arch Linux ISO.
- Click **Start** and wait for the process to finish.

##### Eject the USB

- Once Rufus finishes, safely eject the USB.

## Booting into Arch Linux

1. Insert the USB drive into the target system.
2. Restart the system and boot from the USB by selecting it in the BIOS/UEFI boot menu (usually accessible via keys like `F2`, `F12`, or `Esc`).
3. You should now boot into the Arch Linux installation environment.

# Installation

## Internet Connection

1. Before proceeding with the installation, check for an active internet connection by running:
   
   ```bash
   # ping 1.1.1.1
   ```

2. Arch Linux live environment now includes the `archinstall` script:
   
   ```bash
   # archinstall
   ```

The `archinstall` script provides an easy, guided way to install the system via a text-based installer.

## Arch Install Script Steps

##### Language

- Select your desired language for the installation process.

##### Mirrors

- Select the region for your package mirrors. A nearby region speeds up package downloads during installation.

##### Locales

- Choose a keyboard layout (default is `us` for U.S. English). You can pick from various layouts based on your preference.

##### Disk configuration

- Select the disk where you want to install Arch Linux. You'll see a list of available drives (e.g., `/dev/sda`, `/dev/nvme0n1`).
- Options include:
  - **Use entire disk (auto-partition)**
  - **Manual partitioning** for more control over disk layout.
- Choose the partition type (e.g., `ext4`, `btrfs`, `xfs`) for your root and home partitions.

##### Encryption (Optional)

- You can encrypt your disk with LUKS for added security.
- If selected, you’ll set a password to unlock the disk at boot time.

##### Bootloader

- Choose the bootloader to install:
  - **GRUB** (default)
  - **systemd-boot**
  - Or select none if you wish to configure it manually later.

##### Swap

- Choose whether to create a swap file, swap partition, or none.
- Set the size of the swap file (typically 1-2x the amount of RAM).

##### Filesystem Type

- Select the filesystem for your root partition:
  - **ext4** (default and common)
  - **btrfs** (for advanced features like snapshots)
  - **xfs**, **f2fs**, etc.

##### Hostname

- Set a hostname for your machine (e.g., `archlinux`).

##### Root Password

- Set a password for the root user (administrator).

##### User Creation

- Create a non-root user account for daily operations.
- Set a password for this user.
- Optionally, add the user to the sudo group for administrative privileges.

##### Profile Selection

- Choose a system profile:
  - **Desktop environment** (like GNOME, KDE Plasma, Xfce, etc.)
  - **Headless installation** (minimal install without GUI)
  - **Custom** (install what you want without predefined packages).

##### Additional Packages

- Optionally, install additional packages like:
  - **vim** or **nano** (text editors)
  - **git**, **networkmanager**, and other utilities.
- You can skip this step and install packages later if preferred.

##### Network Configuration

- Choose a network management tool:
  - **NetworkManager** (common for laptops/desktops)
  - **iwd**, **wpa_supplicant**, etc.
- The script may auto-configure your network, depending on your choice.

##### Time Zone & Localization

- Select your time zone (e.g., `Europe/London`).
- Set the system locale (default is `en_US.UTF-8`).

##### Finalize Installation

- Review your configuration before starting the installation.
- Once confirmed, the system will be installed according to your selections.

##### Post-Installation

- After installation, you’ll be prompted to reboot into your new Arch Linux system. Reboot by running:
  
  ```bash
  # reboot
  ```
