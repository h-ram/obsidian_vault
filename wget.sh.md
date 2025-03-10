#command 

`wget` (Web Get) is used for downloading files from the internet or local network using **HTTP, HTTPS, and FTP** protocols. It works in the background, meaning it **does not require user interaction**, making it ideal for scripts and automation.
```bash
wget [options] <URL>
```

# Usage
```bash
# Basic Usage
wget <URL>                  # Download a file from a URL
wget -O file.zip <URL>      # Save the file with a specific name
wget -P /path/to/dir <URL>  # Save the file in a specific directory

# Resuming and Retries
wget -c <URL>               # Resume a failed or paused download
wget -t 3 <URL>             # Retry failed downloads 3 times
wget -T 10 <URL>            # Set a 10-second timeout

# Speed Control
wget --limit-rate=100k <URL>  # Limit download speed to 100 KB/s

# Downloading Multiple Files
wget -i urls.txt            # Download all URLs listed in a text file

# Recursive Download
wget -r <URL>               # Recursively download everything from a directory
wget -np -r <URL>           # Prevent going to parent directories

# Authentication
wget --user=username --password=password <URL>  # Use login credentials

# Custom Headers and User-Agent
wget --user-agent="Mozilla/5.0" <URL>  # Spoof browser identity
wget --header="Cookie: SESSIONID=abc123" <URL>  # Send custom headers

# Mirroring Websites
wget -m -k -p -E <URL>      # Download a website for offline use

# Quiet and Verbose Mode
wget -q <URL>               # Quiet mode (no output)
wget -v <URL>               # Verbose mode (detailed output)

# Port Specification
wget --no-check-certificate <URL>  # Ignore SSL certificate warnings
wget --bind-address=<IP> <URL>     # Use a specific network interface

```