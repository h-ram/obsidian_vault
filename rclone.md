# Usage
```bash
$ rclone config
# go through the setup steps
```
After creating your remote storage, Run your first sync with `--resync` (important):
```
rclone bisync gdrive:obsidian /home/ram/googleDrive --resync --progress
```
Next create a cronjob that handles all the sync from now on:
```bash
$ crontab -e

# Sync Download on system boot
@reboot rclone sync gdrive:obsidian /home/ram/googleDrive --progress

# Sync Download and upload every 5 minutes
*/5 * * * * rclone bisync gdrive:obsidian /home/ram/googleDrive --progress
```
This will store the cronjob in 
```bash
/var/spool/cron/crontabs/USERNAME  # Debian/Ubuntu  
/var/spool/cron/USERNAME           # RHEL/CentOS/Arch  
```
# Installation
```bash
sudo pacman -S rclone
```
---
Resrouces:
- [Sync Google Drive in linux using rclone](https://www.youtube.com/watch?v=ff8Ogk8NIPU&pp=ygUuc3luYyBnb29nbGUgZHJpdmUgZm9sZGVyIGluIGxpbnV4IHVzaW5nIHJjbG9uZQ%3D%3D)
- [Using Rclone to sync files to Google Drive](https://www.youtube.com/watch?v=X_3gJ3Nbsgc&ab_channel=abhiraaid)