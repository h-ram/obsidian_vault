# CSP
### 1. Problem Description
 We have three regions: A, B, and C. The goal is to assign a color to each region such that no two adjacent regions have the same color. For simplicity, the available colors are {Red,Green,Blue}.
### 2. CSP Formulation
 **2.1 Variables**
- Each region is represented as a variable: X={A,B,C} where: A, B, and C represent the regions.
 **2.2 Domains**
- The domain for each variable is the set of colors: D(A)=D(B)=D(C)={Red,Green,Blue}.
 **2.3 Constraints**
1. **Adjacency Constraints**:
    - Region A is adjacent to B: A≠B
    - Region B is adjacent to C: B≠C
    - Region A is adjacent to C: A≠C
### 3. Representation as a CSP
 **Variables**:
X={A,B,C}
 **Domains**:
D(A)=D(B)=D(C)={Red,Green,Blue}
 **Constraints**:
1. A≠B   (Region A and B cannot have the same color).
2. B≠C   (Region B and C cannot have the same color).
3. A≠C   (Region A and C cannot have the same color).
 **4. Solution Process**
We assign values to the variables while respecting the constraints:
1. Assign A=Red
2. Assign B=Green (satisfying A≠B).
3. Assign C=Blue (satisfying B≠C and A≠C).
 **5. Solutions**
All valid assignments:
- A=Red,B=Green,C=Blue
- A=Red,B=Blue,C=Green
- A=Green,B=Red,C=Blue
- A=Green,B=Blue,C=Red
- A=Blue,B=Red,C=Green
- A=Blue,B=Green,C=Red
