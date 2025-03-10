### Explanation of Longest Common Subsequence (LCS) Using Dynamic Programming

The **Longest Common Subsequence (LCS)** problem is about finding the longest sequence that appears in the same order in two given strings but may not be contiguous. Let's break down the steps with examples and tables to simplify the concept:

---
### 1. **Define a DP Table**
We define a 2D table `dp[i][j]`, where:
- `i` represents the first `i` characters of string `X`.
- `j` represents the first `j` characters of string `Y`.
- The value of `dp[i][j]` represents the length of the LCS of the first `i` characters of `X` and the first `j` characters of `Y`.
---

### 2. **Recurrence Relation**

To fill the `dp` table:
1. If the characters `X[i-1]` and `Y[j-1]` match, then:
   $dp[i][j] = dp[i-1][j-1] + 1$
   This means that the LCS includes this matching character.

2. If the characters do not match:
   $dp[i][j] = \max(dp[i-1][j], dp[i][j-1])$
   This means we carry forward the maximum LCS length from the previous rows or columns.

---

### 3. **Initialization**

- `dp[0][j] = 0` for all `j`: An empty sequence compared to any part of `Y` has an LCS of length 0.
- `dp[i][0] = 0` for all `i`: Any part of `X` compared to an empty sequence has an LCS of length 0.

---

### 4. **Example Walkthrough**

Let’s calculate the LCS for:
- `X = "ABCBDAB"`
- `Y = "BDCAB"`

#### Step 1: Initialize the Table

Create a `dp` table of size `(len(X)+1) x (len(Y)+1)`, initializing all entries to 0.

|     |     | B   | D   | C   | A   | B   |
| --- | --- | --- | --- | --- | --- | --- |
|     | 0   | 0   | 0   | 0   | 0   | 0   |
| A   | 0   | 0   | 0   | 0   | 0   | 0   |
| B   | 0   | 0   | 0   | 0   | 0   | 0   |
| C   | 0   | 0   | 0   | 0   | 0   | 0   |
| B   | 0   | 0   | 0   | 0   | 0   | 0   |
| D   | 0   | 0   | 0   | 0   | 0   | 0   |
| A   | 0   | 0   | 0   | 0   | 0   | 0   |
| B   | 0   | 0   | 0   | 0   | 0   | 0   |

---

#### Step 2: Fill the Table Using the Recurrence Relation

Start from `dp[1][1]` and fill row by row:

1. Compare `A` (from `X`) with `B` (from `Y`): No match, so:
   $dp[1][1] = \max(dp[0][1], dp[1][0]) = 0$
2. Compare `A` with `D`, `C`, `A`, and `B`, filling the row similarly.

|     |     | B   | D   | C   | A   | B   |
| --- | --- | --- | --- | --- | --- | --- |
|     | 0   | 0   | 0   | 0   | 0   | 0   |
| A   | 0   | 0   | 0   | 0   | 1   | 1   |
| B   | 0   | 1   | 1   | 1   | 1   | 2   |
| C   | 0   | 1   | 1   | 2   | 2   | 2   |
| B   | 0   | 1   | 1   | 2   | 2   | 3   |
| D   | 0   | 1   | 2   | 2   | 2   | 3   |
| A   | 0   | 1   | 2   | 2   | 3   | 3   |
| B   | 0   | 1   | 2   | 2   | 3   | 4   |

---

#### Step 3: Trace Back to Construct the LCS

Start at `dp[7][5]` (bottom-right corner) and trace back:

- If `X[i-1] == Y[j-1]`, include the character in the LCS and move diagonally (`i-1`, `j-1`).
- Otherwise, move in the direction of the larger value (`i-1, j` or `i, j-1`).

**Tracing Steps:**
1. `dp[7][5]`: `X[6] == Y[4]` (`B`), add `B`, move to `dp[6][4]`.
2. `dp[6][4]`: `X[5] == Y[3]` (`A`), add `A`, move to `dp[5][3]`.
3. `dp[5][3]`: `X[4] == Y[2]` (`C`), add `C`, move to `dp[3][2]`.
4. `dp[3][2]`: `X[2] == Y[0]` (`B`), add `B`, stop.

LCS: `BCAB` (reverse the sequence).

---

### 5. **Code Implementation**

The code provided constructs the table and traces back efficiently, producing:
- **Length of LCS**: `4`
- **LCS**: `BCAB`

---

### Key Takeaways:
- The DP table stores intermediate results for efficient computation.
- Tracing back helps construct the actual LCS.
- LCS problems are widely used in bioinformatics, text comparison, and data analysis.
---
# Practice
Let’s calculate the LCS for:
- `X = "ABCBDAB"`
- `Y = "BDCAB"`

|     |     | B   | D   | C   | A   | B   |
| --- | --- | --- | --- | --- | --- | --- |
|     | 0   | 0   | 0   | 0   | 0   | 0   |
| A   | 0   | 0   | 0   | 0   | 0   | 0   |
| B   | 0   | 0   | 0   | 0   | 0   | 0   |
| C   | 0   | 0   | 0   | 0   | 0   | 0   |
| B   | 0   | 0   | 0   | 0   | 0   | 0   |
| D   | 0   | 0   | 0   | 0   | 0   | 0   |
| A   | 0   | 0   | 0   | 0   | 0   | 0   |
| B   | 0   | 0   | 0   | 0   | 0   | 0   |
Here are three more LCS problems with their solutions at the bottom:

---

### **Problem 1**
 X = "AGGTAB"
 Y = "GXTXAYB"

|     |     | G   | X   | T   | X   | A   | Y   | B   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|     | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
| A   | 0   |     |     |     |     |     |     |     |
| G   | 0   |     |     |     |     |     |     |     |
| G   | 0   |     |     |     |     |     |     |     |
| T   | 0   |     |     |     |     |     |     |     |
| A   | 0   |     |     |     |     |     |     |     |
| B   | 0   |     |     |     |     |     |     |     |

---

### **Problem 2**
 X = "ACADB"
 Y = "CBDA"

|     |     | C   | B   | D   | A   |
| --- | --- | --- | --- | --- | --- |
|     | 0   | 0   | 0   | 0   | 0   |
| A   | 0   |     |     |     |     |
| C   | 0   |     |     |     |     |
| A   | 0   |     |     |     |     |
| D   | 0   |     |     |     |     |
| B   | 0   |     |     |     |     |

---
### **Problem 3**
 X = "XMJYAUZ"
 Y = "MZJAWXU"

| | |M|Z|J|A|W|X|U|
|---|---|---|---|---|---|---|---|---|
||0|0|0|0|0|0|0|0|
|X|0||||||||
|M|0||||||||
|J|0||||||||
|Y|0||||||||
|A|0||||||||
|U|0||||||||
|Z|0||||||||

---

### **Solutions**

#### **Solution to Problem 1**

- **LCS**: "GTAB"
- **Length**: 4

#### **Solution to Problem 2**

- **LCS**: "CBA"
- **Length**: 3

#### **Solution to Problem 3**

- **LCS**: "MJAU"
- **Length**: 4

---

Let me know if you'd like me to fill out any specific DP table or explain steps!