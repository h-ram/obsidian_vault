A constraint satisfaction problem (CSP) is a problem where we have to assign some variables certain values following certain constraints.
An example of a CSP is: I have to give my kids birthday gifts, as long as they don't get jealous from each other.
- variables = gifts
- constraints = gifts must not be a lot better than other gifts, so to not get jealous.
# Components of a CSP
1. **Variables**:
    - Represent the entities that need values.
    - Example: X1​,X2​,…,Xn​.
2. **Domains**:
    - Define the possible values that each variable can take.
    - Example: D1​,D2​,…,Dn​, where Xi∈Di.
3. **Constraints**:
    - Define the restrictions on allowable combinations of variable assignments.
    - Example: A constraint might specify that X1≠X2
4. **Objective**:
    - Assign a value to each variable from its domain such that all constraints are satisfied.
### Brief Examples of CSPs:
1. **Sudoku**:
    - Variables: Each cell in the grid.
    - Domains: Numbers 1 to 9.
    - Constraints: Each number must appear exactly once in each row, column, and 3x3 subgrid.
2. **[[Map Coloring Problem#CSP|Graph Coloring]]**: 
    - Variables: Nodes in a graph.
    - Domains: Colors (e.g., red, green, blue).
    - Constraints: Adjacent nodes cannot have the same color.
3. **Scheduling**:
    - Variables: Time slots for tasks.
    - Domains: Available time slots.
    - Constraints: No two tasks can occupy the same time slot, and some tasks must be scheduled before others.
# Assignment
In CSP, assignment refers to giving a variable Xi a value from its Domain Di.
An assignment can be categorized based on **scope** and **constraint**
1. scope:
	- partial assignment: an assignment in which some variables are assigned.
	- complete assignment: an assignment in which all variables are assigned.
2. constraint:
	- consistent assignment: an assignment that doesn't violate any constraints.
	- inconsistent assignment: an assignment that violates at least one constraint.
A ***complete*** and ***consistent*** assignment is considered a **solution** for a CSP.
# Solving Approaches
CSPs Can be solve using [[Backtracking Algorithm|Backtracking]], [[Forward-Checking Algorithm|Forward-Checking]] or [[Arc Consistency 3|AC3]]

---
# Practice
### 1. Workshop Scheduling
- **Variables**: {W1, W2, W3} (workshops)
- **Domains**: {1, 2, 3} (time slots: 1 = 9 AM, 2 = 12 PM, 3 = 3 PM)
- **Constraints**:
  - $W1 \neq W2$ (W1 and W2 cannot be scheduled at the same time)
  - $W2 \neq W3$ (W2 and W3 cannot be scheduled at the same time)
---
### 2. Classroom Assignment
- **Variables**: {C1, C2, C3, C4} (classes)
- **Domains**: {Room A, Room B, Room C}
- **Constraints**:
  - $C1 \neq C2$ (Classes C1 and C2 must be in different rooms)
  - $C3 \neq C4$ (Classes C3 and C4 must be in different rooms)
  - $C2 = C3$ (Classes C2 and C3 must be in the same room)
---
### 3. Student Course Selection
- **Variables**: {S1, S2, S3} (students)
- **Domains**: {Math, Physics, Chemistry}
- **Constraints**:
  - $S1 \neq S2$ (Students S1 and S2 cannot take the same course)
  - $S2 \neq S3$ (Students S2 and S3 cannot take the same course)
  - $S1 = \text{Chemistry}$ (Student S1 must take Chemistry)

---
### 4. Meeting Room Scheduling
- **Variables**: {M1, M2, M3} (meetings)
- **Domains**: {9 AM, 10 AM, 11 AM, 12 PM}
- **Constraints**:
  - $M1 \neq M2$ (Meetings M1 and M2 must be scheduled at different times)
  - $M2 \neq M3$ (Meetings M2 and M3 must be scheduled at different times)
  - $M1 \neq 9 \text{ AM}$ (Meeting M1 cannot be at 9 AM)
---
### 5. Event Catering
- **Variables**: {E1, E2, E3} (events)
- **Domains**: {Buffet, Set Menu, À La Carte}
- **Constraints**:
  - $E1 \neq E2$ (Events E1 and E2 must have different catering styles)
  - $E2 \neq E3$ (Events E2 and E3 must have different catering styles)
  - $E3 = \text{Buffet}$ (Event E3 must have a Buffet)
---
# Solutions
### 1. Workshop Scheduling
- **Variables**: {W1, W2, W3} (workshops)
- **Domains**: {1, 2, 3} (time slots: 1 = 9 AM, 2 = 12 PM, 3 = 3 PM)
- **Constraints**:
  - $W1 \neq W2$ (W1 and W2 cannot be scheduled at the same time)
  - $W2 \neq W3$ (W2 and W3 cannot be scheduled at the same time)
#### Solution:
1. Assign $W1 = 1$ (9 AM).
2. Assign $W2 = 2$ (12 PM), as it satisfies $W1 \neq W2$.
3. Assign $W3 = 3$ (3 PM), as it satisfies $W2 \neq W3$.
4. Final assignment: $W1 = 1$, $W2 = 2$, $W3 = 3$.

---
### 2. Classroom Assignment
- **Variables**: {C1, C2, C3, C4} (classes)
- **Domains**: {Room A, Room B, Room C}
- **Constraints**:
  - $C1 \neq C2$ (Classes C1 and C2 must be in different rooms)
  - $C3 \neq C4$ (Classes C3 and C4 must be in different rooms)
  - $C2 = C3$ (Classes C2 and C3 must be in the same room)
#### Solution:
1. Assign $C1 = \text{Room A}$.
2. Assign $C2 = \text{Room B}$, satisfying $C1 \neq C2$.
3. Assign $C3 = \text{Room B}$, satisfying $C2 = C3$.
4. Assign $C4 = \text{Room A}$, satisfying $C3 \neq C4$.
5. Final assignment: $C1 = \text{Room A}$, $C2 = \text{Room B}$, $C3 = \text{Room B}$, $C4 = \text{Room A}$.
---
### 3. Student Course Selection
- **Variables**: {S1, S2, S3} (students)
- **Domains**: {Math, Physics, Chemistry}
- **Constraints**:
  - $S1 \neq S2$ (Students S1 and S2 cannot take the same course)
  - $S2 \neq S3$ (Students S2 and S3 cannot take the same course)
  - $S1 = \text{Chemistry}$ (Student S1 must take Chemistry)
#### Solution:
1. Assign $S1 = \text{Chemistry}$, as required.
2. Assign $S2 = \text{Math}$, satisfying $S1 \neq S2$.
3. Assign $S3 = \text{Physics}$, satisfying $S2 \neq S3$.
4. Final assignment: $S1 = \text{Chemistry}$, $S2 = \text{Math}$, $S3 = \text{Physics}$.
---
### 4. Meeting Room Scheduling
- **Variables**: {M1, M2, M3} (meetings)
- **Domains**: {9 AM, 10 AM, 11 AM, 12 PM}
- **Constraints**:
  - $M1 \neq M2$ (Meetings M1 and M2 must be scheduled at different times)
  - $M2 \neq M3$ (Meetings M2 and M3 must be scheduled at different times)
  - $M1 \neq 9 \text{ AM}$ (Meeting M1 cannot be at 9 AM)
#### Solution:
1. Assign $M1 = 10 \text{ AM}$, satisfying $M1 \neq 9 \text{ AM}$.
2. Assign $M2 = 11 \text{ AM}$, satisfying $M1 \neq M2$.
3. Assign $M3 = 12 \text{ PM}$, satisfying $M2 \neq M3$.
4. Final assignment: $M1 = 10 \text{ AM}$, $M2 = 11 \text{ AM}$, $M3 = 12 \text{ PM}$.
---
### 5. Event Catering
- **Variables**: {E1, E2, E3} (events)
- **Domains**: {Buffet, Set Menu, À La Carte}
- **Constraints**:
  - $E1 \neq E2$ (Events E1 and E2 must have different catering styles)
  - $E2 \neq E3$ (Events E2 and E3 must have different catering styles)
  - $E3 = \text{Buffet}$ (Event E3 must have a Buffet)
#### Solution:
1. Assign $E3 = \text{Buffet}$, as required.
2. Assign $E1 = \text{Set Menu}$, satisfying $E1 \neq E2$.
3. Assign $E2 = \text{À La Carte}$, satisfying $E1 \neq E2$ and $E2 \neq E3$.
4. Final assignment: $E1 = \text{Set Menu}$, $E2 = \text{À La Carte}$, $E3 = \text{Buffet}$.
