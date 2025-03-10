#command 

ssh (secure shell) is used to connect to another device's shell.
```bash
ssh username@remote_host
```
- remote_host -> the IP address of the device or its domain name.
- username -> the username of one of the users on that device
```bash
#Example
$ ssh Bob@192.168.1.23
Bob@remotehost's password: *********
Bob@remotehost#
```
---
# **Options**
```bash
-p <port>                 # Connect to a specific port (default is 22)
-i <keyfile>              # Use a private key file for authentication
-D <port>                 # Dynamic SOCKS proxy
-X                        # Enable X11 forwarding (for GUI applications)
-Y                        # Enable trusted X11 forwarding
-C                        # Enable compression for faster transfers
-v                        # Enable verbose mode (debugging)
-q                        # Quiet mode (suppress warnings and messages)
-o <option>               # Set specific SSH options
-L <local_port>:<remote_host>:<remote_port>  # Local port forwarding
-R <remote_port>:<local_host>:<local_port>  # Remote port forwarding
```
# **Usage**
```bash
# Specify port (default is 22, but here we use 48892)
ssh user@94.237.54.164 -p 48892 

# Use a private key file for authentication
ssh user@94.237.54.164 -i ~/.ssh/id_rsa 

# Create a dynamic SOCKS proxy on local port 1080
ssh -D 1080 user@94.237.54.164

# Enable X11 forwarding (for running GUI applications remotely)
ssh -X user@94.237.54.164

# Enable trusted X11 forwarding (some applications require this)
ssh -Y user@94.237.54.164

# Enable compression for faster data transfer
ssh -C user@94.237.54.164

# Enable verbose mode (useful for debugging connection issues)
ssh -v user@94.237.54.164

# Quiet mode (suppress warnings and messages)
ssh -q user@94.237.54.164

# Set a specific SSH option (e.g., disabling strict host key checking)
ssh -o StrictHostKeyChecking=no user@94.237.54.164

# Local port forwarding: forward local port 8080 to remote host’s port 80
ssh -L 8080:localhost:80 user@94.237.54.164

# Remote port forwarding: forward remote port 2222 to local machine’s SSH port (22)
ssh -R 2222:localhost:22 user@94.237.54.164
```

# **Installation**
```bash
sudo pacman -S openssh
sudo apt install openssh-server 
sudo yum install openssh-server
```
After Installing the package, you must enable the service:
```bash
sudo systemctl enable --now sshd
```
To check if SSH is running:
```bash
sudo systemctl status ssh
```
# **Troubleshooting**
1. check if ssh is installed and running
```
sudo systemctl status sshd
sudo systemctl enable --now sshd
```
