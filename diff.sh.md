#command #gnu_coreutils 

 `diff` is a [[GNU Core Utilities (coreutils)|coreutils]] command used to compare files line by line. It helps identify differences between text files and directories.
```sh
diff [OPTIONS] file1 file2
```
---
# **Options**
| **Option**                       | **Description**                                                |
| -------------------------------- | -------------------------------------------------------------- |
| `-q`, `--brief`                  | Show only whether files differ (no detailed output).           |
| `-s`, `--report-identical-files` | Report if files are identical.                                 |
| `-y`, `--side-by-side`           | Display output in a side-by-side format.                       |
| `--left-column`                  | In `-y` mode, show differing lines only in the left column.    |
| `-i`, `--ignore-case`            | Ignore case differences.                                       |
| `-b`, `--ignore-space-change`    | Ignore changes in the number of spaces.                        |
| `-w`, `--ignore-all-space`       | Ignore all white spaces.                                       |
| `-B`, `--ignore-blank-lines`     | Ignore blank lines.                                            |
| `-r`, `--recursive`              | Recursively compare directories.                               |
| `-c`, `--context[=NUM]`          | Show output in context format (default 3 lines).               |
| `-u`, `--unified[=NUM]`          | Show output in unified format (default 3 lines).               |
| `--strip-trailing-cr`            | Ignore carriage return (`\r`) differences.                     |
| `--color[=WHEN]`                 | Highlight differences in color (`always`, `never`, `auto`).    |
| `--suppress-common-lines`        | In `-y` mode, hide identical lines.                            |
| `--from-file=FILE`               | Compare multiple files against one reference file.             |
| `--to-file=FILE`                 | Compare a single file against multiple files.                  |
| `--new-file`                     | Treat missing files as empty.                                  |
| `--normal`                       | Output differences in the default normal format.               |
| `-N`, `--new-file`               | Treat absent files as empty (useful for directory comparison). |


# **Usage**
Consider two files:
```
file1                           file2
-------------------------------|------------------------------
Hello There                    | Hello There
Your momma fat                 | Your dad homo
Your sis ugly                  | Your bro Handsome
You short                      | You tall
This line is the same          | This line is the same
Bye :<                         | Bye :)
```

```sh
$ diff file1 file2
2,4c2,4
< Your momma fat
< Your sis ugly
< You short
---
> Your dad homo
> Your bro handsome
> You tall
6c6
< Bye :<
---
> Bye :)
```
### **Only Check If Different (-q)**
```bash
$ diff -q file1 file2
Files file1 and file2 differ

# If they were the same, no output will be displayed
```
---
### **Side-by-Side Comparison (-y)**
```sh
$diff -y file1.txt file2.txt
Hello There                 Hello There
Your momma fat            | Your dad homo
Your sis ugly             | Your bro handsome
You short                 | You tall
This line is the same       This line is the same
Bye :<		              | Bye :)
# | indicates differences.
```
### **Context Mode (-c)**
```sh
$ diff -c file1 file2
*** file1	2025-02-18 12:48:36.734899880 +0100
--- file2	2025-02-18 12:48:43.184900095 +0100
***************
*** 1,6 ****
  Hello There
! Your momma fat
! Your sis ugly
! You short
  This line is the same
! Bye :<
--- 1,6 ----
  Hello There
! Your dad homo
! Your bro handsome
! You tall
  This line is the same
! Bye :)
```

---
### **Unified Mode (-u)**
```sh
$ diff -u file1 file2
--- file1	2025-02-18 12:48:36.734899880 +0100
+++ file2	2025-02-18 12:48:43.184900095 +0100
@@ -1,6 +1,6 @@
 Hello There
-Your momma fat
-Your sis ugly
-You short
+Your dad homo
+Your bro handsome
+You tall
 This line is the same
-Bye :<
+Bye :)
```