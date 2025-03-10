**K-Means Clustering** is an **unsupervised machine learning** algorithm used to divide a dataset into **K clusters** (groups) based on feature similarity. It’s widely used for tasks like customer segmentation, image compression, anomaly detection, and more.

The goal of K-means is to partition the data into **K clusters** in such a way that the **intra-cluster similarity** is maximized (points in the same cluster are similar to each other) and the **inter-cluster similarity** is minimized (points from different clusters are as different as possible).

---
### **Steps of K-Means Clustering**

1. **Choose the number of clusters, K.**
2. **Initialize the centroids.**
    - Randomly select K data points as the initial **centroids** (center points of the clusters).
3. **Assign each data point to the nearest centroid.**
    - For each data point, calculate the distance to all centroids and assign the point to the cluster with the closest centroid. This creates K groups.
4. **Update the centroids.**
    - After assigning all points to clusters, recalculate the centroids. The new centroid of each cluster is the mean (average) of all points in that cluster.
5. **Repeat steps 3 and 4 until convergence.**
    - Reassign points to the nearest centroid based on the updated centroids, and then update the centroids again. This loop continues until the centroids stop changing or the change becomes very small, indicating convergence.
6. **Output the final clusters and centroids.**
---
# K-Means Clustering Example

| Data Point | X-coordinate | Y-coordinate |
|------------|--------------|--------------|
| A          | 1            | 2            |
| B          | 2            | 3            |
| C          | 3            | 3            |
| D          | 8            | 8            |
| E          | 9            | 9            |
| F          | 10           | 10           |
We will perform K-Means clustering to divide this dataset into two clusters. We will track the process through each **iteration**.

---
### Step 1: Initialize K = 2 clusters
We first choose \( K = 2 \) (two clusters). Next, we randomly initialize the centroids of these clusters.
- **Centroid 1**: \( (1, 2) \)
- **Centroid 2**: \( (8, 8) \)
---
### Step 2: Assign Data Points to Nearest Centroid

Next, we calculate the **Euclidean distance** between each data point and the centroids to assign the points to the nearest cluster.
#### Euclidean Distance Formula:
$\text{Distance} = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}$
Let’s calculate the distances from each point to both centroids.
#### Distance from each data point to Centroid 1 (1, 2):
- **A**:$\sqrt{(1 - 1)^2 + (2 - 2)^2} = 0$
- **B**:$\sqrt{(2 - 1)^2 + (3 - 2)^2} = \sqrt{1+1} = 1.414$
- **C**:$\sqrt{(3 - 1)^2 + (3 - 2)^2} = \sqrt{4+1} = 2.236$
- **D**:$\sqrt{(8 - 1)^2 + (8 - 2)^2} = \sqrt{49+36} = 8.062$
- **E**:$\sqrt{(9 - 1)^2 + (9 - 2)^2} = \sqrt{64+49} = 10.630$
- **F**:$\sqrt{(10 - 1)^2 + (10 - 2)^2} = \sqrt{81+64} = 12.042$
#### Distance from each data point to Centroid 2 (8, 8):
- **A**:$\sqrt{(1 - 8)^2 + (2 - 8)^2} = \sqrt{49+36} = 8.062$
- **B**:$\sqrt{(2 - 8)^2 + (3 - 8)^2} = \sqrt{36+25} = 7.810$
- **C**:$\sqrt{(3 - 8)^2 + (3 - 8)^2} = \sqrt{25+25} = 7.071$
- **D**:$\sqrt{(8 - 8)^2 + (8 - 8)^2} = 0$
- **E**:$\sqrt{(9 - 8)^2 + (9 - 8)^2} = \sqrt{1+1} = 1.414$
- **F**:$\sqrt{(10 - 8)^2 + (10 - 8)^2} = \sqrt{4+4} = 2.828$
#### Assigning Points to the Nearest Centroid:
- **A**: Centroid 1 (Distance 0)
- **B**: Centroid 1 (Distance 1.414)
- **C**: Centroid 1 (Distance 2.236)
- **D**: Centroid 2 (Distance 0)
- **E**: Centroid 2 (Distance 1.414)
- **F**: Centroid 2 (Distance 2.828)
So after the first assignment, we have:
- **Cluster 1 (Centroid 1)**: A, B, C
- **Cluster 2 (Centroid 2)**: D, E, F
---
### Step 3: Update the Centroids
Next, we calculate the new centroids of the clusters by finding the mean (average) of the points in each cluster.
#### New Centroid 1 (for Cluster 1):
- Points in Cluster 1: A (1, 2), B (2, 3), C (3, 3)
- Mean of X-coordinates:$\frac{1+2+3}{3} = 2$
- Mean of Y-coordinates:$\frac{2+3+3}{3} = 2.67$
So, **New Centroid 1**:$(2, 2.67)$
#### New Centroid 2 (for Cluster 2):
- Points in Cluster 2: D (8, 8), E (9, 9), F (10, 10)
- Mean of X-coordinates:$\frac{8+9+10}{3} = 9$
- Mean of Y-coordinates:$\frac{8+9+10}{3} = 9$
So, **New Centroid 2**:$(9, 9)$
---
### Step 4: Reassign Data Points to New Centroids
We now reassign the data points based on the new centroids. Again, we calculate the Euclidean distances from each data point to both centroids.
#### Distance from each data point to Centroid 1 (2, 2.67):

- **A**:$\sqrt{(1 - 2)^2 + (2 - 2.67)^2} = \sqrt{1+0.4489} = 1.073$
- **B**:$\sqrt{(2 - 2)^2 + (3 - 2.67)^2} = \sqrt{0+0.1089} = 0.33$
- **C**:$\sqrt{(3 - 2)^2 + (3 - 2.67)^2} = \sqrt{1+0.1089} = 1.063$
- **D**:$\sqrt{(8 - 2)^2 + (8 - 2.67)^2} = \sqrt{36+28.299} = 7.874$
- **E**:$\sqrt{(9 - 2)^2 + (9 - 2.67)^2} = \sqrt{49+39.0289} = 8.360$
- **F**:$\sqrt{(10 - 2)^2 + (10 - 2.67)^2} = \sqrt{64+53.7289} = 9.277$
#### Distance from each data point to Centroid 2 (9, 9):
- **A**:$\sqrt{(1 - 9)^2 + (2 - 9)^2} = \sqrt{64+49} = 10.630$
- **B**:$\sqrt{(2 - 9)^2 + (3 - 9)^2} = \sqrt{49+36} = 8.062$
- **C**:$\sqrt{(3 - 9)^2 + (3 - 9)^2} = \sqrt{36+36} = 8.485$
- **D**:$\sqrt{(8 - 9)^2 + (8 - 9)^2} = \sqrt{1+1} = 1.414$
- **E**:$\sqrt{(9 - 9)^2 + (9 - 9)^2} = 0$
- **F**:$\sqrt{(10 - 9)^2 + (10 - 9)^2} = \sqrt{1+1} = 1.414$
#### Reassigning Data Points:
- **A**: Closer to Centroid 1 (Distance 1.073)
- **B**: Closer to Centroid 1 (Distance 0.33)
- **C**: Closer to Centroid 1 (Distance 1.063)
- **D**: Closer to Centroid 2 (Distance 1.414)
- **E**: Closer to Centroid 2 (Distance 0)
- **F**: Closer to Centroid 2 (Distance 1.414)
So after the second iteration:
- **Cluster 1 (Centroid 1)**: A, B, C
- **Cluster 2 (Centroid 2)**: D, E, F
---
### Step 5: Check for Convergence
The centroids have not changed (Centroid 1 is still$(2, 2.67)$and Centroid 2 is still$(9, 9)$), so the algorithm has **converged**. No further updates to the centroids or data point assignments will occur.

---
### Final Clusters:
- **Cluster 1**: A (1, 2), B (2, 3), C (3, 3)
- **Cluster 2**: D (8, 8), E (9, 9), F (10, 10)
---
### Exercise 1: Basic Clustering

| Data Point | X-coordinate | Y-coordinate |
| ---------- | ------------ | ------------ |
| A          | 1            | 2            |
| B          | 2            | 2            |
| C          | 3            | 1            |
| D          | 8            | 7            |
| E          | 9            | 6            |
| F          | 10           | 7            |
Perform K-Means clustering on the dataset above using K=2 (two clusters).

---
### Exercise 2: Clustering with Three Clusters

| Data Point | X-coordinate | Y-coordinate |
| ---------- | ------------ | ------------ |
| A          | 1            | 1            |
| B          | 2            | 1            |
| C          | 3            | 1            |
| D          | 8            | 8            |
| E          | 9            | 8            |
| F          | 10           | 8            |
| G          | 15           | 5            |
| H          | 16           | 5            |
| I          | 17           | 5            |
Perform K-Means clustering on the dataset above using K=3 (three clusters).

---
# Solutions
## Exercise 1: Basic Clustering

| Data Point | X-coordinate | Y-coordinate |
|------------|--------------|--------------|
| A          | 1            | 2            |
| B          | 2            | 2            |
| C          | 3            | 1            |
| D          | 8            | 7            |
| E          | 9            | 6            |
| F          | 10           | 7            |
### Step 1: Initialize K = 2 clusters
We initialize two random centroids:
- **Centroid 1**: \( (1, 2) \)
- **Centroid 2**: \( (8, 7) \)
---
### Step 2: Assign Data Points to Nearest Centroid
Now we calculate the **Euclidean distance** between each data point and the centroids.
#### Euclidean Distance Formula:
$\text{Distance} = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}$
#### Distance from each data point to Centroid 1 (1, 2):
- **A**: $\sqrt{(1 - 1)^2 + (2 - 2)^2} = 0$
- **B**: $\sqrt{(2 - 1)^2 + (2 - 2)^2} = 1$
- **C**: $\sqrt{(3 - 1)^2 + (1 - 2)^2} = \sqrt{4 + 1} = 2.236$
- **D**: $\sqrt{(8 - 1)^2 + (7 - 2)^2} = \sqrt{49 + 25} = 8.062$
- **E**: $\sqrt{(9 - 1)^2 + (6 - 2)^2} = \sqrt{64 + 16} = 8.944$
- **F**: $\sqrt{(10 - 1)^2 + (7 - 2)^2} = \sqrt{81 + 25} = 9.110$
#### Distance from each data point to Centroid 2 (8, 7):
- **A**: $\sqrt{(1 - 8)^2 + (2 - 7)^2} = \sqrt{49 + 25} = 8.062$
- **B**: $\sqrt{(2 - 8)^2 + (2 - 7)^2} = \sqrt{36 + 25} = 7.810$
- **C**: $\sqrt{(3 - 8)^2 + (1 - 7)^2} = \sqrt{25 + 36} = 7.810$
- **D**: $\sqrt{(8 - 8)^2 + (7 - 7)^2} = 0$
- **E**: $\sqrt{(9 - 8)^2 + (6 - 7)^2} = \sqrt{1 + 1} = 1.414$
- **F**: $\sqrt{(10 - 8)^2 + (7 - 7)^2} = \sqrt{4 + 0} = 2$
#### Assigning Points to the Nearest Centroid:
- **A**: Closer to Centroid 1 (Distance 0)
- **B**: Closer to Centroid 1 (Distance 1)
- **C**: Closer to Centroid 1 (Distance 2.236)
- **D**: Closer to Centroid 2 (Distance 0)
- **E**: Closer to Centroid 2 (Distance 1.414)
- **F**: Closer to Centroid 2 (Distance 2)
So after the first assignment:
- **Cluster 1**: A, B, C
- **Cluster 2**: D, E, F
---
### Step 3: Update the Centroids
We now calculate the new centroids by averaging the points in each cluster.
#### New Centroid 1 (for Cluster 1):
- Points in Cluster 1: A (1, 2), B (2, 2), C (3, 1)
- Mean of X-coordinates: $\frac{1+2+3}{3} = 2$
- Mean of Y-coordinates: $\frac{2+2+1}{3} = 1.67$
So, **New Centroid 1**: \( (2, 1.67) \)
#### New Centroid 2 (for Cluster 2):
- Points in Cluster 2: D (8, 7), E (9, 6), F (10, 7)
- Mean of X-coordinates: $\frac{8+9+10}{3} = 9$
- Mean of Y-coordinates: $\frac{7+6+7}{3} = 6.67$
So, **New Centroid 2**: \( (9, 6.67) \)
---
### Step 4: Reassign Data Points to New Centroids
We now reassign the data points based on the new centroids and calculate the Euclidean distances again.
#### Distance from each data point to New Centroid 1 (2, 1.67):
- **A**: $\sqrt{(1 - 2)^2 + (2 - 1.67)^2} = \sqrt{1+0.1089} = 1.074$
- **B**: $\sqrt{(2 - 2)^2 + (2 - 1.67)^2} = \sqrt{0+0.1089} = 0.33$
- **C**: $\sqrt{(3 - 2)^2 + (1 - 1.67)^2} = \sqrt{1+0.4489} = 1.073$
- **D**: $\sqrt{(8 - 2)^2 + (7 - 1.67)^2} = \sqrt{36+28.299} = 7.874$
- **E**: $\sqrt{(9 - 2)^2 + (6 - 1.67)^2} = \sqrt{49+18.5289} = 8.360$
- **F**: $\sqrt{(10 - 2)^2 + (7 - 1.67)^2} = \sqrt{64+28.299} = 8.890$
#### Distance from each data point to New Centroid 2 (9, 6.67):
- **A**: $\sqrt{(1 - 9)^2 + (2 - 6.67)^2} = \sqrt{64+22.0889} = 8.318$
- **B**: $\sqrt{(2 - 9)^2 + (2 - 6.67)^2} = \sqrt{49+22.0889} = 7.701$
- **C**: $\sqrt{(3 - 9)^2 + (1 - 6.67)^2} = \sqrt{36+31.0889} = 7.940$
- **D**: $\sqrt{(8 - 9)^2 + (7 - 6.67)^2} = \sqrt{1+0.1089} = 1.074$
- **E**: $\sqrt{(9 - 9)^2 + (6 - 6.67)^2} = \sqrt{0+0.4489} = 0.67$
- **F**: $\sqrt{(10 - 9)^2 + (7 - 6.67)^2} = \sqrt{1+0.1089} = 1.074$
#### Reassigning Data Points:
- **A**: Closer to Centroid 1 (Distance 1.074)
- **B**: Closer to Centroid 1 (Distance 0.33)
- **C**: Closer to Centroid 1 (Distance 1.073)
- **D**: Closer to Centroid 2 (Distance 1.074)
- **E**: Closer to Centroid 2 (Distance 0.67)
- **F**: Closer to Centroid 2 (Distance 1.074)
Since the centroids didn't change significantly, **the algorithm has converged**.
---
### Final Clusters:
- **Cluster 1**: A (1, 2), B (2, 2), C (3, 1)
- **Cluster 2**: D (8, 7), E (9, 6), F (10, 7)
---
## Exercise 2: Clustering with Three Clusters

| Data Point | X-coordinate | Y-coordinate |
|------------|--------------|--------------|
| A          | 1            | 1            |
| B          | 2            | 1            |
| C          | 3            | 1            |
| D          | 8            | 8            |
| E          | 9            | 8            |
| F          | 10           | 8            |
| G          | 15           | 5            |
| H          | 16           | 5            |
| I          | 17           | 5            |
### Step 1: Initialize K = 3 clusters
We initialize three random centroids:
- **Centroid 1**: \( (1, 1) \)
- **Centroid 2**: \( (9, 8) \)
- **Centroid 3**: \( (15, 5) \)
---
### Step 2: Assign Data Points to Nearest Centroid
#### Distance from each data point to Centroid 1 (1, 1):
- **A**: $\sqrt{(1 - 1)^2 + (1 - 1)^2} = 0$
- **B**: $\sqrt{(2 - 1)^2 + (1 - 1)^2} = 1$
- **C**: $\sqrt{(3 - 1)^2 + (1 - 1)^2} = 2$
- **D**: $\sqrt{(8 - 1)^2 + (8 - 1)^2} = \sqrt{49+49} = 9.899$
- **E**: $\sqrt{(9 - 1)^2 + (8 - 1)^2} = \sqrt{64+49} = 10.630$
- **F**: $\sqrt{(10 - 1)^2 + (8 - 1)^2} = \sqrt{81+49} = 11.401$
- **G**: $\sqrt{(15 - 1)^2 + (5 - 1)^2} = \sqrt{196+16} = 14.966$
- **H**: $\sqrt{(16 - 1)^2 + (5 - 1)^2} = \sqrt{225+16} = 15.132$
- **I**: $\sqrt{(17 - 1)^2 + (5 - 1)^2} = \sqrt{256+16} = 16.248$
#### Distance from each data point to Centroid 2 (9, 8):
- **A**: $\sqrt{(1 - 9)^2 + (1 - 8)^2} = \sqrt{64+49} = 10.630$
- **B**: $\sqrt{(2 - 9)^2 + (1 - 8)^2} = \sqrt{49+49} = 9.899$
- **C**: $\sqrt{(3 - 9)^2 + (1 - 8)^2} = \sqrt{36+49} = 8.062$
- **D**: $\sqrt{(8 - 9)^2 + (8 - 8)^2} = 1$
- **E**: $\sqrt{(9 - 9)^2 + (8 - 8)^2} = 0$
- **F**: $\sqrt{(10 - 9)^2 + (8 - 8)^2} = 1$
- **G**: $\sqrt{(15 - 9)^2 + (5 - 8)^2} = \sqrt{36+9} = 6.708$
- **H**: $\sqrt{(16 - 9)^2 + (5 - 8)^2} = \sqrt{49+9} = 7.810$
- **I**: $\sqrt{(17 - 9)^2 + (5 - 8)^2} = \sqrt{64+9} = 8.062$
#### Distance from each data point to Centroid 3 (15, 5):
- **A**: $\sqrt{(1 - 15)^2 + (1 - 5)^2} = \sqrt{196+16} = 14.966$
- **B**: $\sqrt{(2 - 15)^2 + (1 - 5)^2} = \sqrt{169+16} = 13.038$
- **C**: $\sqrt{(3 - 15)^2 + (1 - 5)^2} = \sqrt{144+16} = 12.165$
- **D**: $\sqrt{(8 - 15)^2 + (8 - 5)^2} = \sqrt{49+9} = 7.810$
- **E**: $\sqrt{(9 - 15)^2 + (8 - 5)^2} = \sqrt{36+9} = 6.708$
- **F**: $\sqrt{(10 - 15)^2 + (8 - 5)^2} = \sqrt{25+9} = 5$
- **G**: $\sqrt{(15 - 15)^2 + (5 - 5)^2} = 0$
- **H**: $\sqrt{(16 - 15)^2 + (5 - 5)^2} = 1$
- **I**: $\sqrt{(17 - 15)^2 + (5 - 5)^2} = 2$
---
### Assigning Data Points to the Nearest Centroid:
- **A**: Closer to Centroid 1 (Distance 0)
- **B**: Closer to Centroid 1 (Distance 1)
- **C**: Closer to Centroid 1 (Distance 2)
- **D**: Closer to Centroid 2 (Distance 1)
- **E**: Closer to Centroid 2 (Distance 0)
- **F**: Closer to Centroid 2 (Distance 1)
- **G**: Closer to Centroid 3 (Distance 0)
- **H**: Closer to Centroid 3 (Distance 1)
- **I**: Closer to Centroid 3 (Distance 2)
---
### Final Clusters:
- **Cluster 1**: A (1, 1), B (2, 1), C (3, 1)
- **Cluster 2**: D (8, 8), E (9, 8), F (10, 8)
- **Cluster 3**: G (15, 5), H (16, 5), I (17, 5)
The algorithm has converged, and the final clusters are determined.