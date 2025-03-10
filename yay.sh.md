#command 

Yet Another Yaourt (yay) is a helper too used to download packages from the [[Arch User Repository (AUR)]].

---
# Installation
Dependencies:
```
sudo pacman -S base-devel git
```
Installing yay:
```bash
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```
---
# Usage

```bash
#download a package
yay -S package_name

# Remove Package
yay -R package_name

# Remove Package with Dependencies
yay -Rns package_name
```

> [!NOTE] Warning
> Don't use sudo with yay, just type the command and it will prompt you
