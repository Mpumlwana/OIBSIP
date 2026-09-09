# 🌸 Iris Flower Classification Report

*Data Science Track, Task 1 | Oasis Infobyte Summer Internship Program (SIP)*

---

## 📁 Dataset Overview

- 🌼 **Iris dataset**: 150 samples, 4 numeric features (sepal length, sepal width, petal length, petal width, all in cm), 3 balanced target classes (50 samples each: Setosa, Versicolor, Virginica)
- 📏 Source: loaded directly from `sklearn.datasets.load_iris()` — a clean, pre-verified dataset with zero missing values and correct data types

---

## 🔍 Exploratory Data Analysis

| Check | Result |
|---|---|
| Shape | 150 rows × 5 columns |
| Missing values | 0 across all columns |
| Data types | All measurements as `float64`, species as text |

**Descriptive statistics highlights:**
- Petal length showed the widest spread (std = 1.77, range 1.0–6.9 cm)
- Sepal width showed the narrowest spread (std = 0.44, range 2.0–4.4 cm)

---

## 📊 Feature Discriminative Power

| Feature | Species Separation |
|---|---|
| Petal length | Excellent — near-zero overlap between species |
| Petal width | Excellent — near-zero overlap between species |
| Sepal length | Moderate — some overlap, mainly between versicolor/virginica |
| Sepal width | Weak — heavy overlap across all three species |

**Conclusion:** petal measurements are the strongest predictors of species; sepal width contributes the least.

---

## 🧠 Model Training & Results

- **Train/test split:** 80/20 (120 training samples, 30 test samples), `random_state=42`
- **Models trained:** Logistic Regression, K-Nearest Neighbors (k=5)

| Model | Accuracy | Precision (avg) | Recall (avg) | F1-score (avg) |
|---|---|---|---|---|
| Logistic Regression | 100% | 1.00 | 1.00 | 1.00 |
| K-Nearest Neighbors | 100% | 1.00 | 1.00 | 1.00 |

**Confusion Matrix (both models, identical):**

[[10 0 0]
[ 0 9 0]
[ 0 0 11]]
Zero misclassifications across all three species.

---

## 🏆 Final Model Selection

**Chosen model: Logistic Regression**

Since both models achieved identical, perfect performance, the decision was based on non-accuracy factors:
- **Simplicity** — fewer moving parts, easier to explain
- **Speed** — predicts instantly; KNN must compare against all training points every time
- **Scalability** — remains fast as dataset size grows, unlike KNN
- **Interpretability** — model coefficients reveal how much each feature influences the prediction

---

## 🔑 Key Findings

1. 🎯 **Perfect classification achievable** — the Iris dataset's natural class separation allows even simple models to reach 100% test accuracy.
2. 📈 **Petal measurements dominate** — petal length and width alone would likely be sufficient for near-perfect classification, even without sepal data.
3. ⚖️ **Tie-breaking requires judgment** — when models perform equally, criteria like interpretability and efficiency guide the final choice.

---

## 🚀 Recommendations for Future Work

1. Test additional models (e.g., Decision Tree, Random Forest) to see if results hold across other algorithm types.
2. Apply cross-validation instead of a single train/test split for a more robust performance estimate.
3. Experiment with using only petal length and petal width as features, to test if sepal data is truly unnecessary.

---

## 🛠️ Tools Used
`Python` · `pandas` · `numpy` · `matplotlib` · `seaborn` · `scikit-learn` · `Jupyter Notebook`

---
*📌 This report was generated as part of Task 1 (Iris Flower Classification), Data Science Track, Oasis Infobyte Summer Internship Program.*