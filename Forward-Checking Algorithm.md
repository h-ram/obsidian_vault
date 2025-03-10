### How Forward Checking Works:
1. **Initial Setup**:
    - Each variable in the CSP has a domain of possible values.
    - Constraints define the allowed combinations of values for subsets of variables.
2. **Assign a Value to a Variable**:
    - When a variable X is assigned a value, forward checking immediately checks how this affects the remaining unassigned variables.
3. **Update Domains of Unassigned Variables**:
    - For every constraint involving X and another unassigned variable Y, forward checking removes from Y's domain any values that would violate the constraint when combined with X's assigned value.
4. **Backtrack if a Domain Becomes Empty**:
    - If the domain of any unassigned variable becomes empty (no valid value left), backtracking occurs because the current partial assignment cannot lead to a solution.
5. **Repeat**:
    - Continue assigning values to variables, updating domains, and backtracking when necessary until a solution is found or all possibilities are exhausted.
---
### Example:
- **Problem**: 3 variables $X,Y,Z$ with domains:
    - $D(X) = D(Y) = D(Z)= \{1,2\}$
    - Constraint: $X≠Y , Y≠Z$
- **Steps**:
    1. Assign X=1
    2. Forward checking updates:
        - $D(Y)$: Remove 1 because $X≠Y$, so $D(Y)={2}$.
        - $D(Z)$ No change yet because Z is not directly constrained by X.
    3. Assign $Y=2$.
    4. Forward checking updates:
        - $D(Z)$: Remove 2 because $Y≠Z$ , so $D(Z) = \{1\}$.
    5. Assign $Z=1$ (valid solution).
---