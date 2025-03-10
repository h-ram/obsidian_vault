The **ID3 (Iterative Dichotomiser 3)** algorithm builds a decision tree by using **entropy** and **information gain** to choose the best attribute for splitting the dataset at each step. Here’s how it works:

---
### **Steps of the ID3 Algorithm**

1. **Calculate Entropy of the Dataset**:
    - Entropy measures the impurity or randomness in the dataset.
    - Formula: $\text{Entropy} = - \sum_{i=1}^{n} p_i \log_2(p_i)$ where $p_i$ is the proportion of samples in class $i$.
2. **Calculate Information Gain (IG) for Each Attribute**:
    - Information gain measures how much an attribute reduces the entropy.
    - Formula: $\text{IG}(\text{Attribute}) = \text{Entropy(Parent)} - \sum \left( \frac{|Subset|}{|Parent|} \cdot \text{Entropy(Subset)} \right)$
    - Choose the attribute with the highest information gain as the root or split.
3. **Split the Dataset Based on the Best Attribute**:
    - Divide the dataset into subsets based on the chosen attribute values.
4. **Repeat Recursively**:
    - For each subset, repeat steps 1-3 until:
        - All samples in a subset belong to the same class, or
        - No attributes are left to split, or
        - The subset is empty.
5. **Stop and Assign Class Labels**:
    - Assign the majority class of the subset as the leaf node.

---
# **Example**
#### Dataset:

|Outlook|Temperature|Humidity|Windy|Play Tennis|
|---|---|---|---|---|
|Sunny|Hot|High|False|No|
|Sunny|Hot|High|True|No|
|Overcast|Hot|High|False|Yes|
|Rainy|Mild|High|False|Yes|
|Rainy|Cool|Normal|False|Yes|
|Rainy|Cool|Normal|True|No|
|Overcast|Cool|Normal|True|Yes|
|Sunny|Mild|High|False|No|
|Sunny|Cool|Normal|False|Yes|
|Rainy|Mild|Normal|False|Yes|
|Sunny|Mild|Normal|True|Yes|
|Overcast|Mild|High|True|Yes|
|Overcast|Hot|Normal|False|Yes|
|Rainy|Mild|High|True|No|

#### Step-by-Step:
1. **Calculate the Entropy of the Dataset**:
    - Classes are $PlayTennis=Yes$  and $No$.
    - Count Yes=9, No=5 :
    - $\text{Entropy} = - \left( \frac{9}{14} \log_2 \frac{9}{14} + \frac{5}{14} \log_2 \frac{5}{14} \right) \approx 0.940$
1. **Calculate Information Gain for Each Attribute**:
    - For example, split by "Outlook":
        - Subsets:
            - $Sunny (55): Yes=2,No=3$
            - $Overcast (44): Yes=4,No=0$
            - $Rainy (55): Yes=3,No=2$
        - Calculate Entropies and Weighted Average: $\text{Entropy(Sunny)} = -\left(\frac{2}{5} \log_2 \frac{2}{5} + \frac{3}{5} \log_2 \frac{3}{5}\right) \approx 0.971$ 
        - Similarly, calculate for Overcast and Rainy. Combine for total IG: $\text{IG(Outlook)} = 0.940 - \left(\frac{5}{14} \cdot 0.971 + \frac{4}{14} \cdot 0.0 + \frac{5}{14} \cdot 0.971\right)$
1. **Choose the Attribute with the Highest IG**:
    - Suppose "Outlook" has the highest IG. Make it the root.
4. **Repeat for Each Subset**:
    - Split further (e.g., "Sunny" subset) until subsets are pure or cannot be split further.

---

### **Final Tree**:

The decision tree will look something like this:

```
           Outlook
         /    |     \
      Sunny Overcast Rainy
       /       |       \
  (Temp)    Play=Yes   (Windy)
```

Each branch leads to a decision, eventually classifying whether to "Play Tennis" or not.