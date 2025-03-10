**GNU Readline** is a **library** that provides **line editing, history recall, and auto-completion** in command-line interfaces (CLI), such as Bash and other shells. It allows users to efficiently edit and navigate commands using keyboard shortcuts.

---
# **1. Line Editing**
Readline supports **two editing modes**:
1. **Emacs Mode (default)** →  uses [[Emacs|Emacs Shortcuts]] .
2. **Vi Mode** → Uses vi keybinds (`set -o vi`).
---
- **Cursor Movement**
    - `Ctrl + A` → Move to the beginning of the line
    - `Ctrl + E` → Move to the end of the line
    - `Ctrl + B` → Move back one character (same as left arrow)
    - `Ctrl + F` → Move forward one character (same as right arrow)
    - `Alt + B` → Move back one word
    - `Alt + F` → Move forward one word
	- `Ctrl-l` → Clear the screen
- **Editing and Deletion**
    - `Ctrl + U` → Delete everything before the cursor
    - `Ctrl + K` → Delete everything after the cursor
    - `Ctrl + W` → Delete the previous word
    - `Ctrl + D` → Delete the character under the cursor
	- `Ctrl + Y` → **Paste (yank) last deleted text**
	- `Alt + Y` → Cycle through previously deleted items
    - `Backspace` → Delete the character before the cursor
	- `Ctrl + _` → **Undo** last change (must hold SHIFT)
	- `Ctrl + X Ctrl + E` → Open the command in the **default text editor**

---
# **2. Command History**
- `Ctrl + P` →Previous command (same as up arrow)
- `Ctrl + N` →Next command (same as down arrow)
- `Ctrl + R` → Search command history (R -> Reverse Search)
- `Ctrl + G` → Cancel history search  (G -> Give up search)
- `Alt + .` → Insert **last word** from the previous command
- `!!` → Repeat last command
- `!xyz` → Run the **last command that started with `xyz`**
- `^old^new` → Replace `old` with `new` in the last command and execute
---
# **3. Auto-Completion**
- `Tab` Auto-complete filenames, commands, or variables
- `Alt + ?` Show **all possible completions**
- `Alt + *` Insert all possible completions at once
- `Alt + /` Complete **filename**
---
# **Readline Configuration**
You can list enabled options:
```bash
$ set -o
emacs          	on
histexpand     	on
history        	on
vi off
...SNIP...
```
To switch to Vi mode:
```sh
set -o vi
```
To switch back to Emacs mode:
```sh
set -o emacs
```
You can put all your configurations in `~/.inputrc`

---
# **Readline in Different Shells**
- **Bash** – Uses Readline by default.
- **Zsh** – Uses a different system (`zle`), but can emulate Readline.
- **Fish Shell** – Does **not** use Readline but has its own keybindings.

---
Resrouces: 
- https://readline.kablamo.org/emacs.html