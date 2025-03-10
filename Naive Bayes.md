### **Naive Bayes Classification**
Naive Bayes is a probabilistic classification algorithm based on **Bayes' Theorem**, which calculates the posterior probability of a class given some observed features. It's called **"naive"** because it assumes that the features are independent of each other, which is a simplifying assumption that often works well in practice, even though it may not be true in reality.

---
### **Bayes' Theorem**
Bayes' Theorem is the foundation of the Naive Bayes classifier. It describes the relationship between the conditional probability of the class C given the feature set X and the reverse conditional probabilities. The theorem is expressed as:
$P(C|X) = \frac{P(X|C) \cdot P(C)}{P(X)}$
Where:
- $P(C|X)$ is the **posterior probability** of the class C given the observed features X.
- $P(X|C)$ is the **likelihood**, i.e., the probability of observing features X given that the class is C.
- $P(C)$ is the **prior probability** of the class C.
- $P(X)$ is the **evidence**, the probability of observing the feature set X across all classes.

Since $P(X)$ is the same for all classes, it is often ignored when comparing the relative probabilities of different classes. The classifier focuses on maximizing $P(C|X)$, which is proportional to $P(X|C) \cdot P(C)$.

---
### **Steps in Naive Bayes Classification**
1. **Calculate the Prior Probability for Each Class:**
	$P(C_k) = \frac{\text{Number of samples in class } C_k}{\text{Total number of samples}}$
1. **Calculate the Likelihood for Each Feature Given the Class:**
    - For continuous features, you assume a specific distribution (often Gaussian) to calculate $P(X_i|C_k)$.
    - For categorical features, you use the frequency of feature values within each class.
2. **Apply Bayes' Theorem:** Multiply the prior probability $P(C_k)$ by the likelihoods $P(X_i|C_k)$ for all features, then compute the posterior probabilities for each class.
4. **Select the Class with the Highest Posterior Probability:** Choose the class $C_k$ that maximizes $P(C_k|X)$, which is the one with the highest value of $P(X|C_k) \cdot P(C_k)$.
---
### **Example of Naive Bayes Classification**
Let’s go through a simple example to demonstrate how Naive Bayes classification works.

|Outlook|Temperature|Humidity|Wind|PlayTennis|
|---|---|---|---|---|
|Sunny|Hot|High|Weak|No|
|Sunny|Hot|High|Strong|No|
|Overcast|Hot|High|Weak|Yes|
|Rain|Mild|High|Weak|Yes|
|Rain|Cool|Normal|Weak|Yes|
|Rain|Cool|Normal|Strong|No|
|Overcast|Cool|Normal|Strong|Yes|
|Sunny|Mild|High|Weak|No|
|Sunny|Cool|Normal|Weak|Yes|
|Rain|Mild|Normal|Weak|Yes|
|Sunny|Mild|Normal|Strong|Yes|
|Overcast|Mild|High|Strong|Yes|
|Overcast|Hot|Normal|Weak|Yes|
|Rain|Mild|High|Strong|No|
In this dataset:
- **Features:** Outlook, Temperature, Humidity, Wind
- **Target Class:** $PlayTennis (Yes/No)$
We will classify a new data point: $\text{Outlook = Sunny, Temperature = Cool, Humidity = High, Wind = Weak}.$
---
### **Step 1: Calculate the Prior Probability for Each Class**
We first calculate the prior probability $P(C_k)$ for each class (Yes and No). There are 14 instances, with 9 instances where "PlayTennis = Yes" and 5 instances where "PlayTennis = No".
$P(\text{Yes}) = \frac{9}{14} = 0.643$ 
$P(\text{No}) = \frac{5}{14} = 0.357$
---
### **Step 2: Calculate the Likelihood for Each Feature Given the Class**
We need to calculate $P(\text{Feature}|C_k)$, which is the probability of each feature value given the class. We do this for each feature (Outlook, Temperature, Humidity, Wind) and each class (Yes and No).
#### For $P(\text{Outlook} = \text{Sunny} | \text{Yes})$:
- There are 3 instances where $\text{Outlook} = \text{Sunny}$ and $\text{PlayTennis} = \text{Yes}$ out of 9 instances where PlayTennis is Yes.
- So, $P(\text{Outlook} = \text{Sunny} | \text{Yes}) = \frac{3}{9} = 0.333$
#### For $P(\text{Outlook} = \text{Sunny} | \text{No})$:
- There are 2 instances where $\text{Outlook} = \text{Sunny}$ and $\text{PlayTennis} = \text{No}$ out of 5 instances where PlayTennis is No.
- So, $P(\text{Outlook} = \text{Sunny} | \text{No}) = \frac{2}{5} = 0.4$
#### Similarly, calculate the probabilities for other features (Temperature, Humidity, Wind):
- $P(\text{Temperature} = \text{Cool} | \text{Yes}) = \frac{2}{9} = 0.222$
- $P(\text{Temperature} = \text{Cool} | \text{No}) = \frac{1}{5} = 0.2$
- $P(\text{Humidity} = \text{High} | \text{Yes}) = \frac{3}{9} = 0.333$
- $P(\text{Humidity} = \text{High} | \text{No}) = \frac{4}{5} = 0.8$
- $P(\text{Wind} = \text{Weak} | \text{Yes}) = \frac{4}{9} = 0.444$
- $P(\text{Wind} = \text{Weak} | \text{No}) = \frac{2}{5} = 0.4$

---
### **Step 3: Apply Bayes' Theorem**
Now, we calculate the posterior probability for each class:
$$P(\text{Yes} | X) \propto P(\text{Outlook} = \text{Sunny} | \text{Yes}) \cdot P(\text{Temperature} = \text{Cool} | \text{Yes}) \cdot P(\text{Humidity} = \text{High} | \text{Yes}) \cdot P(\text{Wind} = \text{Weak} | \text{Yes}) \cdot P(\text{Yes})$$
Substituting the values:
$P(\text{Yes} | X) \propto 0.333 \cdot 0.222 \cdot 0.333 \cdot 0.444 \cdot 0.643 = 0.018$
Similarly, for $P(\text{No} | X)$:
$$P(\text{No} | X) \propto P(\text{Outlook} = \text{Sunny} | \text{No}) \cdot P(\text{Temperature} = \text{Cool} | \text{No}) \cdot P(\text{Humidity} = \text{High} | \text{No}) \cdot P(\text{Wind} = \text{Weak} | \text{No}) \cdot P(\text{No})$$
Substituting the values:
$P(\text{No} | X) \propto 0.4 \cdot 0.2 \cdot 0.8 \cdot 0.4 \cdot 0.357 = 0.0103$
---
### **Step 4: Make a Prediction**
Compare the posterior probabilities:
- $P(\text{Yes} | X) = 0.018$
- $P(\text{No} | X) = 0.0103$
Since $P(\text{Yes} | X) > P(\text{No} | X)$, the classifier predicts **Yes**, meaning the new data point will be classified as **PlayTennis = Yes**.

---