`iwctl` is the command-line interface for **iwd** (iNet Wireless Daemon), which is a lightweight and efficient wireless network manager for Linux. It is designed as an alternative to `wpa_supplicant` and integrates well with systemd.

---
## **1. Checking if `iwd` is Installed and Running**
Before using `iwctl`, ensure that **iwd** is installed and running.
```bash
pacman -Q iwd   # Arch Linux
apt list --installed | grep iwd  # Debian-based
```
### **Start `iwd` if not running:**

```bash
sudo systemctl start iwd
```

### **Enable `iwd` to start on boot:**

```bash
sudo systemctl enable iwd
```

### **Check service status:**

```bash
systemctl status iwd
```

---

## **2. Using `iwctl`**

To start `iwctl`, simply run:

```bash
iwctl
```

This launches an interactive shell where you can run commands.

Alternatively, you can execute a command directly:

```bash
iwctl <command>
```

### **Exit `iwctl`**

Type:

```bash
exit
```

---

## **3. Checking Available Interfaces**

To list available Wi-Fi interfaces:

```bash
iwctl device list
```

Example output:

```
Devices:
 Name     Type      Powered   Adapter   Mode
 wlan0    station   on        phy0      connected
```

This shows that `wlan0` is the available network interface.

---

## **4. Scanning for Wi-Fi Networks**

To scan for available networks:

```bash
iwctl station wlan0 scan
```

After scanning, list detected networks:

```bash
iwctl station wlan0 get-networks
```

Example output:

```
Available networks:
Network name     Signal   Security
MyWiFi           80%      wpa2
PublicWiFi       60%      open
```

---

## **5. Connecting to a Wi-Fi Network**

### **5.1 Connecting to an Open Network**

If the network has no password:

```bash
iwctl station wlan0 connect "PublicWiFi"
```

### **5.2 Connecting to a Password-Protected Network**

If the network requires a password:

```bash
iwctl station wlan0 connect "MyWiFi" --passphrase "your_password"
```

If successful, it will say:

```
Connected successfully
```

### **5.3 Connecting with a Hidden SSID**

If the network does not broadcast its SSID:

```bash
iwctl station wlan0 connect-hidden "HiddenSSID" --passphrase "your_password"
```

---

## **6. Disconnecting from a Network**

To disconnect from the current Wi-Fi network:

```bash
iwctl station wlan0 disconnect
```

---

## **7. Managing Saved Networks**

### **7.1 Listing Saved Networks**

```bash
iwctl known-networks list
```

### **7.2 Forgetting a Saved Network**

```bash
iwctl known-networks "MyWiFi" forget
```

### **7.3 Forget All Networks**

```bash
iwctl known-networks flush
```

---

## **8. Checking Connection Status**

To check the current connection status:

```bash
iwctl station wlan0 show
```

Example output:

```
Connected network: MyWiFi
Signal strength: 75%
IP address: 192.168.1.100
```

---

## **9. Power Management**

### **9.1 Turning Wi-Fi On/Off**

Turn Wi-Fi on:

```bash
iwctl radio wifi on
```

Turn Wi-Fi off:

```bash
iwctl radio wifi off
```

### **9.2 Enabling/Disabling a Specific Interface**

Enable the `wlan0` interface:

```bash
iwctl device wlan0 set-property Powered on
```

Disable it:

```bash
iwctl device wlan0 set-property Powered off
```

---

## **10. Connecting via DHCP or Static IP**

By default, `iwd` does not handle IP addressing. Instead, it relies on **systemd-networkd** or **dhclient**.

### **10.1 Using `dhclient`**

If you use `dhclient`, run:

```bash
sudo dhclient wlan0
```

### **10.2 Using `systemd-networkd`**

Configure `/etc/systemd/network/25-wireless.network`:

```
[Match]
Name=wlan0

[Network]
DHCP=yes
```

Then restart `systemd-networkd`:

```bash
sudo systemctl restart systemd-networkd
```

---

## **11. Debugging & Logs**

### **11.1 Check if `iwd` is Running**

```bash
systemctl status iwd
```

### **11.2 View `iwd` Logs**

```bash
journalctl -u iwd --no-pager
```

### **11.3 Check Wireless Device Info**

```bash
iwctl device wlan0 show
```

### **11.4 Check Network Information**

```bash
iwctl station wlan0 show
```

---

## **12. Advanced Configuration**

`iwd` stores configurations in `/var/lib/iwd/`.

### **12.1 Manually Configuring Wi-Fi**

You can manually edit the Wi-Fi configuration:

```bash
sudo nano /var/lib/iwd/MyWiFi.psk
```

Example content:

```
[Security]
Passphrase=your_password
```

Save and restart `iwd`:

```bash
sudo systemctl restart iwd
```

---

## **13. Comparing `iwd` vs `wpa_supplicant`**

|Feature|`iwd`|`wpa_supplicant`|
|---|---|---|
|Performance|Lightweight & fast|Heavier|
|Dependencies|Minimal|Requires more dependencies|
|Configuration|Simple, automatic|Manual setup required|
|IPv4/IPv6 DHCP|Requires `systemd-networkd` or `dhclient`|Can handle DHCP directly|

---

## **14. Uninstalling `iwd`**

If you want to remove `iwd` and switch back to `wpa_supplicant`:

### **Remove `iwd`:**

```bash
sudo pacman -Rns iwd   # Arch Linux
sudo apt remove --purge iwd   # Debian-based
```

### **Re-enable `wpa_supplicant`:**

```bash
sudo systemctl enable --now wpa_supplicant
```

---

## **Conclusion**

`iwctl` is a powerful and lightweight tool for managing Wi-Fi on Linux. It simplifies network management while being more efficient than `wpa_supplicant`.

# Etymology

`iwctl` stands for **"iNet Wireless Control Tool"**.

- **`iNet Wireless`** refers to **iwd** (iNet Wireless Daemon), a lightweight wireless network manager developed by Intel.
- **`Control Tool`** indicates that `iwctl` is a command-line interface used to manage Wi-Fi networks via `iwd`.

Essentially, `iwctl` is the CLI tool used to interact with **iwd**, allowing you to scan, connect, disconnect, and manage wireless networks efficiently. 🚀