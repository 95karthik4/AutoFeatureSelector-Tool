# 🎯 AutoFeatureSelector

![Python](https://img.shields.io/badge/Python-3.8%2B-blue) ![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-orange) ![LightGBM](https://img.shields.io/badge/Library-LightGBM-green) ![Status](https://img.shields.io/badge/Status-Completed-success)

### 🚀 The Problem
In any Data Science project, datasets often contain hundreds of columns. Some are critical signals, while others are just noise. Manually selecting the best features is time-consuming and prone to bias.

### 💡 The Solution
**AutoFeatureSelector** is a Python-based automated tool that evaluates dataset features using **six different selection methods** simultaneously. It creates a voting system to identify the strongest features that are universally agreed upon by multiple algorithms.

---

### 🛠️ Methods Implemented
This tool leverages an "Ensemble" approach, running the following selectors in parallel:

1.  **Pearson Correlation:** Measures linear relationship between features and target.
2.  **Chi-Square:** Statistical test for categorical feature dependence.
3.  **Recursive Feature Elimination (RFE):** Recursively removes weakest features using Logistic Regression.
4.  **Lasso (L1) Regularization:** Penalizes non-important feature coefficients to zero.
5.  **Random Forest:** Tree-based feature importance.
6.  **LightGBM:** Gradient boosting-based feature importance.

---

### 📊 How It Works
The tool takes a dataset (e.g., FIFA 19 Player Skills) and a target variable (e.g., "High Potential Player").

1.  **Preprocessing:** Cleans data, one-hot encodes categorical variables, and removes nulls.
2.  **Selection:** Runs all 6 algorithms to select the top `N` features (e.g., Top 30).
3.  **Voting:** Counts how many algorithms selected each feature.
4.  **Ranking:** Returns a dataframe sorted by "Total Votes," giving you the most robust predictors at the top.

---

### 📈 Sample Output
*The table below shows the top features selected by the tool on the FIFA 19 dataset. Features with 6 votes were selected by ALL methods.*

| Feature | Pearson | Chi-2 | RFE | Logistic | Random Forest | LightGBM | **Total Votes** |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **FKAccuracy** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | **6** |
| **Finishing** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | **6** |
| **LongPassing** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | **6** |
| **Reactions** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | **6** |
| **Acceleration** | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | **5** |
| ... | ... | ... | ... | ... | ... | ... | ... |

---

### 👨‍💻 About the Author
**Karthik Kunnamkumarath**
*Aerospace Engineer | Project Management Professional (PMP) | AI Solutions Developer*

I specialize in building tools that make Data Science workflows more efficient and interpretable.
* 📍 Toronto, ON
* 💼 [LinkedIn Profile](https://linkedin.com/in/4karthik95)
* 📧 Aero13027@gmail.com

---

### 💻 Usage Example

```python
from Task7_AutoFeatureSelector_dn import autoFeatureSelector

# Run the selector
best_features, summary_df = autoFeatureSelector(
    dataset_path="fifa19.csv",
    methods=['pearson', 'chi-square', 'rfe', 'log-reg', 'rf', 'lgbm'],
    num_feats=30
)

print(best_features)

---

