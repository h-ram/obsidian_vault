
A **contingency table** (also called a **cross-tabulation** or **cross table**) is a tabular representation of categorical data that helps analyze the relationship between two or more categorical variables.

It provides the frequency (count) of observations falling into each combination of category levels. Contingency tables are widely used in **statistical analysis**, **hypothesis testing (Chi-square test)**, and **machine learning (feature analysis)**.

---
## **1. Structure of a Contingency Table**
A contingency table consists of:
- **Rows**: Represent one categorical variable.
- **Columns**: Represent another categorical variable.
- **Cells**: Contain frequency counts for each combination of row and column categories.
- **Margins**: Show totals for rows and columns.
#### **Example 1: Gender vs. Preference for a Product**

|Gender|Prefers Product A|Prefers Product B|Total|
|---|---|---|---|
|Male|50|30|80|
|Female|40|60|100|
|Total|90|90|180|
- This table shows how **gender** is related to **product preference**.
- The **marginal totals** show overall distributions.

---

## **2. Types of Contingency Tables**
### **2x2 Contingency Table (Binary Variables)**
A **2x2 table** is the simplest type, often used for hypothesis testing (Chi-square, Fisher's exact test).
#### **Example: Drug Effectiveness (Success/Failure)**

|Outcome|Drug A|Drug B|Total|
|---|---|---|---|
|Success|40|50|90|
|Failure|20|30|50|
|Total|60|80|140|
- **Used for:** A/B testing, medical trials, categorical comparisons.
### **RxC Contingency Table (More than Two Categories)**
For categorical variables with more than two levels.
#### **Example: Education Level vs. Voting Preference**

|Education Level|Party X|Party Y|Party Z|Total|
|---|---|---|---|---|
|High School|30|20|10|60|
|College|50|40|30|120|
|Graduate|20|30|50|100|
|Total|100|90|90|280|
- Shows how **education level** affects **political preference**.
---
## **3. Key Statistical Measures from Contingency Tables**
### **1. Row & Column Percentages**
Helps understand relative proportions.
#### **Example: Gender vs. Product Preference (Row % Calculation)**

|Gender|Prefers A (%)|Prefers B (%)|Total (%)|
|---|---|---|---|
|Male|50/80 = 62.5%|30/80 = 37.5%|100%|
|Female|40/100 = 40%|60/100 = 60%|100%|

- 62.5% of males prefer **Product A**, while only 40% of females do.
### **2. Chi-Square Test for Association**
- Tests whether two categorical variables are independent.
- **Null Hypothesis (H₀)**: No association exists.
- **Alternative Hypothesis (H₁)**: There is an association.
Formula:
χ2=∑(O−E)2E\chi^2 = \sum \frac{(O - E)^2}{E}
Where:
- O = Observed frequency
- E = Expected frequency under independence
### **3. Odds Ratio (For 2x2 Tables)**
Used in **medical studies** to measure association strength.
Formula:
OR=(A×D)(B×C)OR = \frac{(A \times D)}{(B \times C)}
For the **Drug A/B Effectiveness Table**:

||Success|Failure|
|---|---|---|
|**Drug A**|40|20|
|**Drug B**|50|30|

OR=(40×30)(50×20)=1.2OR = \frac{(40 \times 30)}{(50 \times 20)} = 1.2

Since OR > 1, Drug A has **higher success odds** than Drug B.

---

## **4. Creating Contingency Tables in Python**

Using **pandas** and **scipy.stats**:

```python
import pandas as pd
import scipy.stats as stats

# Sample Data
data = {'Gender': ['Male', 'Male', 'Female', 'Female', 'Male', 'Female'],
        'Preference': ['A', 'B', 'A', 'B', 'A', 'B']}

df = pd.DataFrame(data)

# Create Contingency Table
contingency_table = pd.crosstab(df['Gender'], df['Preference'])
print(contingency_table)

# Perform Chi-Square Test
chi2, p, dof, expected = stats.chi2_contingency(contingency_table)
print(f"Chi-Square Value: {chi2}, p-value: {p}")
```

---

## **5. Applications of Contingency Tables**

✅ **Market Research**: Understanding customer demographics & product preferences.  
✅ **Medical Studies**: Analyzing treatment effectiveness.  
✅ **Epidemiology**: Studying risk factors (e.g., smoking vs. lung disease).  
✅ **A/B Testing**: Comparing marketing strategies.

Would you like more examples or statistical tests related to contingency tables? 🚀