#math 

Eigenvalues and eigenvectors are fundamental concepts in linear algebra that describe how a matrix transforms a vector.

Given a **square matrix** $A$ of size $n×n$, an **eigenvector** $v$ and its corresponding **eigenvalue** $\lambda$ satisfy the equation:
$$A v = \lambda v$$
- $A$ is an $n×n$  matrix,
- $v$ is a **nonzero vector** (eigenvector),
- $\lambda$ is a **scalar** (eigenvalue),
- The equation states that when matrix $A$ transforms $v$, the vector's **direction remains unchanged**, but its magnitude is scaled by $\lambda$.
---
# **Finding Eigenvalues and Eigenvectors**
### **Step 1: Solve the Characteristic Equation**
To find eigenvalues, solve the [[Characteristic Equation]]:
$$\det(A - \lambda I) = 0$$
- $I$ is the [[Identity Matrix]],
- $\det(\cdot)$ represents the [[Determinant]].
### **Step 2: Solve for Eigenvectors**
Once eigenvalues $\lambda$ are found, solve:
$$(A - \lambda I)v = 0$$
to find the corresponding eigenvectors.

---
### **Example Calculation**
Consider the matrix:
$A = \begin{bmatrix} 4 & -2 \\ 1 & 1 \end{bmatrix}$
### **Step 1: Compute the Characteristic Equation**
$\det(A - \lambda I) = \det \begin{bmatrix} 4-\lambda & -2 \\ 1 & 1-\lambda \end{bmatrix} = 0$
Expanding the determinant:
$(4 - \lambda)(1 - \lambda) - (-2)(1) = 0$
$4 - 4\lambda - \lambda + \lambda^2 + 2 = 0$ 
$\lambda^2 - 5\lambda + 6 = 0$
Factorizing:
$(\lambda - 3)(\lambda - 2) = 0$
So, the **eigenvalues** are $\lambda_1 = 3,\lambda_2 = 2.$
### **Step 2: Solve for Eigenvectors**
For $\lambda_1 = 3$:

$(A - 3I) v = 0$ 

$= \begin{bmatrix} 4-3 & -2 \\ 1 & 1-3 \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}$ 

$= \begin{bmatrix} 1 & -2 \\ 1 & -2 \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}$

Solving, $x = 2y$, so an eigenvector is:
$v_1 = \begin{bmatrix} 2 \\ 1 \end{bmatrix}$

For $\lambda_2 = 2:$

$\begin{bmatrix} 2 & -2 \\ 1 & -1 \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}$

Solving, $x = y$, so another eigenvector is:
$v_2 = \begin{bmatrix} 1 \\ 1 \end{bmatrix}$
---
# **Properties of Eigenvalues and Eigenvectors**
- **A matrix can have up to nn eigenvalues** (for an n×nn \times n matrix).
- **The eigenvectors corresponding to different eigenvalues are linearly independent**.
- **The determinant of AA is the product of its eigenvalues**:
    $\det(A) = \prod_{i=1}^{n} \lambda_i$
- **The trace of AA (sum of diagonal elements) is the sum of eigenvalues**:
    $\text{Tr}(A) = \sum_{i=1}^{n} \lambda_i$

---
# **Eigenvalues & Eigenvectors in Applications**
**1. Principal Component Analysis (PCA)**
- The **covariance matrix** of a dataset has eigenvectors that define the **principal components**.
- The eigenvalues indicate the **variance captured** by each principal component.
**2. Google’s PageRank Algorithm**
- The eigenvector of a web link matrix determines the **importance of webpages**.
**3. Image Compression**
- Singular Value Decomposition (SVD), which relies on eigenvalues, is used for **image compression**.
**4. Quantum Mechanics**
- Eigenvalues of quantum operators represent **observable physical quantities**.

---

# **Eigenvalues & Eigenvectors in Python**
Using NumPy, we can compute them easily:
```python
import numpy as np

# Define matrix
A = np.array([[4, -2], [1, 1]])

# Compute eigenvalues and eigenvectors
eigenvalues, eigenvectors = np.linalg.eig(A)

print("Eigenvalues:", eigenvalues)
print("Eigenvectors:\n", eigenvectors)

# Output
# Eigenvalues: [3. 2.]
# Eigenvectors:
# [[ 0.8944  0.7071]
#  [ 0.4472  0.7071]]
```
These eigenvectors are **normalized**, meaning their lengths are 1.

---