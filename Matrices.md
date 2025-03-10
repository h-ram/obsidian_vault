#math 

A matrix is a rectangular array of numbers (or elements) arranged in rows and columns. It’s typically represented by a capital letter like $A$, and its elements are denoted by lower-case letters with subscripts, e.g., $a_{ij}$, where $i$ is the row index and $j$ is the column index.
#### **General Form**
A matrix $A$ with $m$ rows and $n$ columns (called an $m \times n$ matrix) looks like this:
$$A = \begin{bmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \\
a_{21} & a_{22} & \cdots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{m1} & a_{m2} & \cdots & a_{mn}
\end{bmatrix}
$$
#### **Examples**
- A $2 \times 3$ matrix:$$
B = \begin{bmatrix}
1 & 2 & 3 \\
4 & 5 & 6
\end{bmatrix}
$$
- A $3 \times 1$ matrix (also called a column vector):$$
C = \begin{bmatrix}
7 \\
8 \\
9
\end{bmatrix}
$$
- A $1 \times 1$ matrix is just a single number (a scalar).
---

### **Basic Terminology**
- **Dimensions**: The size of a matrix is given as $m \times n$, where $m$ is the number of rows and $n$ is the number of columns.
- **Square Matrix**: A matrix where $m = n$ (same number of rows and columns).
- **Element**: Each entry $a_{ij}$ in the matrix.
- **Row Vector**: A $1 \times n$ matrix.
- **Column Vector**: An $m \times 1$ matrix.
- **Diagonal**: In a square matrix, the elements $a_{ii}$ (where row index equals column index) form the main diagonal.

---
### **Types of Matrices**
There are special matrices with unique properties:
1. **Zero Matrix**: All elements are 0.
   $$O = \begin{bmatrix}
   0 & 0 \\
   0 & 0
   \end{bmatrix}$$
2. **Identity Matrix ($I$)**: A square matrix with 1s on the main diagonal and 0s elsewhere.
   $$
   I_3 = \begin{bmatrix}
   1 & 0 & 0 \\
   0 & 1 & 0 \\
   0 & 0 & 1
   \end{bmatrix}
   $$
3. **Diagonal Matrix**: A square matrix where all off-diagonal elements are 0.
   $$
   D = \begin{bmatrix}
   5 & 0 & 0 \\
   0 & 2 & 0 \\
   0 & 0 & 3
   \end{bmatrix}
   $$

4. **Symmetric Matrix**: A square matrix where $A = A^T$ (i.e., $a_{ij} = a_{ji}$).
   $$
   S = \begin{bmatrix}
   1 & 2 & 3 \\
   2 & 4 & 5 \\
   3 & 5 & 6
   \end{bmatrix}
   $$

5. **Upper Triangular Matrix**: All elements below the main diagonal are 0.
   $$
   U = \begin{bmatrix}
   1 & 2 & 3 \\
   0 & 4 & 5 \\
   0 & 0 & 6
   \end{bmatrix}
   $$

6. **Lower Triangular Matrix**: All elements above the main diagonal are 0.
   $$
   L = \begin{bmatrix}
   1 & 0 & 0 \\
   2 & 4 & 0 \\
   3 & 5 & 6
   \end{bmatrix}
   $$

---
### **Basic Operations on Matrices**
#### **Addition and Subtraction**
Matrices of the same dimensions can be added or subtracted element-wise.
- If $A$ and $B$ are both $m \times n$, then $C = A + B$ where $c_{ij} = a_{ij} + b_{ij}$.
**Example:**
$$
A = \begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix}, \quad B = \begin{bmatrix}
5 & 6 \\
7 & 8
\end{bmatrix}
$$
$$
A + B = \begin{bmatrix}
1+5 & 2+6 \\
3+7 & 4+8
\end{bmatrix} = \begin{bmatrix}
6 & 8 \\
10 & 12
\end{bmatrix}
$$

#### **Scalar Multiplication**
Multiply every element of a matrix by a scalar (a single number).
- If $k$ is a scalar, then $C = kA$ where $c_{ij} = k \cdot a_{ij}$.

**Example:**
$$
A = \begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix}, \quad k = 2
$$
$$
kA = \begin{bmatrix}
2 \cdot 1 & 2 \cdot 2 \\
2 \cdot 3 & 2 \cdot 4
\end{bmatrix} = \begin{bmatrix}
2 & 4 \\
6 & 8
\end{bmatrix}
$$

#### **Matrix Multiplication**
Matrix multiplication is defined between an $m \times n$ matrix $A$ and an $n \times p$ matrix $B$, resulting in an $m \times p$ matrix $C$.
- The element $c_{ij}$ is the dot product of the $i$-th row of $A$ and the $j$-th column of $B$:
$$
c_{ij} = \sum_{k=1}^n a_{ik} b_{kj}
$$

**Example:**
$$
A = \begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix}, \quad B = \begin{bmatrix}
5 & 6 \\
7 & 8
\end{bmatrix}
$$
$$
C = A \cdot B = \begin{bmatrix}
(1 \cdot 5 + 2 \cdot 7) & (1 \cdot 6 + 2 \cdot 8) \\
(3 \cdot 5 + 4 \cdot 7) & (3 \cdot 6 + 4 \cdot 8)
\end{bmatrix} = \begin{bmatrix}
19 & 22 \\
43 & 50
\end{bmatrix}
$$

**Note**: Matrix multiplication is **not commutative**, i.e., $AB \neq BA$ in general.
#### **Transpose**
The transpose of a matrix $A$, denoted $A^T$, swaps rows and columns.
- If $A$ is $m \times n$, then $A^T$ is $n \times m$, and $(A^T)_{ij} = a_{ji}$.

**Example:**
$$
A = \begin{bmatrix}
1 & 2 & 3 \\
4 & 5 & 6
\end{bmatrix}
$$
$$
A^T = \begin{bmatrix}
1 & 4 \\
2 & 5 \\
3 & 6
\end{bmatrix}
$$
---
### **5. Determinants**
The determinant is a scalar value associated with a square matrix. It provides information about the matrix (e.g., whether it’s invertible).
#### 2x2 Matrix
For a $2 \times 2$ matrix:
$$
A = \begin{bmatrix}
a & b \\
c & d
\end{bmatrix}
$$$$
\det(A) = ad - bc
$$

**Example:**
$$
A = \begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix}
$$
$$
\det(A) = (1 \cdot 4) - (2 \cdot 3) = 4 - 6 = -2
$$
#### 3x3 Matrix
For a $3 \times 3$ matrix, use the cofactor expansion along the first row:
$$
A = \begin{bmatrix}
a & b & c \\
d & e & f \\
g & h & i
\end{bmatrix}
$$
$$
\det(A) = a(ei - fh) - b(di - fg) + c(dh - eg)
$$
**Example:**
$$
A = \begin{bmatrix}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9
\end{bmatrix}
$$
$$
\det(A) = 1(5 \cdot 9 - 6 \cdot 8) - 2(4 \cdot 9 - 6 \cdot 7) + 3(4 \cdot 8 - 5 \cdot 7)
$$
$$
= 1(45 - 48) - 2(36 - 42) + 3(32 - 35)
$$
$$
= 1(-3) - 2(-6) + 3(-3) = -3 + 12 - 9 = 0
$$
#### n×n Matrix (General Case)
For larger matrices ($n \geq 3$), the determinant is computed using **cofactor expansion** or **row reduction**.
The determinant of an $n×n$ matrix $A$ is given by:
$$\det(A) = \sum_{j=1}^{n} (-1)^{1+j} a_{1j} \det(A_{1j})$$
- $a_{1j}$ is an element from the first row.
- $A_{1j}$ is the minor (submatrix obtained by removing row 1 and column j).
- The sign factor $(-1)^{1+j}$ alternates signs.
#### **Properties of Determinants**
- $\det(AB) = \det(A) \det(B)$
- $\det(A^T) = \det(A)$
- If $\det(A) = 0$, the matrix is not invertible (singular).

---

### **6. Inverse of a Matrix**
The inverse of a square matrix $A$, denoted $A^{-1}$, satisfies:
$$
A A^{-1} = A^{-1} A = I
$$
A matrix is invertible only if its determinant is non-zero.
#### **2x2 Matrix Inverse**
For:
$$
A = \begin{bmatrix}
a & b \\
c & d
\end{bmatrix}
$$
$$
A^{-1} = \frac{1}{\det(A)} \begin{bmatrix}
d & -b \\
-c & a
\end{bmatrix}
$$

**Example:**
$$
A = \begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix}
$$
$\det(A) = -2$ (from earlier).
$$
A^{-1} = \frac{1}{-2} \begin{bmatrix}
4 & -2 \\
-3 & 1
\end{bmatrix} = \begin{bmatrix}
-2 & 1 \\
1.5 & -0.5
\end{bmatrix}
$$

#### **General Method**
For larger matrices, use the adjoint method:
$$
A^{-1} = \frac{1}{\det(A)} \text{adj}(A)
$$
where $\text{adj}(A)$ is the adjugate matrix (transpose of the cofactor matrix).

---

### **7. Eigenvalues and Eigenvectors**
For a square matrix $A$, an eigenvector $v$ and eigenvalue $\lambda$ satisfy:
$$
A v = \lambda v
$$
#### **Finding Eigenvalues**
Solve the characteristic equation:
$$
\det(A - \lambda I) = 0
$$
**Example:**
$$
A = \begin{bmatrix}
2 & 1 \\
1 & 2
\end{bmatrix}
$$
$$
A - \lambda I = \begin{bmatrix}
2 - \lambda & 1 \\
1 & 2 - \lambda
\end{bmatrix}
$$
$$
\det(A - \lambda I) = (2 - \lambda)^2 - 1 = 0
$$
$$
(2 - \lambda)^2 = 1 \implies 2 - \lambda = \pm 1
$$
$$
\lambda = 3 \text{ or } \lambda = 1
$$
#### **Finding Eigenvectors**
For each eigenvalue, solve $(A - \lambda I)v = 0$.

For $\lambda = 3$:
$$
A - 3I = \begin{bmatrix}
-1 & 1 \\
1 & -1
\end{bmatrix}
$$
Solve:
$$
\begin{bmatrix}
-1 & 1 \\
1 & -1
\end{bmatrix} \begin{bmatrix}
v_1 \\
v_2
\end{bmatrix} = 0
$$
\[
-v_1 + v_2 = 0 \implies v_1 = v_2
\]
Eigenvector: $\begin{bmatrix} 1 \\ 1 \end{bmatrix}$.

For $\lambda = 1$:
\[
A - I = \begin{bmatrix}
1 & 1 \\
1 & 1
\end{bmatrix}
\]
\[
v_1 + v_2 = 0 \implies v_1 = -v_2
\]
Eigenvector: $\begin{bmatrix} 1 \\ -1 \end{bmatrix}$.

---

### **8. Applications of Matrices**
Matrices have countless applications:

1. **Systems of Linear Equations**:
   Represent as $Ax = b$, solve using Gaussian elimination or $x = A^{-1} b$.

2. **Transformations**:
   Matrices represent linear transformations like rotations, scaling, etc.
   - Example: Rotation matrix in 2D:
   \[
   R = \begin{bmatrix}
   \cos \theta & -\sin \theta \\
   \sin \theta & \cos \theta
   \end{bmatrix}
   \]

3. **Graph Theory**:
   Adjacency matrices represent graphs where $a_{ij} = 1$ if there’s an edge between vertices $i$ and $j$.

4. **Computer Graphics**:
   Matrices handle transformations (e.g., scaling, rotation) of objects in 3D space.

5. **Machine Learning**:
   Matrices represent datasets, weights in neural networks, etc.

---

### **9. Advanced Concepts**
- **Singular Value Decomposition (SVD)**: Decomposes $A = U \Sigma V^T$, used in data compression, PCA, etc.
- **Positive Definite Matrices**: A symmetric matrix $A$ where $x^T A x > 0$ for all non-zero $x$.
- **Jordan Canonical Form**: Represents matrices in a nearly diagonal form for non-diagonalizable matrices.

---

### **10. Practical Tips**
- Use libraries like NumPy in Python for matrix operations:
  ```python
  import numpy as np
  A = np.array([[1, 2], [3, 4]])
  B = np.array([[5, 6], [7, 8]])
  print(A @ B)  # Matrix multiplication
  print(np.linalg.det(A))  # Determinant
  print(np.linalg.inv(A))  # Inverse
  ```
- For large matrices, numerical stability matters—use algorithms like LU decomposition or QR factorization.

---

### **Summary**
Matrices are powerful tools for organizing and manipulating data. They allow you to solve systems of equations, represent transformations, and model real-world phenomena. Start with basic operations (addition, multiplication), then explore determinants, inverses, and eigenvalues for deeper understanding. If you’d like to dive into a specific application or problem, let me know!
# **Transpose of a Matrix ($A^T$)**
The **transpose** of a matrix $A$, denoted as $A^T$, is obtained by swapping its rows and columns.
If $A$ is an $m×n$ matrix:
$$A = \begin{bmatrix} a_{11} & a_{12} & \dots & a_{1n} \\ a_{21} & a_{22} & \dots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \dots & a_{mn} \end{bmatrix}$$
Then its **transpose** $A^T$ is an $n×m$ matrix where the **rows become columns**:
$$A^T = \begin{bmatrix} a_{11} & a_{21} & \dots & a_{m1} \\ a_{12} & a_{22} & \dots & a_{m2} \\ \vdots & \vdots & \ddots & \vdots \\ a_{1n} & a_{2n} & \dots & a_{mn} \end{bmatrix}$$
---
**Example**

$$A = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{bmatrix} \quad A^T = \begin{bmatrix} 1 & 4 \\ 2 & 5 \\ 3 & 6 \end{bmatrix}$$

---
# **Properties of Transpose**
1. **Double Transpose**: $(A^T)^T = A$
2. **Transpose of a Sum**: $(A + B)^T = A^T + B^T$
3. **Transpose of a Product**: $(AB)^T = B^T A^T$
4. **Transpose of a Scalar Multiple**: $(\alpha A)^T = \alpha A^T$, where $\alpha$ is a scalar.
5. **Symmetric Matrix**: A matrix is symmetric if $A^T = A$.