#math 

An **identity matrix** is a square matrix in which all the elements on the main diagonal are **1**, and all other elements are **0**. It is denoted by **$I_n$** for an $n×n$ matrix.
$$I_n = \begin{bmatrix} 1 & 0 & 0 & \cdots & 0 \\ 0 & 1 & 0 & \cdots & 0 \\ 0 & 0 & 1 & \cdots & 0 \\ \vdots & \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & 0 & \cdots & 1 \end{bmatrix}$$

In general, the elements of $I_n$ are given by:
$$(I_n)_{ij} = \begin{cases} 1, & \text{if } i = j \\ 0, & \text{if } i \neq j \end{cases}$$
where $i, j = 1, 2, \dots, n$.
**Examples**:
$$I_2 = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix} \quad I_3 = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix} \quad I_4 = \begin{bmatrix} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 1 \end{bmatrix}$$
# **Properties of an Identity Matrix**
1. **Multiplicative Identity**: For any square matrix $A$ of size $n×n$, multiplying it by the identity matrix results in the same matrix:
    $A \cdot I_n = I_n \cdot A = A$
2. **Inverse Property**: The identity matrix is the inverse of itself, meaning:
    $I_n^{-1} = I_n$
3. **Determinant**: The determinant of an identity matrix is always **1**:
    $\det(I_n) = 1$
4. **Eigenvalues**: All eigenvalues of an identity matrix are **1**.