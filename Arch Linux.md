# Installation
## Pre-Iinstall
1. **Check Internet Connection**:
    - Wired: Usually works automatically. Test with ping archlinux.org.
    - Wi-Fi: Configure manually if needed:
	```bash
    root@archiso $ iwctl
    [iwd]$ device list # Find your wireless device (e.g., wlan0) 
    [iwd]$ station wlan0 scan # scan for networks
    [iwd]$ station wlan0 get-networks # list the scanned networks
    [iwd]$ station wlan0 connect "WIFI_SSID" # Enter passphrase
	root@archiso $ ping archlinux.org # Verify connectivity
	```
2. **Update the System Clock**:
```bash
root@archiso $ timedatectl set-ntp true
root@archsio $ date
```
## archinstall
```bash
root@archiso $ sudo pacman -Sy archinstall
root@archiso $ archinstall
```
3. **Mirrors Region**: Select Mirrors Region `France` (if algeria is not available)
4. **Disk Configuration**
	- **Best-effort default layout**: Wipes the disk and sets up EFI (if UEFI), root, and swap automatically.    
	- **Manual partitioning**: For custom setups (e.g., dual-boot).
5. **Disk Encryption**
	- Don't encyprt usually
	- else use [[Linux Unified Key Setup (LUKS)]]
6. **Swap**: enable [[Swap Memory]] with 4GB (usually)
7. **Bootloader** - Choose Grub
8. **Audio** : Pipewire
## **Post Install**
1. remove the default directories.
```bash
$ vim ~/.config/user-dirs.dirs
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_PICTURES_DIR="$HOME/Pictures"
...SNIP...

$ xdg-user-dirs-update # applies changes
```

## Manual Install
---
Relate: [[Package Manager (Pacman)|Pacman]]