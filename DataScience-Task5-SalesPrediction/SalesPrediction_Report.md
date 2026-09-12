# 📈 Sales Prediction Report

*Data Science Track, Task 5 | Oasis Infobyte Summer Internship Program (SIP)*

---

## 📁 Dataset Overview

- 📊 **Advertising dataset**: 200 campaigns, 3 numeric features (TV, Radio, Newspaper ad budgets in $), 1 numeric target (Sales)
- 📏 Source: Kaggle ("Advertising Sales Dataset")
- Data quality: zero missing values, zero duplicate rows, correct numeric data types across all columns

---

## 🔍 Exploratory Findings

| Channel | Average Spend | Correlation with Sales |
|---|---|---|
| TV | $147.04 | 0.78 (strong) |
| Radio | $23.26 | 0.58 (moderate) |
| Newspaper | $30.55 | 0.23 (weak) |

Scatter plots confirmed these relationships visually: TV showed a tight, clear upward (though slightly curved) trend; Radio showed a moderate trend; Newspaper showed a scattered, largely random pattern.

---

## 🧠 Model Training & Results

- **Train/test split:** 80/20 (160 training samples, 40 test samples), `random_state=42`
- **Models trained:** Linear Regression, Random Forest Regressor

| Model | MAE | RMSE | R² Score |
|---|---|---|---|
| Linear Regression | 1.46 | 1.78 | 0.899 |
| Random Forest Regressor | **0.62** | **0.77** | **0.981** |

**Residual analysis:** Random Forest's residuals were randomly scattered around zero across the full range of predictions, indicating no systematic bias — errors reflect genuine data noise rather than a model weakness.

---

## 🏆 Final Model Selection

**Chosen model: Random Forest Regressor**

Justification:
- Roughly 2.3x lower MAE and RMSE compared to Linear Regression
- R² of 0.981 vs. 0.899 — explains substantially more of the variation in sales
- Better suited to the slightly non-linear, diminishing-returns pattern observed in TV ad spend, which a straight-line model cannot capture

---

## 💼 Business Interpretation

| Method | Top Channel | Insight |
|---|---|---|
| Correlation heatmap | TV (0.78) | Strongest linear relationship with sales |
| Random Forest feature importance | TV (62.5%) | Most influential in the model's actual decisions |
| Linear Regression coefficients | Radio (0.189) | Most efficient sales gain per $1 spent |

**Reconciling the disagreement:** Radio is the most efficient channel per dollar spent, but companies allocate far larger absolute budgets to TV ($147 avg vs. $23 avg for Radio). As a result, TV drives the largest real-world total impact on sales despite being less efficient per dollar. Newspaper is consistently the weakest channel across every method tested and is the safest channel to cut if budgets are reduced.

---

## 🔑 Key Findings

1. 🎯 **Random Forest significantly outperforms Linear Regression** on this dataset, likely due to non-linear patterns in advertising spend.
2. 📺 **TV drives the most total sales impact**, confirmed by three independent methods (correlation, feature importance, visual scatter pattern).
3. 📻 **Radio is the most cost-efficient channel**, an insight only visible through regression coefficients, not raw correlation alone.
4. 📰 **Newspaper advertising has minimal measurable effect** on sales in this dataset.

---

## 🚀 Recommendations for Future Work

1. Test Gradient Boosting or XGBoost regressors to see if performance improves further.
2. Investigate potential interaction effects (e.g., does combining TV + Radio spend outperform either channel alone?).
3. Collect additional business context (e.g., product category, region) to explain remaining unexplained variance.

---

## 🛠️ Tools Used
`Python` · `pandas` · `numpy` · `matplotlib` · `seaborn` · `scikit-learn` · `Jupyter Notebook`

---
*📌 This report was generated as part of Task 5 (Sales Prediction), Data Science Track, Oasis Infobyte Summer Internship Program.*