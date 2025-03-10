#command 

## **1. File and Buffer Management**

|Shortcut|Action|
|---|---|
|`Ctrl + x, Ctrl + f`|Open a file|
|`Ctrl + x, Ctrl + s`|Save the file|
|`Ctrl + x, Ctrl + w`|Save file with a new name|
|`Ctrl + x, Ctrl + c`|Exit Emacs|
|`Ctrl + x, k`|Kill (close) current buffer|
|`Ctrl + x, b`|Switch buffers|
|`Ctrl + x, Ctrl + b`|Show buffer list|
|`Ctrl + x, s`|Save all buffers|

---
## **2. Cursor Navigation**

| Shortcut   | Action                                |
| ---------- | ------------------------------------- |
| `Ctrl + f` | Move forward (right) one character    |
| `Ctrl + b` | Move backward (left) one character    |
| `Alt + f`  | Move forward one word                 |
| `Alt + b`  | Move backward one word                |
| `Ctrl + a` | Move to the beginning of the line     |
| `Ctrl + e` | Move to the end of the line           |
| `Ctrl + n` | Move to the next line                 |
| `Ctrl + p` | Move to the previous line             |
| `Alt + a`  | Move to the beginning of the sentence |
| `Alt + e`  | Move to the end of the sentence       |
| `Alt + {`  | Move to the beginning of a paragraph  |
| `Alt + }`  | Move to the end of a paragraph        |
| `Ctrl + v` | Scroll down one screen                |
| `Alt + v`  | Scroll up one screen                  |
| `Alt + <`  | Jump to the beginning of the buffer   |
| `Alt + >`  | Jump to the end of the buffer         |
| `Ctrl + l` | Center the cursor in the window       |

---
## **3. Editing Text**

|Shortcut|Action|
|---|---|
|`Ctrl + d`|Delete the character under the cursor|
|`Ctrl + h` or `Backspace`|Delete the character before the cursor|
|`Alt + d`|Delete the next word|
|`Alt + Backspace`|Delete the previous word|
|`Ctrl + k`|Kill (cut) from the cursor to the end of the line|
|`Alt + k`|Kill (cut) to the end of the sentence|
|`Ctrl + u, Ctrl + k`|Kill (cut) the whole line|
|`Ctrl + w`|Kill (cut) the selected region|
|`Alt + w`|Copy (kill-ring-save) the selected region|
|`Ctrl + y`|Yank (paste) the last cut/copied text|
|`Alt + y`|Cycle through the kill ring (previous yanks)|
|`Ctrl + x, u` or `Ctrl + /`|Undo last change|
|`Alt + u`|Convert word to UPPERCASE|
|`Alt + l`|Convert word to lowercase|
|`Alt + c`|Capitalize the word|
|`Ctrl + t`|Transpose (swap) two characters|
|`Alt + t`|Transpose (swap) two words|
|`Ctrl + x, Ctrl + t`|Transpose (swap) two lines|

---
## **4. Searching and Replacing**

|Shortcut|Action|
|---|---|
|`Ctrl + s`|Search forward (incremental)|
|`Ctrl + r`|Search backward (incremental)|
|`Alt + %`|Find and replace|

---
## **5. Windows and Frames (Splits)**

|Shortcut|Action|
|---|---|
|`Ctrl + x, 2`|Split window horizontally|
|`Ctrl + x, 3`|Split window vertically|
|`Ctrl + x, 1`|Close all other windows|
|`Ctrl + x, 0`|Close the current window|
|`Ctrl + x, o`|Move to the next split window|
|`Ctrl + x, ^`|Increase window height|
|`Ctrl + x, }`|Increase window width|
|`Ctrl + x, {`|Decrease window width|

---
## **6. Working with Regions (Selections)**

|Shortcut|Action|
|---|---|
|`Ctrl + Space`|Set mark (start selection)|
|`Ctrl + x, h`|Select all|
|`Alt + h`|Select current paragraph|

---
## **7. Working with Shell and Terminal**

|Shortcut|Action|
|---|---|
|`Alt + x, shell`|Open a shell inside Emacs|
|`Alt + x, eshell`|Open Emacs' built-in shell|
|`Alt + !`|Run shell command|
|`Alt + &`|Run shell command in the background|

---
## **8. Running and Debugging Code**

|Shortcut|Action|
|---|---|
|`Alt + x, compile`|Run compilation command|
|`Alt + x, recompile`|Re-run the last compilation command|

---
## **9. Working with Tabs (Buffers)**

|Shortcut|Action|
|---|---|
|`Ctrl + x, b`|Switch to another buffer|
|`Ctrl + x, Ctrl + b`|List all buffers|
|`Ctrl + x, k`|Kill (close) the current buffer|

---
## **10. Org-mode Shortcuts**

|Shortcut|Action|
|---|---|
|`Alt + x, org-mode`|Activate Org-mode|
|`Ctrl + c, Ctrl + e`|Export an Org file|
|`Ctrl + c, Ctrl + t`|Toggle TODO state|
|`Ctrl + c, Ctrl + s`|Schedule a task|

---
## **11. Emacs Help System**

|Shortcut|Action|
|---|---|
|`Ctrl + h, ?`|Open help menu|
|`Ctrl + h, k`|Describe a keybinding|
|`Ctrl + h, f`|Describe a function|
|`Ctrl + h, v`|Describe a variable|
|`Ctrl + h, t`|Start the Emacs tutorial|

---
## **12. Exiting Emacs**

|Shortcut|Action|
|---|---|
|`Ctrl + x, Ctrl + c`|Save and exit Emacs|
|`Ctrl + g`|Cancel current command|

---
## **13. Fun and Easter Eggs**

|Shortcut|Action|
|---|---|
|`Alt + x, tetris`|Play Tetris in Emacs|
|`Alt + x, doctor`|Talk to an AI therapist|
|`Alt + x, snake`|Play Snake game|

---
# **Installation**
```bash
sudo pacman -S emacs
sudo apt install emacs
sudo dnf install emacs
sudo zypper install emacs
sudo apk add emacs
brew install emacs
```