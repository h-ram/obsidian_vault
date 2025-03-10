# What is the Problem?
You want to **minimize a function** (fancy word for something you want to make as small as possible). For example:

- Suppose you're designing a product, and you want to **minimize cost** while following certain rules (constraints). 

The constraints are of two types:
1. **Equality Constraints** (g(x) = 0) – Rules you **must satisfy exactly**. For example, "The total weight must be 100 kg."
2. **Inequality Constraints** (h(x) ≤ 0) – Rules you can’t **go over**. For example, "The height must be no more than 10 meters."

---

# What are the KKT Conditions?
The **Karush-Kuhn-Tucker (KKT)** conditions are a checklist of requirements to find the best solution while following these rules.

Imagine you're trying to find the lowest point of a mountain (minimizing a function), but there are fences (constraints) around you. KKT tells you:
- Where to stop walking (stationarity),
- Whether you're inside the fences (primal feasibility),
- Which fences are blocking you (dual feasibility),
- And whether you're leaning against the fences or not (complementary slackness).

---

# Steps in Simple Terms

## 1. Set Up the Lagrangian
The Lagrangian is a formula that combines:
- The function you want to minimize (f(x)),
- The equality constraints (g(x)), and
- The inequality constraints (h(x)).

$L(x, λ, μ) = f(x) + λg(x) + μh(x)$


Here:
- λ (lambda): Multiplier for equality constraints.
- μ (mu): Multiplier for inequality constraints.

These multipliers adjust the importance of each constraint.

---

## 2. Conditions to Satisfy
To solve the problem, the solution must pass these 4 tests:

### 1. Stationarity
The "steepness" (gradient) of the Lagrangian must be **zero** at the solution.  
This means you're at a "flat" point where no improvement can be made.

∇f(x) + λ∇g(x) + μ∇h(x) = 0


Think of this as "balancing forces" between the function and the constraints.

### 2. Primal Feasibility
The solution must satisfy:
- g(x) = 0 (the equality rules), and
- h(x) ≤ 0 (the inequality rules).

### 3. Dual Feasibility
The multipliers for inequality constraints (μ) must be **non-negative**:

μ ≥ 0


You can't have "negative importance" for an inequality constraint.

### 4. Complementary Slackness
If an inequality constraint isn't blocking the solution (not "active"), its multiplier must be zero.  

μh(x) = 0

This means:
- If h(x) < 0 (not active), then μ = 0.
- If h(x) = 0 (active), then μ > 0.

---

# Example Walkthrough
Let’s apply this to an example:

**Minimize**:

f(x, y) = x^2 + y^2

**Subject to**:
1. g(x, y) = x + y - 1 = 0 (equality constraint).
2. h(x, y) = x - y ≤ 1 (inequality constraint).

---

## Step 1: Write the Lagrangian

L(x, y, λ, μ) = x^2 + y^2 + λ(x + y - 1) + μ(x - y - 1)
## Step 2: Apply the Conditions

### 1. Stationarity  
Take partial derivatives of L with respect to x, y, and set them to 0:


∂L/∂x = 2x + λ + μ = 0 (1) ∂L/∂y = 2y + λ - μ = 0 (2)


### 2. Primal Feasibility  
The constraints must be satisfied:

x + y - 1 = 0 (3) x - y ≤ 1 (4)


### 3. Dual Feasibility  
The multiplier for the inequality constraint must be non-negative:

μ ≥ 0 (5)

### 4. Complementary Slackness  
Either the inequality constraint is active (x - y = 1), or the multiplier is 0 (μ = 0):

μ(x - y - 1) = 0 (6)

---

## Step 3: Solve the System
Now, solve these equations step-by-step:

1. From x + y - 1 = 0 (Equation 3):  

y = 1 - x


2. Substitute y = 1 - x into x - y ≤ 1 (Equation 4):  

x - (1 - x) ≤ 1 2x ≤ 2 x ≤ 1


3. Use the stationarity equations (1 and 2):  
From (1): `2x + λ + μ = 0`.  
From (2): `2y + λ - μ = 0`.  

Substitute `y = 1 - x` into these and solve for x, λ, and μ.

---

## Final Solution
After solving, you find:

x = 0.5, y = 0.5, λ = -1, μ = 0


This is the optimal solution, satisfying all the KKT conditions.

---

# Key Takeaways
1. KKT combines the function and constraints into a unified system.
2. The four conditions ensure you're at the best solution while respecting the rules.
3. The method involves solving equations step-by-step to find the optimal x, y, and multipliers (λ, μ).
---
# Practice
