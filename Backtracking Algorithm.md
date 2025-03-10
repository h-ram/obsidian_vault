**Backtracking** in Constraint Satisfaction Problems (CSP) is a systematic search algorithm used to find solutions by incrementally building assignments for variables while ensuring constraints are satisfied. It explores the search space by assigning values to one variable at a time and backtracks whenever a constraint is violated.
### How it Works:

1. **Start with an Empty Assignment**: Initially, no variables are assigned a value.
2. **Assign a Value**: Assign a value to a variable from its domain, checking if the assignment satisfies all constraints.
3. **Proceed Recursively**: Move to the next variable and repeat the process.
4. **Backtrack on Failure**: If no valid value can be assigned to a variable (constraint violation), backtrack to the previous variable and try the next possible value.
5. **Continue or Stop**: Continue until all variables are assigned (solution found) or all options are exhausted (no solution exists).
### Example:
For a CSP where variables $X,Y$ must satisfy $X+Y=3$ with domains D(X) = D(Y) = {1,2}:
1. Assign X=1.
2. Try $Y=1: 1+1 ≠ 3$ → Backtrack.
3. Try $Y=2: 1+2 = 3$ → Solution: $X=1,Y=2$.
---
