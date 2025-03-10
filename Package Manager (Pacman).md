#command 

Pacman (`pac`kage `man`ager) is Arch Linux's default package manager. 

```
sudo pacman [OPTION] package_name
```

---
# Usage 
### **Installing Packages**
- **Install a package** from the official repositories:
    ```bash
    sudo pacman -S <package_name>
    ```
	`-S`: This tells pacman to synchronize (install or update) the package with the latest version available in the repositories.
- **Install multiple packages**:
    ```bash
    sudo pacman -S package1 package2 package3
    ```
- **Reinstall a package**:
    ```bash
    sudo pacman -S <package_name> --overwrite '*'
    ```
### **Removing Packages**
- **Remove a package**:
    ```bash
    sudo pacman -R <package_name>
    ```
- **Remove a package and its dependencies (if not needed by others)**:
    ```bash
    sudo pacman -Rns <package_name>
    ```
### **Updating Packages**
- **Update the entire system**:
    ```bash
    sudo pacman -Syu
    ```
- **Update only a specific package**:
    ```bash
    sudo pacman -S <package_name>
    ```
---
## **2. Managing Repositories**
### **Syncing Repositories**
- **Refresh the package database**:
    ```bash
    sudo pacman -Sy
    ```
- **Sync and upgrade all packages**:
    ```bash
    sudo pacman -Syu
    ```
### **Finding Packages**
- **Search for a package in the official repositories**:
    
    ```bash
    pacman -Ss <keyword>
    ```
    
- **Check if a package is installed**:
    
    ```bash
    pacman -Qs <package_name>
    ```
    

---

## **3. Handling Package Files**

### **Listing Installed Packages**

- **List all installed packages**:
    
    ```bash
    pacman -Q
    ```
    
- **Check the installed version of a package**:
    
    ```bash
    pacman -Qi <package_name>
    ```
    
- **List all explicitly installed packages**:
    
    ```bash
    pacman -Qe
    ```
    
- **List all dependencies installed automatically**:
    
    ```bash
    pacman -Qdt
    ```
    

### **Cleaning Up**

- **Remove orphaned dependencies**:
    
    ```bash
    sudo pacman -Rns $(pacman -Qdtq)
    ```
    
- **Clear the package cache (only old versions)**:
    
    ```bash
    sudo pacman -Sc
    ```
    
- **Clear the entire package cache** (use cautiously):
    
    ```bash
    sudo pacman -Scc
    ```
    

---

## **4. Troubleshooting Pacman**

### **Fixing Keyring Issues**

- If you get **"invalid or corrupted package"** errors:
    
    ```bash
    sudo pacman -Sy archlinux-keyring
    ```
    

### **Unlocking a Stuck Database**

- If Pacman is locked by another process:
    
    ```bash
    sudo rm /var/lib/pacman/db.lck
    ```
    

### **Fixing Failed Transactions**

- If you get a package conflict or dependency issue:
    
    ```bash
    sudo pacman -Syu --overwrite '*'
    ```
    

### **Forcing a Package Reinstallation**

- If a package is corrupted or misbehaving:
    
    ```bash
    sudo pacman -S <package_name> --overwrite '*'
    ```
    

---

## **5. Using the Arch User Repository (AUR)**

Pacman does not support the **AUR (Arch User Repository)** directly. To install AUR packages, you need an **AUR helper** like `paru` or `yay`.

### **Installing an AUR Helper (`yay`)**

```bash
sudo pacman -S git base-devel
git clone https://aur.archlinux.org/yay-bin.git
cd yay-bin
makepkg -si
```

### **Using yay (AUR Helper)**

- Install an AUR package:
    
    ```bash
    yay -S <package_name>
    ```
    
- Update all packages, including AUR:
    
    ```bash
    yay -Syu
    ```
    
- Search for a package:
    
    ```bash
    yay -Ss <keyword>
    ```
    

---

## **6. Additional Pacman Tips**

- **Download a package without installing it**:
    
    ```bash
    sudo pacman -Sw <package_name>
    ```
    
- **List all available package groups**:
    
    ```bash
    pacman -Sg
    ```
    
- **Check what package provides a specific file**:
    
    ```bash
    pacman -F <file_name>
    ```
    

---
# Troubleshooting
1. The request URL is returned error 404
```bash
# update the package list
sudo pacman -Sy
```