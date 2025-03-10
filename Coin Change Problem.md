The Coin Change Problem is a classic dynamic programming problem where the goal is to determine the minimum number of coins required to make a given amount using the available denominations. If it's not possible to make the amount with the given coins, the solution should return `-1`.

### Problem Breakdown:

- **Input:**
    
    - An array of coin denominations (e.g., [100, 50, 20, 10, 5, 1]).
    - A target amount (e.g., 270).
- **Output:**
    
    - The minimum number of coins required to make the given amount. If it's not possible, return `-1`.

### Dynamic Programming Approach:

1. **Define DP Array:**
    
    - Let `dp[i]` represent the minimum number of coins needed to make the amount `i`.
    - The goal is to fill the array `dp[]` such that `dp[amount]` will eventually hold the minimum number of coins for the target amount.
2. **Recurrence Relation:**
    
    - For each coin `c`, and each amount `i`, if `i >= c`, update the `dp[i]` value by considering the possibility of using coin `c`: $$dp[i]=min⁡(dp[i],dp[i−c]+1)dp[i] = \min(dp[i], dp[i - c] + 1)$$
	    - `dp[i - c] + 1` represents using coin `c` and then looking at the remaining amount `i - c`.
1. **Initialization:**
    
    - Initialize `dp[0] = 0` because 0 coins are needed to make an amount of 0.
    - Set all other values of `dp[i]` to infinity (`∞`), meaning the amount `i` is initially unreachable.
4. **Example Walkthrough:**
    
    - Let’s say the target amount is **270**, and we have the available coins: [100, 50, 20, 10, 5, 1].

#### Step-by-Step Execution:

##### Initialization:

- `dp[0] = 0` because no coins are needed for the amount 0.
- For all amounts from 1 to 270, initialize `dp[i]` as infinity (`∞`), representing that these amounts are initially not achievable.

##### Execution:

We begin processing each amount from `1` to `270` and consider all coins one by one to update the `dp` values.

- **For Amount 1:**
    
    - Only the coin `1` is available. So, `dp[1] = min(dp[1], dp[1 - 1] + 1)` → `dp[1] = min(∞, 0 + 1)` → `dp[1] = 1`.
- **For Amount 2:**
    
    - Coin `1` can be used to get to `dp[2]`, so `dp[2] = min(∞, dp[1] + 1)` → `dp[2] = 2`.
- **For Amount 5:**
    
    - Coin `5` directly gives `dp[5] = 1` because 1 coin is enough to make 5 dollars.
- **For Amount 10:**
    
    - Coin `10` can directly give `dp[10] = 1`, so the minimum coins required to make 10 is 1.
- **For Amount 20:**
    
    - Coin `20` can directly give `dp[20] = 1`.
- **For Amount 50:**
    
    - Coin `50` can directly give `dp[50] = 1`.
- **For Amount 100:**
    
    - Coin `100` can directly give `dp[100] = 1`.
- **For Amount 105:**
    
    - We can make 105 by using `dp[100]` + 1 (i.e., `dp[105] = dp[100] + 1 = 1 + 1 = 2`).
- **For Amount 270:**
    
    - After processing all amounts up to 270, `dp[270] = 4`, which means that we can make 270 dollars with 4 coins.
    - The coins used are [100, 100, 50, 20].

##### Final Result:

- The minimum number of coins required to make 270 dollars is **4**, and the coins used are [100, 100, 50, 20].

---

### Key Insights:

- **DP Array Structure:**
    
    - `dp[i]` holds the minimum number of coins needed for amount `i`. Initially, it’s set to infinity for all amounts greater than 0 (meaning unreachable amounts), except `dp[0]`, which is 0.
- **Recurrence Relation:**
    
    - For each coin, the problem is solved iteratively by checking if the coin can be used to reduce the problem size (i.e., reduce the remaining amount) and update the minimum coins needed.
- **Time Complexity:**
    
    - The time complexity is **O(n * m)**, where `n` is the target amount and `m` is the number of coin denominations. This is because, for each amount, we check all available coins to update the `dp` value.

---

### Example Code Implementation:

```python
def coinChange(coins, amount):
    dp = [float('inf')] * (amount + 1)  # Initialize dp array with infinity
    dp[0] = 0  # No coins needed to make amount 0
    
    for i in range(1, amount + 1):
        for coin in coins:
            if i >= coin:
                dp[i] = min(dp[i], dp[i - coin] + 1)
    
    return dp[amount] if dp[amount] != float('inf') else -1

# Example usage:
coins = [100, 50, 20, 10, 5, 1]
amount = 270
result = coinChange(coins, amount)
print(result)  # Output: 4
```

This implementation follows the steps described and outputs the correct minimum number of coins for the given amount.