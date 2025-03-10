### **K-Nearest Neighbors (KNN) Algorithm**
K-Nearest Neighbors (KNN) is a simple, non-parametric, and lazy machine learning algorithm used for classification and regression. It predicts the class or value of a data point based on the classes or values of its **k nearest neighbors**.

---
### **Steps of KNN**
1. **Choose the Value of k:**
    - Decide the number of neighbors (k) to consider. k is typically a small, odd number like 3 or 5 to avoid ties in classification.
2. **Calculate Distance:**
    - Measure the distance between the new data point and all points in the dataset using a distance metric like:
        - **Euclidean Distance**: $d = \sqrt{\sum_{i=1}^n (x_i - y_i)^2}$
        - **Manhattan Distance**: $d = \sum_{i=1}^n |x_i - y_i|$
        - **Hamming Distance** (for categorical variables) :$d(x,y)=∑n​δ(xi​,yi​)$ where:
			- $\delta(x_i, y_i) = 1, if  x_i \neq y_i ​$
			- $\delta(x_i, y_i) = 0, if xi=yi$
1. **Find the Nearest Neighbors:**
    - Identify the $k$ data points with the smallest distances to the query point.
2. **Vote or Average:**
    - For **classification**: Assign the class that is most frequent among the k neighbors (**majority voting**).
    - For **regression**: Calculate the average or weighted average of the neighbors' values.
3. **Make a Prediction:**
    - Return the predicted class (for classification) or value (for regression).

---
### **Example of KNN for Classification**

| Point | Feature 1 (X1) | Feature 2 (X2) | Class |
| ----- | -------------- | -------------- | ----- |
| A     | 1              | 1              | Red   |
| B     | 2              | 2              | Red   |
| C     | 3              | 3              | Blue  |
| D     | 6              | 6              | Blue  |
**Query Point:** $(X1 = 4, X2 = 4)$

---
#### **Step 1: Choose kk**
Let k=3k = 3.
#### **Step 2: Calculate Distances**

Use **Euclidean Distance** to compute the distance from the query point $(4, 4)$ to each dataset point:
1. Distance to $A (1, 1)$:
    $d = \sqrt{(4-1)^2 + (4-1)^2} = \sqrt{9 + 9} = \sqrt{18} \approx 4.24$
2. Distance to $B (2, 2)$:
    $d = \sqrt{(4-2)^2 + (4-2)^2} = \sqrt{4 + 4} = \sqrt{8} \approx 2.83$
3. Distance to $C (3, 3)$:
    $d = \sqrt{(4-3)^2 + (4-3)^2} = \sqrt{1 + 1} = \sqrt{2} \approx 1.41$
4. Distance to $D (6, 6)$:
    $d = \sqrt{(4-6)^2 + (4-6)^2} = \sqrt{4 + 4} = \sqrt{8} \approx 2.83$
#### **Step 3: Find the Nearest Neighbors**
Sort the points by distance:
- C: d=1.41
- B: d=2.83
- D: d=2.83
The nearest 3 neighbors are **C, B, D**.
#### **Step 4: Majority Voting**
The classes of the nearest neighbors:
- C: Blue
- B: Red
- D: Blue
Count the classes:
- Blue: 2
- Red: 1
The majority class is **Blue**.
#### **Step 5: Make a Prediction**
The query point (4, 4) is predicted to belong to the **Blue** class.

---