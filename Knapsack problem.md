# Simplified Explanation of the Knapsack Problem

### **Problem**
You have:
- A **knapsack** with a maximum weight it can carry (capacity `W`).
- A list of **items**, where each item has:
  - A **weight** (e.g., how heavy it is).
  - A **value** (e.g., how valuable it is).

You want to figure out:  
**What is the maximum value you can carry in the knapsack without exceeding its weight limit?**

---

### **Approach**
We solve this using **Dynamic Programming (DP)**. The idea is to break the problem into smaller sub-problems and build a table that helps us keep track of the best solution at every step.

---

### **Step-by-Step Explanation**

#### 1. Define the DP Table  
We create a table `dp[i][j]`:
- `i` is the number of items we consider.
- `j` is the current capacity of the knapsack.

Each cell `dp[i][j]` tells us:  
**What is the maximum value we can get using the first `i` items with a knapsack capacity of `j`?**

#### Example:  
Let’s say we have 4 items with these weights and values:
- `weights = [1, 3, 4, 5]`
- `values = [1, 4, 5, 7]`
And the knapsack capacity is `W = 7`.

We initialize a table of size `(n+1) x (W+1)`, where `n` is the number of items. It will look like this at the start (all 0s because we haven't done any calculations yet):

| i\w | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|-----|---|---|---|---|---|---|---|---|
| 0   | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 1   | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 2   | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 3   | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 4   | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

Here:
- Rows represent items (0 means no items, 1 means the first item, etc.).
- Columns represent knapsack capacities (0 means no capacity, 1 means capacity 1, etc.).

---

#### 2. Base Case  
If we don’t consider any items (`i = 0`) or the knapsack has no capacity (`j = 0`), the maximum value is **0**.  
This is why the first row and first column remain **0**.

---

#### 3. Filling the DP Table  

We process each item one by one and check for every possible knapsack capacity (`j`) whether to **include** or **exclude** the item.

### Case 1: **Exclude the item**  
If the current capacity `j` is less then the current items weight `weights[i-1]` we don’t include the item, the value at `dp[i][j]` is the same as the previous row:  
`dp[i][j] = dp[i-1][j]`

### Case 2: **Include the item**  
If the item’s weight (`weights[i-1]`) is less than or equal to the current capacity `j`, we have two options:
1. **Exclude the item**: Keep the same value as before: `dp[i-1][j]`.
2. **Include the item**: Add the value of the item (`values[i-1]`) to the value of the remaining capacity (`dp[i-1][j - weights[i-1]]`).

Take the maximum of these two:
`dp[i][j] = max(dp[i-1][j], dp[i-1][j - weights[i-1]] + values[i-1])`

---

### **Example Walkthrough**

We’ll fill the table step by step for each item.

---

#### **Item 1 (weight = 1, value = 1)**  

We go through capacities `j = 1` to `j = 7`:

- At `j = 1`:  
  The weight of item 1 (1) ≤ capacity (1).  
  `dp[1][1] = max(dp[0][1], dp[0][0] + 1) = max(0, 0 + 1) = 1`
- At `j = 2`:  
  Same logic. Include the item.  
  `dp[1][2] = max(dp[0][2], dp[0][1] + 1) = 1`

After processing item 1, the table looks like this:

| i\w | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|-----|---|---|---|---|---|---|---|---|
| 0   | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 1   | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |

---

#### **Item 2 (weight = 3, value = 4)**  

We go through capacities `j = 1` to `j = 7`:

- At `j = 1` and `j = 2`:  
  The weight of item 2 (3) > capacity (1 or 2). So, we can’t include it.  
  `dp[2][1] = dp[1][1] = 1`  
  `dp[2][2] = dp[1][2] = 1`

- At `j = 3`:  
  The weight of item 2 (3) ≤ capacity (3).  
  `dp[2][3] = max(dp[1][3], dp[1][0] + 4) = max(1, 0 + 4) = 4`

- At `j = 4`:  
  Include item 2:  
  `dp[2][4] = max(dp[1][4], dp[1][1] + 4) = max(1, 1 + 4) = 5`

After processing item 2, the table looks like this:

| i\w | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|-----|---|---|---|---|---|---|---|---|
| 0   | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 1   | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 2   | 0 | 1 | 1 | 4 | 5 | 5 | 5 | 5 |

---

#### **Item 3 (weight = 4, value = 5)**  

Follow the same logic for `j = 1` to `j = 7`. After processing, the table becomes:

| i\w | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|-----|---|---|---|---|---|---|---|---|
| 0   | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 1   | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 2   | 0 | 1 | 1 | 4 | 5 | 5 | 5 | 5 |
| 3   | 0 | 1 | 1 | 4 | 5 | 6 | 6 | 9 |

---

#### **Item 4 (weight = 5, value = 7)**  

Finally, process item 4. The completed table looks like this:

| i\w | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|-----|---|---|---|---|---|---|---|---|
| 0   | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 1   | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| 2   | 0 | 1 | 1 | 4 | 5 | 5 | 5 | 5 |
| 3   | 0 | 1 | 1 | 4 | 5 | 6 | 6 | 9 |
| 4   | 0 | 1 | 1 | 4 | 5 | 7 | 8 | 9 |

---

### **Result**

The maximum value you can achieve with a capacity of `7` is in `dp[4][7]`, which is **9**.

---

### **Recap**

1. Build a DP table to track the maximum value for each capacity.
2. For each item and capacity, decide whether to include or exclude the item.
3. The bottom-right corner of the table gives the final answer.

Determining which items actually go into the knapsack requires **backtracking** after filling out the DP table. Here's how you can figure it out step by step:

---

### 1. **Start from the last cell of the DP table**

The value in the bottom-right corner of the table (`dp[n][W]`, where `n` is the number of items and `W` is the capacity) represents the **maximum value** you can achieve.

### 2. **Trace back through the table**

To find which items are included, compare the value of `dp[i][j]` with the value of `dp[i-1][j]`:

- If `dp[i][j] == dp[i-1][j]`:  
    The item `i` was **not included**. Move to the previous row (`i-1`).
- If `dp[i][j] != dp[i-1][j]`:  
    The item `i` was **included**. Subtract the item's weight from the current capacity (`j -= weight[i-1]`), and move to the previous row (`i-1`).

### 3. **Stop when you reach the first row or capacity is 0**

Once you've worked your way back to the first row (`i = 0`) or the remaining capacity becomes 0, you've identified all the items that go into the knapsack.

---
# Practice
- `weights = [1, 3, 4, 5]` - `values = [1, 4, 5, 7]`

| i\w | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
| 1   | 0   |     |     |     |     |     |     |     |
| 2   | 0   |     |     |     |     |     |     |     |
| 3   | 0   |     |     |     |     |     |     |     |
| 4   | 0   |     |     |     |     |     |     |     |
Here are three more knapsack problems for practice, along with their solutions at the bottom:

---

### **Problem 1**

- **Weights**: `[2, 3, 4, 5]`
- **Values**: `[3, 4, 5, 6]`
- **Knapsack Capacity**: `7`

#### Table Layout:

| i\w | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   |
| 1   | 0   |     |     |     |     |     |     |     |
| 2   | 0   |     |     |     |     |     |     |     |
| 3   | 0   |     |     |     |     |     |     |     |
| 4   | 0   |     |     |     |     |     |     |     |

---

### **Problem 2**

- **Weights**: `[1, 2, 3]`
- **Values**: `[6, 10, 12]`
- **Knapsack Capacity**: `5`

#### Table Layout:

| i\w | 0   | 1   | 2   | 3   | 4   | 5   |
| --- | --- | --- | --- | --- | --- | --- |
| 0   | 0   | 0   | 0   | 0   | 0   | 0   |
| 1   | 0   |     |     |     |     |     |
| 2   | 0   |     |     |     |     |     |
| 3   | 0   |     |     |     |     |     |

---

### **Problem 3**

- **Weights**: `[1, 4, 3, 5]`
- **Values**: `[2, 5, 7, 8]`
- **Knapsack Capacity**: `6`

#### Table Layout:

|i\w|0|1|2|3|4|5|6|
|---|---|---|---|---|---|---|---|
|0|0|0|0|0|0|0|0|
|1|0|||||||
|2|0|||||||
|3|0|||||||
|4|0|||||||

---

### **Solutions**

#### **Problem 1**

- Maximum value: `9`
- Items included: `[3, 4]` (weights: `[3, 4]`)

#### **Problem 2**

- Maximum value: `22`
- Items included: `[10, 12]` (weights: `[2, 3]`)

#### **Problem 3**

- Maximum value: `15`
- Items included: `[7, 8]` (weights: `[3, 5]`)

Let me know if you'd like a detailed explanation for solving any specific problem!