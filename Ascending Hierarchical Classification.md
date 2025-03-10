# Ascending Hierarchical Classification: Step-by-Step Example

We have five data points in a 2D space:
\[ A = (1, 2), \, B = (2, 2), \, C = (3, 4), \, D = (5, 6), \, E = (8, 8) \]
We will use **Single Linkage** (minimum distance between clusters).

---

## Step 1: Start with Each Data Point as a Cluster
Initially, each point is its own cluster:
\[
\{A\}, \{B\}, \{C\}, \{D\}, \{E\}
\]

---

## Step 2: Compute Pairwise Distances
Using the Euclidean distance formula:

\[
d(p, q) = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}
\]

Calculate distances between all pairs:

1. \( d(A, B) = \sqrt{(2 - 1)^2 + (2 - 2)^2} = \sqrt{1} = 1 \)
2. \( d(A, C) = \sqrt{(3 - 1)^2 + (4 - 2)^2} = \sqrt{4 + 4} = \sqrt{8} \approx 2.83 \)
3. \( d(A, D) = \sqrt{(5 - 1)^2 + (6 - 2)^2} = \sqrt{16 + 16} = \sqrt{32} \approx 5.66 \)
4. \( d(A, E) = \sqrt{(8 - 1)^2 + (8 - 2)^2} = \sqrt{49 + 36} = \sqrt{85} \approx 9.22 \)
5. \( d(B, C) = \sqrt{(3 - 2)^2 + (4 - 2)^2} = \sqrt{1 + 4} = \sqrt{5} \approx 2.24 \)
6. \( d(B, D) = \sqrt{(5 - 2)^2 + (6 - 2)^2} = \sqrt{9 + 16} = \sqrt{25} = 5 \)
7. \( d(B, E) = \sqrt{(8 - 2)^2 + (8 - 2)^2} = \sqrt{36 + 36} = \sqrt{72} \approx 8.49 \)
8. \( d(C, D) = \sqrt{(5 - 3)^2 + (6 - 4)^2} = \sqrt{4 + 4} = \sqrt{8} \approx 2.83 \)
9. \( d(C, E) = \sqrt{(8 - 3)^2 + (8 - 4)^2} = \sqrt{25 + 16} = \sqrt{41} \approx 6.40 \)
10. \( d(D, E) = \sqrt{(8 - 5)^2 + (8 - 6)^2} = \sqrt{9 + 4} = \sqrt{13} \approx 3.61 \)

---

## Step 3: Merge the Closest Clusters
- Identify the smallest distance. The smallest distance is \( d(A, B) = 1 \).
- Merge \( \{A\} \) and \( \{B\} \) into a new cluster \( \{A, B\} \).

New clusters:
\[
\{A, B\}, \{C\}, \{D\}, \{E\}
\]

---

## Step 4: Update Distances
Using **Single Linkage**, the distance between \( \{A, B\} \) and another cluster is the **minimum distance** between any point in \( \{A, B\} \) and the points in the other cluster.

- \( d(\{A, B\}, C) = \min(d(A, C), d(B, C)) = \min(2.83, 2.24) = 2.24 \)
- \( d(\{A, B\}, D) = \min(d(A, D), d(B, D)) = \min(5.66, 5) = 5 \)
- \( d(\{A, B\}, E) = \min(d(A, E), d(B, E)) = \min(9.22, 8.49) = 8.49 \)

Updated distances:
\[
\{A, B\}-C: 2.24, \quad \{A, B\}-D: 5, \quad \{A, B\}-E: 8.49, \quad C-D: 2.83, \quad C-E: 6.40, \quad D-E: 3.61
\]

---

## Step 5: Merge the Closest Clusters
- The smallest distance is \( d(\{A, B\}, C) = 2.24 \).
- Merge \( \{A, B\} \) and \( \{C\} \) into a new cluster \( \{A, B, C\} \).

New clusters:
\[
\{A, B, C\}, \{D\}, \{E\}
\]

---

## Step 6: Update Distances
- \( d(\{A, B, C\}, D) = \min(d(A, D), d(B, D), d(C, D)) = \min(5.66, 5, 2.83) = 2.83 \)
- \( d(\{A, B, C\}, E) = \min(d(A, E), d(B, E), d(C, E)) = \min(9.22, 8.49, 6.40) = 6.40 \)

Updated distances:
\[
\{A, B, C\}-D: 2.83, \quad \{A, B, C\}-E: 6.40, \quad D-E: 3.61
\]

---

## Step 7: Merge the Closest Clusters
- The smallest distance is \( d(\{A, B, C\}, D) = 2.83 \).
- Merge \( \{A, B, C\} \) and \( \{D\} \) into a new cluster \( \{A, B, C, D\} \).

New clusters:
\[
\{A, B, C, D\}, \{E\}
\]

---

## Step 8: Merge the Final Clusters
- The last distance is \( d(\{A, B, C, D\}, E) = 6.40 \).
- Merge \( \{A, B, C, D\} \) and \( \{E\} \) into a single cluster \( \{A, B, C, D, E\} \).

Final cluster:
\[
\{A, B, C, D, E\}
\]

---

## Step 9: Visualize with a Dendrogram
A dendrogram for this process:

