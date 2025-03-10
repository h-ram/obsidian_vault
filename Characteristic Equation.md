#math 

The **characteristic equation** is a fundamental concept in linear algebra and differential equations. It is primarily used to find eigenvalues of a matrix or to solve linear differential equations.
# **Characteristic Equation of a Matrix**
Given an $n×n$ square matrix $A$, the characteristic equation is derived from the **characteristic polynomial**, which is defined as:
$$\det(A - \lambda I) = 0$$
where:
- $\lambda$ represents an eigenvalue of $A$,
- $I$ is the [[Identity Matrix]] of the same dimension as $A$,
- $\det$ denotes the [[Determinant]].
**Example:**
For a 2×2 matrix:
$A = \begin{bmatrix} 4 & 3 \\ 2 & 1 \end{bmatrix}$
The characteristic equation is obtained as:
$\det \begin{bmatrix} 4 - \lambda & 3 \\ 2 & 1 - \lambda \end{bmatrix} = 0$
Expanding the determinant:
$(4 - \lambda)(1 - \lambda) - (3 \times 2) = 0$
$4 - 4\lambda - \lambda + \lambda^2 - 6 = 0$
$\lambda^2 - 5\lambda - 2 = 0$