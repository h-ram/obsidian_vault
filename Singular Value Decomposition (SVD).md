#math 

Singular Value Decomposition (**SVD**) is a fundamental technique in linear algebra **that decomposes a matrix into three separate matrices**.
Given an **m × n** matrix $A$, the **SVD decomposition** is:
$$A = U \Sigma V^T$$
- $U$ (_m × m_): Left singular vectors (orthogonal matrix)
- $\Sigma$ (_m × n_): Diagonal matrix of singular values
- $V^T$ (_n × n_): Right singular vectors (orthogonal matrix).
---
# **Components of SVD**
#### **2.1. Left Singular Vectors ($U$)**
- Columns of $U$ are called **left singular vectors**.
- These are the **eigenvectors** of $A A^T$.
- They are orthogonal and form an orthonormal basis for the column space of $A$.
#### **2.2. Singular Values ($\Sigma$)**
- The diagonal elements of $\Sigma$ are the **singular values** of $A$.
- These are the square roots of the **eigenvalues** of $A^T A$.
- The singular values are always **non-negative** and **sorted in decreasing order**.
#### **2.3. Right Singular Vectors ($V$)**
- Columns of $V$ are called **right singular vectors**.
- These are the **eigenvectors** of $A^T A$.
- They form an orthonormal basis for the row space of $A$.
---
# **How to Obtain The SDV**
1. Compute $A^T A$ and $A A^T$
2. Compute the Eigenvalues of $A^T A$ -> ($\lambda^1$ and $\lambda^2$)
3. Compute **Singular Values** ($\Sigma$ ) $$\sigma_1 = \sqrt{\lambda^1}, \quad \sigma_2 = \sqrt{\lambda^2}$$
4. Compute **Right Singular Vectors** ($V$) $$(A^T A - \lambda I)V = 0$$
5. Compute **Left Singular Vectors** ($U$) $$(A A^T - \lambda I)U = 0$$
### **Example:**
We are given the matrix:
$$A = \begin{bmatrix} 4 & 0 \\ 3 & -5 \end{bmatrix}$$
We want to find its **Singular Value Decomposition (SVD)**, i.e.,
$$A = U \Sigma V^T$$
where:
- **UU** (left singular vectors)
- **Σ\Sigma** (singular values)
- **VTV^T** (right singular vectors)
---
**Step 1: Compute $A^T A$ and $A A^T$**
$$A^T A = \begin{bmatrix} 4 & 3 \\ 0 & -5 \end{bmatrix} \begin{bmatrix} 4 & 0 \\ 3 & -5 \end{bmatrix} = \begin{bmatrix} 16 & 12 \\ 12 & 34 \end{bmatrix}$$
$$A A^T = \begin{bmatrix} 4 & 0 \\ 3 & -5 \end{bmatrix} \begin{bmatrix} 4 & 3 \\ 0 & -5 \end{bmatrix} = \begin{bmatrix} 16 & 12 \\ 12 & 34 \end{bmatrix}$$
(Interestingly, we get the same result here.)

---
**Step 2: Compute the Eigenvalues of $A^T A$**
To find **singular values**, compute the eigenvalues of $A^T A$:
Solve the characteristic equation:
$$
\begin{align*}
    \det(A^T A - \lambda I) = 0 \\ \\
    \begin{vmatrix} 16 - \lambda & 12 \\ 12 & 34 - \lambda \end{vmatrix} = 0
\end{align*}
$$
Expanding the determinant:
$$
\begin{align*}
	(16 - \lambda)(34 - \lambda) - (12)(12) = 0 \\
	544 - 50\lambda + \lambda^2 - 144 = 0 \\
	\lambda^2 - 50\lambda + 400 = 0
\end{align*}
$$
Solving using the quadratic formula:
$$
\begin{align}
	\lambda = \frac{50 \pm \sqrt{50^2 - 4(1)(400)}}{2(1)} \\
	= \frac{50 \pm \sqrt{2500 - 1600}}{2} \\
	= \frac{50 \pm \sqrt{900}}{2} \\
	= \frac{50 \pm 30}{2} \\
	\lambda_1 = \frac{50 + 30}{2} = 40 \\
	\quad \lambda_2 = \frac{50 - 30}{2} = 10
\end{align}
$$

Thus, the **singular values** are:
$$\sigma_1 = \sqrt{40} = 6.32, \quad \sigma_2 = \sqrt{10} = 3.16$$
So the **$\Sigma$ matrix** is:
$$\Sigma = \begin{bmatrix} 6.32 & 0 \\ 0 & 3.16 \end{bmatrix}$$
---
**Step 3: Compute Right Singular Vectors ($V$)**
Solve for each $\lambda$ the following:
$$(A^T A - \lambda I)V = 0$$
1. For $\lambda_1 = 40$:$$
	\begin{align*}
		\begin{bmatrix} 16 - 40 & 12 \\ 12 & 34 - 40 \end{bmatrix}
		\begin{bmatrix} v_1 \\ v_2 \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix} \\
		\begin{bmatrix} -24 & 12 \\ 12 & -6 \end{bmatrix}  \begin{bmatrix} v_1 \\ v_2 \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}
	\end{align*}
	$$
	Solving $-24 v_1 + 12 v_2 = 0$ 
	gives $v_1 = 0.447, v_2 = 0.894$.
2. For $\lambda_2 = 10$, solving similarly gives $v_1 = -0.894, v_2 = 0.447$.
Thus, $V$is:
$$V = \begin{bmatrix} 0.447 & -0.894 \\ 0.894 & 0.447 \end{bmatrix}$$
---
**Step 4: Compute Left Singular Vectors ($U$)**

Solve for each $\lambda$:
$$(A A^T - \lambda I)U = 0$$
Using the same method as above, we get:
$$U = \begin{bmatrix} 0.894 & 0.447 \\ 0.447 & -0.894 \end{bmatrix}$$
---
**Step 5: Verify the SVD Decomposition**
Now we check:
$$A = U \Sigma V^T$$
Multiplying,
$$\begin{bmatrix} 0.894 & 0.447 \\ 0.447 & -0.894 \end{bmatrix} \begin{bmatrix} 6.32 & 0 \\ 0 & 3.16 \end{bmatrix} \begin{bmatrix} 0.447 & -0.894 \\ 0.894 & 0.447 \end{bmatrix} = \begin{bmatrix} 4 & 0 \\ 3 & -5 \end{bmatrix}$$
Thus, we successfully decomposed $A$ into $U \Sigma V^T$! 🎉

---
**Final Results:**
- $U$: $\begin{bmatrix} 0.894 & 0.447 \\ 0.447 & -0.894 \end{bmatrix}$
- $\Sigma$: $\begin{bmatrix} 6.32 & 0 \\ 0 & 3.16 \end{bmatrix}$
- $V$: $\begin{bmatrix} 0.447 & -0.894 \\ 0.894 & 0.447 \end{bmatrix}$
---
# **Applications of SVD**
#### **5.1. Dimensionality Reduction (PCA)**
- Principal Component Analysis (**PCA**) uses SVD to project data onto **principal components**.
- By keeping only **top singular values**, we reduce dimensions while preserving most of the variance.
#### **5.2. Image Compression**
- An image is represented as a matrix of pixel values.
- By keeping only the top kk singular values, we can **approximate** the image with fewer data points.
#### **5.3. Recommendation Systems**
- Used in **Latent Semantic Analysis (LSA)** to extract hidden relationships in data.
- Netflix and Spotify use SVD to recommend content.
#### **5.4. Solving Linear Systems**
- SVD helps solve **ill-conditioned** linear systems, improving stability.
#### **5.5. Noise Reduction**
- Small singular values correspond to noise.
- By filtering them out, we get a cleaner signal.
---
# **SVD in Python**
```python
import numpy as np

# Define matrix A
A = np.array([[4, 0], [3, -5]])

# Compute SVD
U, Sigma, VT = np.linalg.svd(A)

print("U Matrix:\n", U)
print("Singular Values:\n", Sigma)
print("V Transpose:\n", VT)
```

```python
# Output
U Matrix:
 [[-0.4472136  -0.89442719]
 [-0.89442719  0.4472136 ]]
Singular Values:
 [6.32455532 3.16227766]
V Transpose:
 [[-0.70710678  0.70710678]
 [-0.70710678 -0.70710678]]
```
---