#command 
**tmux (Terminal Multiplexer)** allows you to **run multiple terminal sessions within a single window**. It is useful for managing multiple tasks in a single terminal, keeping sessions running after disconnecting, and organizing workflows efficiently.

---
### **Key Features of tmux**
1. **Session Persistence** – Keeps terminal sessions active even if you disconnect (useful for SSH sessions).
2. **Multiple Panes** – Split a terminal window into multiple sections.
3. **Multiple Windows** – Open multiple terminal windows within a single tmux session.
4. **Session Management** – Attach, detach, and switch between sessions easily.
5. **Customizable** – Supports configuration via `~/.tmux.conf`.
---
### **Basic tmux Commands**
```bash
#start tmux
tmux

#start tmux with a session name
tmux new -s mysession

#list active sessions
tmux list-sessions

#detach from a sessions
(CTRL + B) + D

#Reattache to a Session
tmux attach -t mysession

#Reattache to last session
tmux attach

#Kill Session
tmux attach

#Kill all Sessions
tmux kill-server
```

---
### **Window & Pane Management**
```
[CTRL + B] + c                  # Create new window
[CTRL + B] + (0-9)              # Switch between windows
[CTRL + B] + %                  # Split Horizontally
[CTRL + B] + "                  # Split Vertically
[CTRL + B] + B                  # Swtich Between Panes
[CTRL + B] + [CTRL + Arrow_key] # Resize Pane
[CTRL + B] + x                  # Close Pane
```

---
### **Configuration**
Customize tmux by editing `~/.tmux.conf`. Example:
```bash
set -g mouse on  # Enable mouse support
set -g status-bg blue  # Change status bar color
```
Apply changes:
```bash
tmux source-file ~/.tmux.conf
```
---
### Resources
- [Online Cheatsheet](https://tmuxcheatsheet.com/)