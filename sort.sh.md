#command #gnu_coreutils 


`sort` is a [[GNU Core Utilities (coreutils)|coreutils]] command used to **sort lines of text files**. By default, it sorts in **ascending order** (A-Z, 0-9).
```sh
sort [OPTIONS] [FILE]
```
If no file is specified, `sort` reads from **standard input (stdin)**.

---
# **Options**

|**Option**|**Description**|
|---|---|
|`-r`|Reverse order (descending)|
|`-n`|Sort numerically (e.g., `2 < 10`, not `10 < 2`)|
|`-h`|Human-readable numeric sort (`1K < 2M < 3G`)|
|`-f`|Ignore case (`a == A`)|
|`-u`|Unique lines (removes duplicates)|
|`-o file`|Output to a file instead of stdout|
|`-c`|Check if a file is already sorted|
|`-b`|Ignore leading spaces|
|`-V`|Natural version sort (`file1 < file2 < file10`)|
|`-M`|Sort by month names (`Jan < Feb < Mar`)|

---
# **Examples**

```bash
# Sorting Alphabetically
$ cat names.txt
banana
apple
cherry

$ sort names.txt
apple
banana
cherry

# Sorting in Reverse Order
$ sort -r names.txt
cherry
banana
apple

# Sorting Numerically
$ cat numbers.txt
10
2
5
1

$ sort -n numbers.txt
1
2
5
10

# Sorting Numerically Without -n (Lexicographically)
$ sort numbers.txt
1
10
2
5

# Sorting Human-Readable Sizes
$ cat sizes.txt
1K
500M
2G
100M

$ sort -h sizes.txt
1K
100M
500M
2G

# Sorting by Month Names
$ cat months.txt
April
January
March
February

$ sort -M months.txt
January
February
March
April

# Sorting by Column (Field-Based Sorting)
$ cat scores.txt
Alice  95
Bob    88
Charlie 100

$ sort -k2 scores.txt
Bob    88
Alice  95
Charlie 100

# Sorting Numerically by Column
$ sort -k2 -n scores.txt
Bob    88
Alice  95
Charlie 100

# Sorting Unique Lines
$ cat duplicates.txt
apple
banana
apple
cherry
banana

$ sort -u duplicates.txt
apple
banana
cherry

# Checking if a File is Sorted
$ sort -c names.txt
(sort: names.txt: disorder: banana)

# Sorting and Saving Output
$ sort -o sorted.txt names.txt
$ cat sorted.txt
apple
banana
cherry

# Natural Version Sorting
$ cat versions.txt
file1
file10
file2
file20

$ sort -V versions.txt
file1
file2
file10
file20

# Sorting by Third Column, Numerically, in Descending Order
$ cat data.txt
A 5 100
B 2 200
C 3 50

$ sort -k3 -n -r data.txt
B 2 200
A 5 100
C 3 50
```