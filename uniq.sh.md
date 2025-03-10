#command #gnu_coreutils 

A [[GNU Core Utilities (coreutils)|coreutils]] command used to  **filter out adjacent duplicate lines** from a file or input stream. It works only on **sorted** or **consecutive** duplicate lines, meaning you should often use it with `sort` first.
```bash
uniq [OPTIONS] [INPUT_FILE] [OUTPUT_FILE]
```
If no file is specified, `uniq` reads from **stdin**.

---
# **Usage**
```bash
# Remove Adjacent Duplicates
uniq file.txt
cat file.txt | uniq

# Show Only Duplicates (-d)
uniq -d file.txt

# Show Unique Lines (-u)
uniq -u file.txt

# Count Repeated Adjacent Lines (-c)
uniq -c file.txt

# Ignore Case (-i)
uniq -i file.txt

# Sort Before Using uniq
sort file.txt | uniq
```

> [!NOTE] NOTE
> Since `uniq` only removes **adjacent** duplicates, you should sort first

---
# **Options**

| Option   | Alternative       | Description                               |
| -------- | ----------------- | ----------------------------------------- |
| `-d`     | `--repeated`      | Show only duplicated lines                |
| `-u`     | `unique`          | Show only unique lines                    |
| `-c`     | `--count`         | Count occurrences of each line            |
| `-i`     | `--ignore-case`   | Ignore case differences                   |
| `-s`     | `--skip-chars=N`  | Avoid comparing the first N characters    |
| `-w`     | `--check-chars=N` | Compare nomore than N characters in lines |
| `--help` |                   | Show help menu                            |
# **Example**
Let there be file.txt
```
apple
banana
banana
apple
orange
orange
orange
banana
```
Here are some example commands
```bash
$ uniq file.txt
apple
banana
apple
orange
banana
```

```bash
$ uniq -d file.txt
banana
orange
```

```bash
$ uniq -u file.txt
apple
apple
banana
```

```bash
$ uniq -c file.txt
1 apple
2 banana
1 apple
3 orange
1 banana
```

```bash
$ sort file.txt | uniq -c
2 apple
3 banana
3 orange
```