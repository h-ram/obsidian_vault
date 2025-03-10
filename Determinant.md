#math 

The **determinant** is a [[Scalar Value]] associated with a square matrix. It provides important properties about the matrix, such as whether it is invertible and how it scales transformations.
# **Determinant of a 2×2 Matrix**
$$A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$$$$\det(A) = ad - bc$$
**Example:**
$A = \begin{bmatrix} 4 & 3 \\ 2 & 1 \end{bmatrix}$
$\det(A) = (4 \times 1) - (3 \times 2) = 4 - 6 = -2$
# **Determinant of a 3×3 Matrix**
$$A = \begin{bmatrix} a & b & c \\ d & e & f \\ g & h & i \end{bmatrix}$$
$$\det(A) = a(ei - fh) - b(di - fg) + c(dh - eg)$$
**Example:**
$A = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 9 \end{bmatrix}$
$\det(A) = 1(5\cdot9 - 6\cdot8) - 2(4\cdot9 - 6\cdot7) + 3(4\cdot8 - 5\cdot7)$
$= 1(45 - 48) - 2(36 - 42) + 3(32 - 35)$
$=1(-3) - 2(-6) + 3(-3) = -3 + 12 - 9 = 0$
Since the determinant is **0**, the matrix is **singular** (non-invertible)


# **Properties of Determinants**
1. **If a matrix has a row or column of zeros, its determinant is 0.**
2. **Swapping two rows negates the determinant.**
3. **If two rows or columns are identical, the determinant is 0.**
4. **Multiplying a row by a scalar multiplies the determinant by the same scalar.**
5. **Determinant of an identity matrix is always 1.**
6. **For an invertible matrix A, $\det(A^{-1}) = \frac{1}{\det(A)}$.**
# **Determinants and Matrix Invertibility**
- If $\det(A) \neq 0$, the matrix is **invertible**.
- If $\det(A) = 0$, the matrix is **singular** (not invertible).
