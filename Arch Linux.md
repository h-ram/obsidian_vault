
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
#### 3. **Mirrors Region**
- Select Mirrors Region `France` (if algeria is not available)
#### 4. **Disk Configuration**
- **Best-effort default layout**: Wipes the disk and sets up EFI (if UEFI), root, and swap automatically.    
- **Manual partitioning**: For custom setups (e.g., dual-boot).
#### 5. **Disk Encryption**
- Don't encyprt usually
- else use [[Linux Unified Key Setup (LUKS)]]
#### 6. **Swap**
- [[Swap Memory]]
- the ideal swap size depends on your **RAM size**, **usage**, and whether you need **hibernation**.

| **RAM Size** | **Swap (No Hibernation)** | **Swap (With Hibernation)** |
| ------------ | ------------------------- | --------------------------- |
| ≤ 2GB        | 2GB – 4GB                 | 1.5× RAM                    |
| 4GB – 8GB    | 2GB – 4GB                 | 1.5× RAM                    |
| 8GB – 16GB   | 2GB – 4GB                 | 1.5× RAM                    |
| 16GB – 32GB  | 1GB – 4GB                 | 1.5× RAM                    |
| > 32GB       | 0GB – 2GB (or none)       | 1.5× RAM                    |
#### 7. **Bootloader**
- Choose Grub
- Audio : Pipewire
## Manual Install
---
Relate: [[Package Manager (Pacman)|Pacman]]