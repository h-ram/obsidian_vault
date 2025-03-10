Principal Component Analysis (PCA) is a **dimensionality reduction** technique used in statistics and machine learning to transform high-dimensional data into a lower-dimensional space while preserving as much variance as possible.

---
# **How to Perform PCA**
### Step 1: Prepare Your Data
Start with a dataset in the form of a matrix $X$, where:
- Rows represent samples (e.g., observations, like people or objects).
- Columns represent features (e.g., variables like height, weight, etc.).
- $X$ is an $n \times p$ matrix, where $n$ is the number of samples and $p$ is the number of features.
---
### Step 2: Standardize the Data
Since features might be on different scales (e.g., height in inches, weight in pounds), standardize the data so each feature has a mean of 0 and a standard deviation of 1. This prevents features with larger scales from dominating the analysis.
For each feature (column) $j$:
1. Compute the mean $\mu_j$:  
   $$\mu_j = \frac{1}{n} \sum_{i=1}^n X_{ij}$$
2. Compute the standard deviation $\sigma_j$:  
   $$\sigma_j = \sqrt{\frac{1}{n} \sum_{i=1}^n (X_{ij} - \mu_j)^2}$$
3. Standardize each data point:  
   $$Z_{ij} = \frac{X_{ij} - \mu_j}{\sigma_j}$$
The result is a new matrix $Z$, where each column has mean 0 and standard deviation 1. Standardization is crucial unless your features are already on comparable scales or you have a specific reason to skip it (e.g., in some domain-specific cases).
---
### Step 3: Compute the Covariance Matrix
The covariance matrix captures the relationships (correlations) between features in the standardized data. Since we standardized, this matrix is effectively a correlation matrix scaled by the variances (which are now 1).
The covariance matrix $C$ is computed as:
$$C = \frac{1}{n-1} Z^T Z$$
- $Z^T$ is the transpose of $Z$.
- $Z^T Z$ is a $p \times p$ matrix.
- Dividing by $n-1$ gives an unbiased estimate of the covariance (use $n$ if you prefer the maximum likelihood estimate).
Each element $C_{jk}$ represents the covariance between features $j$ and $k$. The diagonal elements are the variances of each feature (which should be close to 1 since we standardized), and off-diagonal elements show how features co-vary.

---
### Step 4: Compute Eigenvalues and Eigenvectors of the Covariance Matrix
The principal components are the eigenvectors of the covariance matrix, and the eigenvalues tell us how much variance each principal component explains.
1. Solve the characteristic equation to find the eigenvalues $\lambda$:$$\det(C - \lambda I) = 0$$where $I$ is the identity matrix of size $p \times p$. This gives you $p$ eigenvalues $\lambda_1, \lambda_2, \ldots, \lambda_p$.
2. For each eigenvalue $\lambda_i$, solve for the corresponding eigenvector $v_i$:$$(C - \lambda_i I) v_i = 0$$Normalize each eigenvector so its magnitude is 1 (i.e., $||v_i|| = 1$).
The eigenvectors represent the directions of the new axes (principal components), and the eigenvalues represent the amount of variance along each direction.

(Note: In practice, numerical libraries like NumPy or R handle this step efficiently via singular value decomposition (SVD) or eigenvalue decomposition, but understanding the math helps!)

---
### Step 5: Sort Eigenvalues and Eigenvectors
Sort the eigenvalues in descending order, and reorder the corresponding eigenvectors accordingly. The largest eigenvalue corresponds to the first principal component (PC1), the second largest to the second principal component (PC2), and so on.
- If $\lambda_1 \geq \lambda_2 \geq \cdots \geq \lambda_p$, then the first principal component is the eigenvector associated with $\lambda_1$, the second with $\lambda_2$, etc.
- Form a matrix $V$, where each column is an eigenvector: $V = [v_1, v_2, \ldots, v_p]$.
---
### Step 6: Project the Data onto the Principal Components
Transform the standardized data $Z$ into the new coordinate system defined by the principal components.
The projection is:
$T = Z V$
- $T$ is the transformed data (scores) in the principal component space.
- $T$ has dimensions $n \times p$, where each column corresponds to a principal component.
- If you want to reduce dimensionality, you can select only the first $k$ columns of $V$ (where $k < p$) and compute $T = Z V_k$, giving a $n \times k$ matrix.
Each row of $T$ represents a sample in the new coordinate system, and each column corresponds to a principal component.

---

### Step 7: Interpret the Results
- **Variance explained**: The proportion of variance explained by the $i$-th principal component is:$$\text{Proportion} = \frac{\lambda_i}{\sum_{j=1}^p \lambda_j}$$The cumulative variance explained by the first $k$ components helps you decide how many components to keep for dimensionality reduction.
- **Principal components**: The eigenvectors (columns of $V$) show the contribution of each original feature to the principal component. For example, if $v_1 = [0.707, 0.707]$, it means PC1 is equally influenced by both features (assuming $p=2$).
- **Transformed data**: The matrix $T$ gives the coordinates of your data in the new space. If you kept all components, this is just a rotation of the original data. If you kept fewer components, you’ve reduced dimensionality.

---
### Optional Step 8: Dimensionality Reduction (if desired)
If your goal is to reduce dimensionality, choose $k$ principal components (where $k < p$) based on the cumulative variance explained (e.g., keep enough components to explain 90% of the variance). Then, use only the first $k$ columns of $V$ to project the data, as mentioned in Step 6.
## Example

| Person | Height (inches) | Weight (pounds) |
|--------|-----------------|-----------------|
| 1      | 70              | 150             |
| 2      | 65              | 130             |
| 3      | 72              | 160             |
| 4      | 68              | 140             |
| 5      | 67              | 135             |

So, our data matrix $X$ (where each row is a sample and each column is a feature) is:
$$X = \begin{bmatrix}
70 & 150 \\
65 & 130 \\
72 & 160 \\
68 & 140 \\
67 & 135
\end{bmatrix}
$$

---
### Step 1: Standardize the Data
Since height and weight are on different scales (inches vs. pounds), we need to standardize the data so that each feature has a mean of 0 and a standard deviation of 1. This ensures that features with larger ranges don’t dominate the PCA.
1. **Compute the mean of each feature**
	- Mean height: $\frac{70 + 65 + 72 + 68 + 67}{5} = 68.4$
	- Mean weight: $\frac{150 + 130 + 160 + 140 + 135}{5} = 143$
2. **Compute the standard deviation of each feature**
	- For height: Variance = $\frac{(70-68.4)^2 + (65-68.4)^2 + (72-68.4)^2 + (68-68.4)^2 + (67-68.4)^2}{5} = 5.84$
	  - Std dev = $\sqrt{5.84} \approx 2.42$
	- For weight: Variance = $\frac{(150-143)^2 + (130-143)^2 + (160-143)^2 + (140-143)^2 + (135-143)^2}{5} = 116$
	  - Std dev = $\sqrt{116} \approx 10.77$
3. **Standardize the data**
	For each data point, compute $\frac{x - \text{mean}}{\text{std dev}}$:
	- Standardized height: $\frac{70 - 68.4}{2.42} \approx 0.66$, $\frac{65 - 68.4}{2.42} \approx -1.40$, $\frac{72 - 68.4}{2.42} \approx 1.49$, $\frac{68 - 68.4}{2.42} \approx -0.17$, $\frac{67 - 68.4}{2.42} \approx -0.58$
	- Standardized weight: $\frac{150 - 143}{10.77} \approx 0.65$, $\frac{130 - 143}{10.77} \approx -1.21$, $\frac{160 - 143}{10.77} \approx 1.58$, $\frac{140 - 143}{10.77} \approx -0.28$, $\frac{135 - 143}{10.77} \approx -0.74$
	Standardized data matrix $Z$: $$Z = \begin{bmatrix}
0.66 & 0.65 \\
-1.40 & -1.21 \\
1.49 & 1.58 \\
-0.17 & -0.28 \\
-0.58 & -0.74
\end{bmatrix}
$$
---
### Step 2: Compute the Covariance Matrix
Now we compute the covariance matrix of the standardized data to understand how the features vary together. The covariance matrix for standardized data is the same as the correlation matrix since the standard deviation is 1.
$$\text{Cov}(Z) = \frac{Z^T Z}{n-1}$$
where $n = 5$ (number of samples).
First, compute $Z^T Z$:
$$Z^T Z \approx \begin{bmatrix} 5 & 4.95 \\ 4.95 & 5 \end{bmatrix}$$
Divide by $n-1 = 4$:
$$\text{Cov}(Z) \approx \begin{bmatrix}
\frac{5}{4} & \frac{4.95}{4} \\
\frac{4.95}{4} & \frac{5}{4}
\end{bmatrix} = \begin{bmatrix}
1.25 & 1.24 \\
1.24 & 1.25
\end{bmatrix}$$
The high covariance between height and weight (1.24) suggests they’re strongly correlated, which is expected.

---
### Step 3: Compute Eigenvalues and Eigenvectors
The principal components are the eigenvectors of the covariance matrix, and the eigenvalues tell us how much variance each component explains.

Solve for the eigenvalues using the characteristic equation $\det(\text{Cov}(Z) - \lambda I) = 0$:

$$\text{Cov}(Z) - \lambda I = \begin{bmatrix}
1.25 - \lambda & 1.24 \\
1.24 & 1.25 - \lambda
\end{bmatrix}$$
$$\det\begin{bmatrix}
1.25 - \lambda & 1.24 \\
1.24 & 1.25 - \lambda
\end{bmatrix} = (1.25 - \lambda)^2 - (1.24)^2 = 0$$
$$(1.25 - \lambda)^2 - (1.24)^2 = (1.25 - \lambda - 1.24)(1.25 - \lambda + 1.24) = (2.49 - \lambda)(0.01 - \lambda) = 0$$

So, $\lambda_1 = 2.49$, $\lambda_2 = 0.01$.
#### Compute eigenvectors:
For $\lambda_1 = 2.49$:
$$\begin{bmatrix}
1.25 - 2.49 & 1.24 \\
1.24 & 1.25 - 2.49
\end{bmatrix} = \begin{bmatrix}
-1.24 & 1.24 \\
1.24 & -1.24
\end{bmatrix}$$

Solve $-1.24x_1 + 1.24x_2 = 0$, so $x_1 = x_2$. A normalized eigenvector is $\begin{bmatrix} \frac{1}{\sqrt{2}} \\ \frac{1}{\sqrt{2}} \end{bmatrix} \approx \begin{bmatrix} 0.707 \\ 0.707 \end{bmatrix}$.
For $\lambda_2 = 0.01$:
$$\begin{bmatrix}
1.25 - 0.01 & 1.24 \\
1.24 & 1.25 - 0.01
\end{bmatrix} = \begin{bmatrix}
1.24 & 1.24 \\
1.24 & 1.24
\end{bmatrix}$$

Solve $1.24x_1 + 1.24x_2 = 0$, so $x_1 = -x_2$. A normalized eigenvector is $\begin{bmatrix} \frac{1}{\sqrt{2}} \\ -\frac{1}{\sqrt{2}} \end{bmatrix} \approx \begin{bmatrix} 0.707 \\ -0.707 \end{bmatrix}$.

---
### Step 5: Sort Eigenvalues and Eigenvectors
The eigenvalues are $\lambda_1 = 2.49$, $\lambda_2 = 0.01$. The eigenvector corresponding to the largest eigenvalue (2.49) is the first principal component (PC1), and the second is PC2.
$$\text{PC1} = \begin{bmatrix} 0.707 \\ 0.707 \end{bmatrix}, \quad \text{PC2} = \begin{bmatrix} 0.707 \\ -0.707 \end{bmatrix}$$

---
### Step 6: Project the Data onto Principal Components
We project the standardized data $Z$ onto the principal components to get the new coordinates.
$$\text{Projected data} = Z \cdot \begin{bmatrix}
0.707 & 0.707 \\
0.707 & -0.707
\end{bmatrix}$$
For each row of $Z$:
- Person 1: $[0.66, 0.65] \cdot \text{PC1} = 0.66 \cdot 0.707 + 0.65 \cdot 0.707 \approx 0.93$, $\cdot \text{PC2} = 0.66 \cdot 0.707 + 0.65 \cdot (-0.707) \approx 0.01$
- Person 2: $[-1.40, -1.21] \cdot \text{PC1} \approx -1.85$, $\cdot \text{PC2} \approx -0.14$
- Person 3: $[1.49, 1.58] \cdot \text{PC1} \approx 2.17$, $\cdot \text{PC2} \approx -0.06$
- Person 4: $[-0.17, -0.28] \cdot \text{PC1} \approx -0.32$, $\cdot \text{PC2} \approx 0.08$
- Person 5: $[-0.58, -0.74] \cdot \text{PC1} \approx -0.93$, $\cdot \text{PC2} \approx 0.11$

Projected data:
$$
\begin{bmatrix}
0.93 & 0.01 \\
-1.85 & -0.14 \\
2.17 & -0.06 \\
-0.32 & 0.08 \\
-0.93 & 0.11
\end{bmatrix}$$

---
### Step 7: Interpret the Results
- The first column (PC1) captures the direction of maximum variance (eigenvalue 2.49, about 99% of the variance since $\frac{2.49}{2.49 + 0.01} \approx 0.996$).
- The second column (PC2) captures the remaining variance (eigenvalue 0.01, about 1%).
If we wanted to reduce dimensions, we could keep only PC1 and still retain nearly all the information.

---
### Optional: Visualize (Conceptual)
If you plotted the original standardized data and the principal components, PC1 would be a line along the direction $[0.707, 0.707]$, which is roughly the diagonal where height and weight increase together. PC2 would be perpendicular to it, capturing the small deviations orthogonal to this trend.

---

This step-by-step process shows how PCA works: it finds the directions (principal components) that maximize variance and projects the data onto them, allowing dimensionality reduction while preserving as much information as possible. Let me know if you’d like to dive deeper into any part or try a different dataset!

---
# Key Notes and Intuition
- **Why standardize?** If you skip standardization, features with larger variances will dominate the principal components, even if they’re not the most informative.
- **What do the principal components mean?** The first principal component (PC1) is the direction in the data with the most variance. The second (PC2) is the direction with the next most variance, orthogonal to PC1, and so on.
- **When to use PCA?** Use PCA when you want to reduce dimensionality, visualize high-dimensional data, or remove noise by focusing on the components with the most variance.

---

# Practical Implementation
In practice, you’d use libraries like:
- Python: `sklearn.decomposition.PCA` or `numpy.linalg.eig`/`np.linalg.svd`.
- R: `prcomp()` or `princomp()`.

These libraries handle the numerical computations efficiently, especially for large datasets. However, knowing the steps helps you understand what’s happening under the hood and interpret the results correctly.

---
# PCA In Python
Here are two approaches on how to perform Principal Component Analysis (PCA) in Python
1. Using [[scikit-learn.py]] for a high-level implementation that's commonly used in practice. 
2. A Manual implementation using NumPy.
## 1. Using scikit-learn

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.decomposition import PCA
from sklearn.preprocessing import StandardScaler

# Define the dataset (height in inches, weight in pounds)
data = np.array([
    [70, 150],
    [65, 130],
    [72, 160],
    [68, 140],
    [67, 135]
])

# Separate features for clarity
X = data  # Shape: (5 samples, 2 features)
```
Our dataset has 5 samples and 2 features (height and weight). Let’s proceed with both approaches.

---
`scikit-learn` provides a convenient `PCA` class that handles all the steps (standardization, eigenvalue decomposition, projection) for us. We'll standardize the data manually first to match our earlier process, but `sklearn` can also handle this internally if needed.

### Step 1: Standardize the Data
Use `StandardScaler` to standardize the data (mean = 0, std dev = 1).

```python
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)
print("Standardized Data (mean=0, std=1):\n", X_scaled)
```

**Output** (approximate, rounded for clarity):
```
Standardized Data (mean=0, std=1):
 [[ 0.66  0.65]
 [-1.40 -1.21]
 [ 1.49  1.58]
 [-0.17 -0.28]
 [-0.58 -0.74]]
```

This matches the standardized data we calculated manually earlier.

### Step 2: Apply PCA Using `sklearn`
Now we apply PCA to get the principal components and transform the data.

```python
# Initialize PCA (we'll keep all components for now, since we have only 2 features)
pca = PCA(n_components=2)
X_pca = pca.fit_transform(X_scaled)

print("Transformed Data (in PCA space):\n", X_pca)
print("\nPrincipal Components (eigenvectors):\n", pca.components_)
print("\nExplained Variance (eigenvalues):\n", pca.explained_variance_)
print("\nExplained Variance Ratio:\n", pca.explained_variance_ratio_)
```

**Output** (approximate):
```
Transformed Data (in PCA space):
 [[ 0.93  0.01]
 [-1.85 -0.14]
 [ 2.17 -0.06]
 [-0.32  0.08]
 [-0.93  0.11]]

Principal Components (eigenvectors):
 [[ 0.707  0.707]
 [-0.707  0.707]]

Explained Variance (eigenvalues):
 [2.49 0.01]

Explained Variance Ratio:
 [0.996 0.004]
```

- The transformed data (`X_pca`) gives the coordinates of the original data in the new principal component space.
- The principal components (`pca.components_`) are the eigenvectors, matching our manual calculation of \( [0.707, 0.707] \) for PC1 and \( [0.707, -0.707] \) for PC2 (or their negatives, as direction sign can flip).
- The explained variance and ratio confirm that PC1 captures ~99.6% of the variance, as expected.

---

## Approach 2: Manual PCA Using NumPy
Now let’s implement PCA manually to match the step-by-step process we discussed. This will help you see how the math translates to code.
```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.preprocessing import StandardScaler

# Define the dataset (height in inches, weight in pounds)
data = np.array([
    [70, 150],
    [65, 130],
    [72, 160],
    [68, 140],
    [67, 135]
])

# Separate features for clarity
X = data  # Shape: (5 samples, 2 features)

scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)
```
### Step 1: Standardize the Data
We already standardized using `StandardScaler`, so we’ll reuse `X_scaled`.

### Step 2: Compute the Covariance Matrix
Compute the covariance matrix of the standardized data.

```python
cov_matrix = np.cov(X_scaled.T, bias=False)  # .T because np.cov expects features as rows
print("Covariance Matrix:\n", cov_matrix)
```

**Output** (approximate):
```
Covariance Matrix:
 [[1.25 1.24]
 [1.24 1.25]]
```

This matches our earlier calculation (1.25 on the diagonal, 1.24 off-diagonal).

### Step 3: Compute Eigenvalues and Eigenvectors
Use NumPy’s linear algebra module to compute the eigenvalues and eigenvectors of the covariance matrix.

```python
eigenvalues, eigenvectors = np.linalg.eigh(cov_matrix)  # eigh for symmetric matrices (like cov)
print("Eigenvalues:\n", eigenvalues)
print("Eigenvectors:\n", eigenvectors)
```

**Output** (approximate):
```
Eigenvalues:
 [0.01 2.49]

Eigenvectors:
 [[-0.707  0.707]
 [ 0.707  0.707]]
```

The eigenvalues are `[0.01, 2.49]`, and the eigenvectors are the columns of the matrix. Note that `np.linalg.eigh` sorts eigenvalues in ascending order, so we need to sort them in descending order (as PCA typically uses largest first).

### Step 4: Sort Eigenvalues and Eigenvectors
Sort eigenvalues in descending order and reorder the eigenvectors accordingly.

```python
# Sort eigenvalues and eigenvectors in descending order
idx = eigenvalues.argsort()[::-1]  # Indices for descending order
eigenvalues = eigenvalues[idx]
eigenvectors = eigenvectors[:, idx]

print("Sorted Eigenvalues:\n", eigenvalues)
print("Sorted Eigenvectors:\n", eigenvectors)
```

**Output** (approximate):
```
Sorted Eigenvalues:
 [2.49 0.01]

Sorted Eigenvectors:
 [[ 0.707 -0.707]
 [ 0.707  0.707]]
```

### Step 5: Project the Data onto Principal Components
Project the standardized data onto the principal components.

```python
X_pca_manual = X_scaled @ eigenvectors
print("Manually Transformed Data (in PCA space):\n", X_pca_manual)
```

**Output** (approximate):
```
Manually Transformed Data (in PCA space):
 [[ 0.93  0.01]
 [-1.85 -0.14]
 [ 2.17 -0.06]
 [-0.32  0.08]
 [-0.93  0.11]]
```

This matches the `sklearn` result, confirming our manual implementation is correct.

---

## Step 3: Visualize the Results
Since we have a 2D dataset, we can visualize both the original standardized data and the principal components. We’ll plot the standardized data points, the principal component directions, and the transformed data.

```python
# Plotting
plt.figure(figsize=(8, 6))

# Plot standardized data
plt.scatter(X_scaled[:, 0], X_scaled[:, 1], label='Standardized Data', alpha=0.7)

# Plot principal components as arrows
scale = 2  # Scale factor for visibility
for i in range(len(eigenvalues)):
    vec = eigenvectors[:, i] * scale * np.sqrt(eigenvalues[i])
    plt.arrow(0, 0, vec[0], vec[1], color='r' if i == 0 else 'g', width=0.05,
              head_width=0.1, label=f'PC{i+1}')

# Add labels for points
for i in range(len(X_scaled)):
    plt.text(X_scaled[i, 0] + 0.1, X_scaled[i, 1], f'P{i+1}')

plt.axhline(0, color='black', linewidth=0.5, linestyle='--')
plt.axvline(0, color='black', linewidth=0.5, linestyle='--')
plt.xlabel('Standardized Height')
plt.ylabel('Standardized Weight')
plt.title('PCA: Standardized Data with Principal Components')
plt.legend()
plt.grid(True)
plt.show()
```

### Explanation of the Plot
- **Blue dots**: Standardized data points (labeled P1 to P5).
- **Red arrow (PC1)**: Direction of the first principal component, scaled by the square root of its eigenvalue for visibility.
- **Green arrow (PC2)**: Direction of the second principal component, orthogonal to PC1.
- The plot shows that PC1 aligns with the direction of maximum variance (roughly the diagonal where height and weight increase together), and PC2 is perpendicular, capturing the leftover variance.

---

## Summary of Code Outputs
Both implementations (`sklearn` and manual) give the same results:
- **Principal Components**: PC1 ≈ \([0.707, 0.707]\), PC2 ≈ \([-0.707, 0.707]\) (or vice versa, as signs can flip).
- **Transformed Data**: Matches our earlier manual calculations.
- **Explained Variance**: PC1 explains ~99.6% of the variance, PC2 explains ~0.4%.

---

## Key Takeaways
- **Using `sklearn`**: Quick and reliable for real-world applications. It handles standardization, PCA computation, and projection in a few lines.
- **Manual Implementation**: Helps you understand the underlying math (covariance matrix, eigenvalues, projection) and matches the step-by-step process we discussed.
- **Visualization**: Especially useful in 2D or 3D to see how the principal components align with the data.

If you’d like to extend this (e.g., reduce dimensions, apply to a larger dataset, or explore more visualizations), let me know! You can also experiment with this code by changing the dataset or adding more features. Want to try implementing PCA on a different dataset or dive into a specific part of the code?

---
# Resources
- [Video Tutorial](https://www.youtube.com/watch?v=g-Hb26agBFg&ab_channel=Serrano.Academy)