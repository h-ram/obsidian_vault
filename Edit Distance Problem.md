### Example: Edit Distance Between "kitten" and "sitting"

We will compute the minimum edit distance between **String A = "kitten"** and **String B = "sitting"** step by step.

---

### Step 1: Initialize the DP Table

Create a table `dp` of size `(len(A) + 1) x (len(B) + 1)`. This table will hold the minimum edit distances for various substrings of `A` and `B`.

| | |s|i|t|t|i|n|g|
|---|---|---|---|---|---|---|---|---|
||0|1|2|3|4|5|6|7|
|k|1||||||||
|i|2||||||||
|t|3||||||||
|t|4||||||||
|e|5||||||||
|n|6||||||||

#### Base Cases:

1. When `A` is empty (first row), the edit distance is the length of `B` (all insertions).
2. When `B` is empty (first column), the edit distance is the length of `A` (all deletions).

| | |s|i|t|t|i|n|g|
|---|---|---|---|---|---|---|---|---|
||0|1|2|3|4|5|6|7|
|k|1||||||||
|i|2||||||||
|t|3||||||||
|t|4||||||||
|e|5||||||||
|n|6||||||||

---

### Step 2: Fill the DP Table Using Recurrence Relation

Use the following rules:

1. If `A[i-1] == B[j-1]`: No cost. $dp[i][j]=dp[i−1][j−1]$
2. Otherwise:
    
    ```
    dp[i][j] = 1 + min(dp[i-1][j], dp[i][j-1], dp[i-1][j-1])
    ```
    
    - **Insertion**: `dp[i][j-1]`
    - **Deletion**: `dp[i-1][j]`
    - **Substitution**: `dp[i-1][j-1]`

---

### Step 3: Fill Row by Row

#### First Row (Comparing "k" with "sitting")

| | |s|i|t|t|i|n|g|
|---|---|---|---|---|---|---|---|---|
||0|1|2|3|4|5|6|7|
|k|1|1|2|3|4|5|6|7|

Explanation:

- Compare "k" with each character of "sitting".
- Mismatch at each step → Increment edit distance.

---

#### Second Row (Comparing "ki" with "sitting")

| | |s|i|t|t|i|n|g|
|---|---|---|---|---|---|---|---|---|
||0|1|2|3|4|5|6|7|
|k|1|1|2|3|4|5|6|7|
|i|2|2|1|2|3|4|5|6|

Explanation:

- Compare "ki" with "sitting".
- At position "i" in both strings, they match → Take value from diagonal (`dp[1][1] = 1`).
- Other cells involve mismatches → Use recurrence relation.

---

#### Third Row (Comparing "kit" with "sitting")

| | |s|i|t|t|i|n|g|
|---|---|---|---|---|---|---|---|---|
||0|1|2|3|4|5|6|7|
|k|1|1|2|3|4|5|6|7|
|i|2|2|1|2|3|4|5|6|
|t|3|3|2|1|2|3|4|5|

Explanation:

- Match at "t" in both strings → Take diagonal value (`dp[2][2] = 1`).
- Other cells filled based on the recurrence relation.

---

#### Continue for Remaining Rows

Repeat the process for the remaining rows ("kitt", "kitte", "kitten").

Final DP Table:

|     |     | s   | i   | t   | t   | i   | n   | g   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|     | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   |
| k   | 1   | 1   | 2   | 3   | 4   | 5   | 6   | 7   |
| i   | 2   | 2   | 1   | 2   | 3   | 4   | 5   | 6   |
| t   | 3   | 3   | 2   | 1   | 2   | 3   | 4   | 5   |
| t   | 4   | 4   | 3   | 2   | 1   | 2   | 3   | 4   |
| e   | 5   | 5   | 4   | 3   | 2   | 2   | 3   | 4   |
| n   | 6   | 6   | 5   | 4   | 3   | 3   | 2   | 3   |

---

### Step 4: Extract the Result

The value in `dp[len(A)][len(B)]` is the minimum edit distance.

For "kitten" → "sitting", the minimum edit distance is **3**.

---

### Step 5: Traceback to Find Operations

1. Start at `dp[6][7]` (bottom-right corner).
2. Move backward to determine which operations were performed:
    - Diagonal: Substitution.
    - Left: Insertion.
    - Up: Deletion.

Operations:

- Substitute "k" → "s".
- Insert "i".
- Substitute "e" → "i".

# Practice

|     |     | s   | i   | t   | t   | i   | n   | g   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|     | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   |
| k   | 1   |     |     |     |     |     |     |     |
| i   | 2   |     |     |     |     |     |     |     |
| t   | 3   |     |     |     |     |     |     |     |
| t   | 4   |     |     |     |     |     |     |     |
| e   | 5   |     |     |     |     |     |     |     |
| n   | 6   |     |     |     |     |     |     |     |

|     |     | f   | l   | a   | w   |
| --- | --- | --- | --- | --- | --- |
|     | 0   | 1   | 2   | 3   | 4   |
| l   | 1   |     |     |     |     |
| a   | 2   |     |     |     |     |
| w   | 3   |     |     |     |     |

|     |     | a   | b   | c   |
| --- | --- | --- | --- | --- |
|     | 0   | 1   | 2   | 3   |
| y   | 1   |     |     |     |
| a   | 2   |     |     |     |
| b   | 3   |     |     |     |
| d   | 3   |     |     |     |

|   |   | s | u | n | d | a | y |
|---|---|---|---|---|---|---|---|
|   | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
| s | 1 |   |   |   |   |   |   |
| a | 2 |   |   |   |   |   |   |
| t | 3 |   |   |   |   |   |   |
| u | 4 |   |   |   |   |   |   |
| r | 5 |   |   |   |   |   |   |
| d | 6 |   |   |   |   |   |   |
| a | 7 |   |   |   |   |   |   |
| y | 8 |   |   |   |   |   |   |

|     |     | a   | b   | c   | d   | e   | f   |
| --- | --- | --- | --- | --- | --- | --- | --- |
|     | 0   | 1   | 2   | 3   | 4   | 5   | 6   |
| a   | 1   | 0   | 1   | 2   | 3   | 4   | 5   |
| z   | 2   | 1   | 1   | 2   | 3   | 4   | 5   |
| c   | 3   | 2   | 2   | 1   | 2   | 3   | 4   |
| e   | 4   | 3   | 3   | 2   | 2   | 2   | 3   |
| d   | 5   | 4   | 4   | 3   | 2   | 3   | 3   |
| f   | 6   | 5   | 5   | 4   | 3   | 3   | 3   |

---

Below are the solutions to each of the edit distance problems provided. The **edit distance** is computed using the dynamic programming approach to find the minimum number of insertions, deletions, or substitutions needed to convert one string into another.

---

### **Problem 1**

#### Strings: "kitten" → "sitting"

| | |s|i|t|t|i|n|g|
|---|---|---|---|---|---|---|---|---|
||0|1|2|3|4|5|6|7|
|k|1|1|2|3|4|5|6|7|
|i|2|2|1|2|3|4|5|6|
|t|3|3|2|1|2|3|4|5|
|t|4|4|3|2|1|2|3|4|
|e|5|5|4|3|2|2|3|4|
|n|6|6|5|4|3|3|2|3|

**Edit Distance**: 3  
**Explanation**: Replace 'k' → 's', replace 'e' → 'i', and add 'g'.

---

### **Problem 2**

#### Strings: "flaw" → "flaw"

| | |f|l|a|w|
|---|---|---|---|---|---|
||0|1|2|3|4|
|l|1|1|1|2|3|
|a|2|2|2|1|2|
|w|3|3|3|2|1|

**Edit Distance**: 0  
**Explanation**: The strings are identical.

---

### **Problem 3**

#### Strings: "abcd" → "abc"

| | |a|b|c|
|---|---|---|---|---|
||0|1|2|3|
|y|1|1|2|3|
|a|2|1|2|3|
|b|3|2|1|2|
|d|4|3|2|2|

**Edit Distance**: 1  
**Explanation**: Remove 'd'.

---

### **Problem 4**

#### Strings: "sunday" → "saturday"

| | |s|u|n|d|a|y|
|---|---|---|---|---|---|---|---|
||0|1|2|3|4|5|6|
|s|1|0|1|2|3|4|5|
|a|2|1|1|2|3|3|4|
|t|3|2|2|2|3|4|5|
|u|4|3|2|3|3|4|5|
|r|5|4|3|3|4|5|6|
|d|6|5|4|4|3|4|5|
|a|7|6|5|5|4|3|4|
|y|8|7|6|6|5|4|3|

**Edit Distance**: 3  
**Explanation**: Add 'a', add 't', and add 'r'.

---

### **Problem 5**

#### Strings: "azced" → "abcdef"

| | |a|b|c|d|e|f|
|---|---|---|---|---|---|---|---|
||0|1|2|3|4|5|6|
|a|1|0|1|2|3|4|5|
|z|2|1|1|2|3|4|5|
|c|3|2|2|1|2|3|4|
|e|4|3|3|2|2|1|2|
|d|5|4|4|3|2|2|2|
|f|6|5|5|4|3|3|2|

**Edit Distance**: 3  
**Explanation**: Replace 'z' → 'b', add 'f', and replace 'e' → 'c'.

---

Let me know if you need further clarification or detailed steps for solving these problems!
