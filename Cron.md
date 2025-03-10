**Cron** is a **time-based job scheduler** in Unix-like operating systems. It allows users to schedule **automated tasks (cron jobs)** to run at specific times or intervals. managed by the **cron daemon (`crond`)**. 

# **Where do Cronjobs live**
Cron jobs are stored in **crontab (cron table) files**.
Cron jobs can be listed from different locations depending on whether they are **user-specific** or **system-wide**. Here are **all the possible locations** where cron jobs can be stored:
### **1. User-Specific Crontabs**
Each user has their own crontab file stored in:
```bash
/var/spool/cron/crontabs/USERNAME  # Debian/Ubuntu  
/var/spool/cron/USERNAME           # RHEL/CentOS/Arch  
```
To list a specific user's cron jobs:
```bash
crontab -u username -l
```
To list your own cron jobs:
```bash
crontab -l
```
These crontabs **should not be edited manually**—always use `crontab -e` to edit.

---
### **2. System-Wide Cron Jobs**
System-wide cron jobs are stored in:
```
/etc/crontab
```
To view system-wide cron jobs:
```bash
cat /etc/crontab
```
These jobs include an additional **USER** field (to specify which user runs the job).

---
### **3. Jobs in `/etc/cron.d/`**
Files in this directory contain additional system-wide cron jobs.
```bash
ls -l /etc/cron.d/
cat /etc/cron.d/*
```
Each file follows the same format as `/etc/crontab`.

---
### **4. Periodic Cron Job Directories**
Scripts placed in these directories run automatically at predefined intervals:

|Directory|Runs|
|---|---|
|`/etc/cron.hourly/`|Every hour|
|`/etc/cron.daily/`|Every day|
|`/etc/cron.weekly/`|Every week|
|`/etc/cron.monthly/`|Every month|
To list scripts in these locations:
```bash
ls -l /etc/cron.hourly/
ls -l /etc/cron.daily/
ls -l /etc/cron.weekly/
ls -l /etc/cron.monthly/
```
---
### **5. Checking All Cron Jobs for All Users**
To list all user cron jobs:
```bash
for user in $(cut -f1 -d: /etc/passwd); do  
    echo "Crontab for: $user"  
    crontab -u $user -l 2>/dev/null  
done
```
This loops through all system users and displays their cron jobs.
To list system-wide cron jobs and user cron jobs together:
```bash
cat /etc/crontab
ls -l /etc/cron.d/
crontab -l
for user in $(cut -f1 -d: /etc/passwd); do crontab -u $user -l 2>/dev/null; done
```
---
### **Summary of Cron Job Locations**

| Location                            | Purpose                          | Listing Command            |
| ----------------------------------- | -------------------------------- | -------------------------- |
| `/var/spool/cron/crontabs/USERNAME` | User-specific cron jobs          | `crontab -l`               |
| `/etc/crontab`                      | System-wide cron jobs            | `cat /etc/crontab`         |
| `/etc/cron.d/`                      | Additional system-wide cron jobs | `ls -l /etc/cron.d/`       |
| `/etc/cron.hourly/`                 | Hourly jobs                      | `ls -l /etc/cron.hourly/`  |
| `/etc/cron.daily/`                  | Daily jobs                       | `ls -l /etc/cron.daily/`   |
| `/etc/cron.weekly/`                 | Weekly jobs                      | `ls -l /etc/cron.weekly/`  |
| `/etc/cron.monthly/`                | Monthly jobs                     | `ls -l /etc/cron.monthly/` |
# **Syntax**
A Cron Job stored in `/etc/crontab` for example follows this syntax:
```bash
MIN HOUR DOM MON DOW USER COMMAND
```
- `MIN` (0-59) → Minute of execution
- `HOUR` (0-23) → Hour of execution (24-hour format)
- `DOM` (1-31) → Day of the month
- `MON` (1-12) → Month (January = 1, December = 12)
- `DOW` (0-7) → Day of the week (Sunday = 0 or 7)
- `USER` The user that the cronjob runs as
- `COMMAND` → The script or command to execute
```bash
# Run a script every day at 3 AM
0 3 * * * /path/to/script.sh

# Run a command as root every Monday at 8 AM
0 8 * * 1 root echo "Weekly reminder"

# Run a backup script at midnight on the first day of every month
0 0 1 * * /path/to/backup.sh
```

> [!warning] Warning
> Unlike user crontabs (`crontab -e`), **`/etc/crontab` requires a user field**:
> ```bash
> */5 * * * * root /path/to/script.sh
> ```
> If you forgot the **USER** field, the cron job **won't run**.
## **Special Scheduling Keywords**
Instead of numbers, you can use:
- `@reboot` → Run once at system startup
- `@hourly` → Run every hour
- `@daily` → Run once a day
- `@weekly` → Run once a week
- `@monthly` → Run once a month
- `@yearly` → Run once a year
```bash
# Example
@daily /path/to/daily-task.sh
```
## **Special Characters**
Cron jobs use special characters to define flexible schedules. The most common ones are:
3. Asterisk (`*`) Means **"any" or "every"** possible value.
4. Comma (`,`) Specifies **multiple values** in a field.
5. Dash (`-`) Specifies **a range of values**.
6. Slash (`/`) Defines a **step interval**.
7.  Question Mark (`?`) Used instead of `*` when the exact value is **not specified**
8. Hash (`#`) Specifies **"the nth weekday"** of a month. (Only system-wide crontabs)
```bash
# Run the script every minute, every hour, every day, etc.
* * * * * /path/to/script.sh

# Run at 9 AM and 6 PM every day.
0 9,18 * * * /path/to/script.sh

# Run every hour from 5 AM to 10 AM.
0 5-10 * * * /path/to/script.sh

# Run every 15 minutes.
*/15 * * * * /path/to/script.sh

# Run at 12 PM every day, ignoring the day of the week.
0 12 * * ? /path/to/script.sh

# Run on the first Tuesday of every month.
0 9 * * 2#1 /path/to/script.sh
```
# **crontab.sh**
The `crontab` command is used to **manage user-specific cron jobs** in Linux.
```bash
/var/spool/cron/crontabs/USERNAME  # Debian/Ubuntu  
/var/spool/cron/USERNAME           # RHEL/CentOS/Arch  
```

| Command                  | Description                                           |
| ------------------------ | ----------------------------------------------------- |
| `crontab -e`             | Edit the current user's crontab.                      |
| `crontab -l`             | List the current user's cron jobs.                    |
| `crontab -r`             | Remove the current user's crontab.                    |
| `crontab -i -r`          | Remove the current user's crontab **withnfirmation**. |
| `crontab -u username -l` | List another user's crontab (root required).          |
| `crontab -u username -e` | Edit another user's crontab (root required).          |
# Installation
```
sudo pacman -S cronie
```

```
sudo systemctl enable --now cronie.service
```
# Etymology
**Cron** does stand for “command run on notice”. However, the abbreviation also alludes to Chronos, the ancient Greek god of time.