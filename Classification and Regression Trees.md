### **CART (Classification and Regression Trees)**
The **CART algorithm** builds decision trees by splitting the dataset at each node into two branches, optimizing a specific criterion. CART supports both **classification** and **regression** tasks and always produces **binary trees** (each split has two branches). Here’s a detailed explanation of the steps with an example for clarity.

---
### **Steps of the CART Algorithm**

#### **1. Choose the Splitting Criterion**
- **Gini Impurity** is used to measure the "purity" of splits.
- Formula: $Gini = 1 - \sum_{i=1}^{C} p_i^2$  Where C is the number of classes, and $p_i$ is the proportion of instances in class $i$.
#### **2. Evaluate All Possible Splits**
- For each feature:
    - Sort the feature values.
    - Consider all possible thresholds for splitting (midpoints between values).
    - Calculate the impurity for each split.
#### **3. Select the Best Split**
- Compute the **weighted average impurity** of the left and right branches for each split: $\text{Weighted Impurity} = \frac{|L|}{|N|} \cdot \text{Impurity}(L) + \frac{|R|}{|N|} \cdot \text{Impurity}(R)$ Where $L$ and $R$ are the left and right subsets, and $|N|$ is the total number of samples.
- Choose the split that minimizes the weighted impurity.
#### **4. Split the Dataset**
- Divide the dataset into two subsets based on the best split.
#### **5. Repeat Recursively**
- Repeat steps 1–4 for each subset until a stopping criterion is met:
    - Maximum tree depth is reached.
    - Minimum number of samples in a node is reached.
    - Impurity improvement is below a threshold.
#### **6. Assign Predictions**
- For classification: Assign the majority class of samples in the node.
- For regression: Assign the mean or median of the target variable in the node.

---

### **Example: Classification Task**

#### **Dataset**:

|Feature 1 (Height)|Feature 2 (Weight)|Class (Fit Clothes)|
|---|---|---|
|150|50|Yes|
|160|55|Yes|
|170|70|No|
|175|80|No|
#### **Step-by-Step Explanation**:

1. **Calculate Gini for the Entire Dataset**:
    - Total instances: 4.
    - Classes: "Yes" = 2, "No" = 2.
    $Gini = 1 - \left(\left(\frac{2}{4}\right)^2 + \left(\frac{2}{4}\right)^2\right) = 0.5$
2. **Find Possible Splits**:
    - For "Height": Possible splits are 155,165,172.5.
    - For "Weight": Possible splits are 52.5,62.5,75.
3. **Evaluate Splits**:
    - Example: Split "Height ≤ 165":
        - Left: [150,160][150, 160], Classes: Yes, Yes , Gini = 0.0.
        - Right: [170,175][170, 175], Classes: No,No , Gini = 0.0.
        - Weighted Gini: $Gini = \frac{2}{4} \cdot 0.0 + \frac{2}{4} \cdot 0.0 = 0.0$
4. **Choose the Best Split**:
    - "Height ≤ 165" results in the lowest Gini (0.0). Split the dataset.
5. **Repeat**:
    - For the subsets, repeat steps 1–4 until all nodes are pure or meet stopping criteria.

#### **Final Tree**:

```
       Height ≤ 165?
       /          \
    Yes           Height ≤ 172.5?
                 /          \
              No            No
```

---
