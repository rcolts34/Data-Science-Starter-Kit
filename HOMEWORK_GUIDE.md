# 🧭 Step-by-Step Guide: Completing the Data Science Homework

 This will walk you through the steps to complete your data science homework based on Chapters 3 & 4 of *Introduction to Data Science*.



---

## 🔧 Step 1: Setup Environment

1. Install [Anaconda](https://www.anaconda.com/products/distribution) or ensure Python 3.9+ is installed - lab machines should be good, and you can skip this step
2. Create and activate a new environment (optional but recommended):
```bash
conda create -n ds_homework python=3.9 pandas matplotlib seaborn jupyter scipy
conda activate ds_homework
```
3. Launch Jupyter Notebook:
```bash
jupyter notebook
```

---

## 📂 Step 2: Open the starting notebook

- Navigate to `notebooks/starter.ipynb`

---

## 📊 Step 3: Descriptive Statistics

- Compute:
  - Mean
  - Median
  - Mode
  - Standard deviation
  - IQR (Interquartile Range)

Use pandas functions like `.mean()`, `.median()`, `.mode()`, `.std()`, `.quantile()`.

```python
import pandas as pd
import numpy as np
df = pd.read_csv('../data/ACCIDENTS_GU_BCN_2013.csv')
victims = df['N�mero de v�ctimes']
print('Mean:', victims.mean())
##  etc..
```

---

## 📉 Step 4: Visualizations

Create the following plots using `matplotlib` and `seaborn`:
- Histogram
- KDE (Kernel Density Estimate)
- Boxplot
- Correlation heatmap (use `.corr()` on numeric columns)


```python
import matplotlib.pyplot as plt
import seaborn as sns
sns.histplot(victims, bins=15, kde=False)
plt.title('Histogram')
plt.show()

sns.kdeplot(victims, fill=True)
plt.title('KDE Plot')
plt.show()

sns.boxplot(x=victims)
plt.title('Boxplot')
plt.show()

plt.figure(figsize=(10,6))
sns.heatmap(df.corr(numeric_only=True), annot=True, cmap='coolwarm')
##  etc..
```

---

## 📈 Step 5: Bootstrap Confidence Interval

- Use random sampling with replacement to generate 1000 bootstrap means.
- Calculate the 95% confidence interval using `np.percentile`.

Example:
```python
boot_means = [victims.sample(frac=1, replace=True).mean() for _ in range(1000)]
ci_lower = np.percentile(boot_means, 2.5)
ci_upper = np.percentile(boot_means, 97.5)
print(f'95% CI for mean victims: ({ci_lower:.2f}, {ci_upper:.2f})')
```

---

## 🧪 Step 6: Hypothesis Testing

- Use a one-sample t-test to test if the mean number of victims differs from 1:
```python
from scipy.stats import ttest_1samp
t_stat, p_val = ttest_1samp(victims.dropna(), popmean=1)
print(f't-statistic: {t_stat:.2f}, p-value: {p_val:.4f}')
if p_val < 0.05:
    print('Reject null hypothesis: mean is significantly different from 1')
else:
    print('Fail to reject null hypothesis')
```
- Interpret the p-value to determine significance.

---

## ✅ Step 7: Finalize and Submit

- Write your interpretations in markdown cells
- Save your notebook as `notebooks/solution.ipynb`
- Push all changes to your own GitHub fork
- Submit the link as instructed
 