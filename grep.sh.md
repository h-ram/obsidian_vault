#command #gnu_coreutils 

`grep` (**global regular expression print**) is a command used to search for **patterns** (text or [[Regular  Expressions (regex)|regular expressions]]) in files or output streams. It prints matching lines and is useful for filtering logs, finding specific content in files, and processing text data.
```bash
grep [OPTIONS] PATTERN [FILE...]
```
- **PATTERN** → The text or regex you are searching for.
- **FILE** → The file(s) to search in. If omitted, `grep` reads from standard input (`stdin`).
---
# **Usage**

```bash
# Search for a Word in a File
grep "error" log.txt

# Case-Insensitive Search (-i)
grep -i "error" log.txt

# Search in Multiple Files
grep "error" file1.txt file2.txt

# Display Line Numbers (-n)
grep -n "failed" auth.log

# Invert Match (-v)
grep -v "success" log.txt  # lines that do NOT contain "success".

# Count Matches (-c)
grep -c "error" log.txt    # Outputs how many times "error" appears

# Match Whole Words (-w)
grep -w "root" /etc/passwd # Matches "root" but not "rootuser"

# Search Recursively (-r)
grep -r "TODO" /home/user/ # Searches for "TODO" in all files inside `/home/user/` (including subdirectories)

# Show N Lines Before Match (-B)
grep -B 2 "error" log.txt # Shows 2 lines before each match.

# Show N Lines After Match (-A)
grep -A 3 "failed" log.txt # Shows 3 lines after each match.

# Show N Lines Before & After Match (-C)
grep -C 2 "critical" log.txt

# Highlight Matches (--color)
grep --color=auto "warning" log.txt

# Ignore Binary Files (-I)
grep -I "error" /var/log/*

# Search Only File Names (-l)
grep -l "TODO" *.txt

# Show Only Matches (-o)
grep -o "user[0-9]" users.txt

# Recursive Search in Specific File Types (--include)
grep -r --include="*.log" "error" /var/log/

# Exclude Specific Files (--exclude)
grep -r --exclude="debug.log" "error" /var/log/
```
Usually we'll be pipping some output to `grep` instead of actually using the command byitself
```bash
#Example
cat file.txt | grep "error"
```
---
# **Options**

| Option                    | Description                             |
| ------------------------- | --------------------------------------- |
| `-i`, `--ignore-case`     | Case-insensitive search                 |
| `-n`, `--line-number`     | Show line numbers                       |
| `-v`, `--invert-match`    | Invert match (exclude lines)            |
| `-c`, `--count`           | Count matches                           |
| `-w`, `--word-regexp`     | Match whole words                       |
| `-r`                      | Search recursively in directories       |
| `-B N`                    | Show `N` lines before match             |
| `-A N`                    | Show `N` lines after match              |
| `-C N`                    | Show `N` lines before & after           |
| `-o`                      | Show only matched text                  |
| `-l`                      | List file names with matches            |
| `-I`                      | Ignore binary files                     |
| `--color`                 | Highlight matches                       |
| `-E`, `--extended-regexp` | Use Extended Regex (ERE) instead of BRE |
| `-P`, `--pearl-regexp`    | Use PCRE                                |

---
# **Regular Expressions** 
The default `grep` command uses [[Regular  Expressions (regex)#Basic Regex (BRE)|Basic Regex (BRE)]], but by using the `-E` option we can use ERE (Extended Regular Expressions )

---
# **`egrep` (Extended `grep`)**
Using `egrep` is the equivilant to `grep -E`

```bash
egrep "error|fail|critical" log.txt
```

- Matches **any** of `"error"`, `"fail"`, or `"critical"`.

---



