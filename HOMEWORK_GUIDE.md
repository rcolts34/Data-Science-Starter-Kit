# 🧭 Step-by-Step Guide: Completing the Data Science Homework

 This will walk you through the steps to complete your data science homework based on Chapters 3 & 4 of *Introduction to Data Science*.

---

## 🔧 Step 1: Setup Environment

1. Install [Anaconda](https://www.anaconda.com/products/distribution) or ensure Python 3.9+ is installed - lab machines should be good.
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

## 📂 Step 2: Load the Data

- Navigate to `notebooks/starter.ipynb`
- Load the dataset `../data/ACCIDENTS_GU_BCN_2013.csv` using pandas
```python
import pandas as pd
df = pd.read_csv('../data/ACCIDENTS_GU_BCN_2013.csv')
```

---

## 📊 Step 3: Descriptive Statistics

- Compute:
  - Mean
  - Median
  - Mode
  - Standard deviation
  - IQR (Interquartile Range)

Use pandas functions like `.mean()`, `.median()`, `.mode()`, `.std()`, `.quantile()`.

---

## 📉 Step 4: Visualizations

Create the following plots using `matplotlib` and `seaborn`:
- Histogram
- KDE (Kernel Density Estimate)
- Boxplot
- Correlation heatmap (use `.corr()` on numeric columns)

---

## 📈 Step 5: Bootstrap Confidence Interval

- Use random sampling with replacement to generate 1000 bootstrap means.
- Calculate the 95% confidence interval using `np.percentile`.

Example:
```python
import numpy as np
boot_means = [df['Número de víctimes'].sample(frac=1, replace=True).mean() for _ in range(1000)]
ci_lower = np.percentile(boot_means, 2.5)
ci_upper = np.percentile(boot_means, 97.5)
```

---

## 🧪 Step 6: Hypothesis Testing

- Use a one-sample t-test to test if the mean number of victims differs from 1:
```python
from scipy.stats import ttest_1samp
t_stat, p_val = ttest_1samp(df['Número de víctimes'].dropna(), popmean=1)
```
- Interpret the p-value to determine significance.

---

## ✅ Step 7: Finalize and Submit

- Write your interpretations in markdown cells
- Save your notebook
- Push all changes to your GitHub fork
- Submit the link as instructed

Good luck!
