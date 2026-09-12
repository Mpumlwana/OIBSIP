# 📝 Reflection — Data Science Task 5: Sales Prediction

## 🎯 What I Did
For this task, I built a regression model to predict product sales based on advertising spend across three channels: TV, Radio, and Newspaper. Unlike Task 1 (a classification problem), this was my first regression task — predicting an actual number instead of a category.

I completed the full workflow:
- 📥 **Loading:** downloaded the Advertising dataset from Kaggle, dropped a redundant index column, and renamed columns for cleaner code.
- 🔍 **EDA:** confirmed 200 clean rows, correct data types, zero missing values, and zero duplicates.
- 📊 **Visualization:** scatter plots showed TV had the tightest, clearest relationship with sales; Newspaper showed almost no clear pattern. A correlation heatmap confirmed this numerically (TV: 0.78, Radio: 0.58, Newspaper: 0.23).
- 🤖 **Modeling:** trained Linear Regression and Random Forest Regressor, then compared them using MAE, RMSE, and R².
- 📏 **Evaluation:** Random Forest clearly outperformed Linear Regression on every metric (MAE 0.62 vs 1.46, R² 0.981 vs 0.899).
- 🔎 **Residual check:** confirmed Random Forest's errors were randomly scattered, not systematically biased.
- 🧠 **Interpretation:** discovered an important nuance — Linear Regression's coefficients suggested Radio was more "efficient per dollar," but Random Forest's feature importance and the correlation heatmap both confirmed TV had the biggest real-world impact, since companies actually spend far more on TV overall.
- 🏆 **Selection:** chose Random Forest Regressor as my final model.

## 💡 What I Learned
- ✅ Real datasets need actual downloading and cleaning — unlike Iris, this data came as a raw CSV file with a messy leftover index column and awkward column names.
- ✅ Renaming a file doesn't always work as expected on Windows — I hit a `FileNotFoundError` because the file secretly had a double extension (`.csv.csv`) after renaming, since Windows had hidden the original extension.
- ✅ A `KeyError` when re-running a cell often means the notebook's memory is out of sync with what you're trying to do — restarting the kernel and running cells in order from the top fixed it.
- ✅ `random_state` isn't about getting a "better" split — it's about making a random process reproducible, so results don't change every time the code re-runs.
- ✅ Regression uses different tools and metrics than classification: MAE, RMSE, and R² instead of accuracy and confusion matrices.
- ✅ A residual plot is essential — it reveals whether a model's mistakes are random noise (acceptable) or a hidden systematic bias (a real problem).
- ✅ Coefficients and feature importance can genuinely disagree, and understanding *why* (per-dollar efficiency vs. real-world total impact) was one of the most valuable lessons of this task — a model's numbers need real business context to interpret correctly, not just face-value reading.

## 🧗 Challenges I Faced
- Hit a `FileNotFoundError` due to a hidden double file extension after renaming the CSV on Windows — fixed by enabling file extension visibility and renaming correctly.
- Hit a `KeyError` from re-running cells out of order — fixed by restarting the kernel and running all cells fresh, top to bottom.
- Had to think carefully about why Linear Regression and Random Forest disagreed on which channel mattered most, rather than just picking whichever number looked biggest.

## 🛠️ Tools Used
`Python` · `pandas` · `numpy` · `matplotlib` · `seaborn` · `scikit-learn` · `Jupyter Notebook`

---
*Data Science Track, Task 5 of the Oasis Infobyte Summer Internship Program*