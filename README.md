# 💼 Supervised Learning: Billionaire Age Classification

An advanced **supervised machine learning** project in R predicting whether a billionaire is an **Adult** (≤65) or a **Senior** (>65).  
This study combines **data preprocessing, feature engineering, model training, interpretation, and comparison** across **seven classification algorithms**, building a complete predictive pipeline from raw data to interpretability.  
All results and insights are summarized in the **5-page analytical report (`REPORT.pdf`)**.

---

### 🚀 Project Summary

This project showcases a robust application of **supervised learning** and **model interpretability** in a real-world socioeconomic dataset.  
It demonstrates advanced use of **R** for feature selection, ensemble modeling, cross-validation, and post-hoc model interpretation using **Random Forest**, **XGBoost**, and **SHAP** analysis.

**Core Competencies:**
- Binary classification using multiple supervised models  
- Model evaluation (Accuracy, ROC, AUC) and hyperparameter optimization  
- Feature engineering and imputation with `mice`  
- Model interpretability with **feature importance**, **partial dependence**, and **SHAP** values  
- Ensemble learning: Bagging (Random Forest), Boosting (GBM, XGBoost, LightGBM)

---

### 🧠 Techniques & Technologies

* **Languages & Tools:** R, R Markdown  
* **Key Packages:** `randomForest`, `xgboost`, `gbm`, `glmnet`, `MASS`, `e1071`, `lightgbm`, `mice`, `VIM`, `caret`, `SHAPforxgboost`  
* **Methods Implemented:**
  - Naive Bayes, LDA, QDA  
  - Logistic Regression & Penalized Logistic Regression (Lasso/Ridge)  
  - Decision Trees & Random Forest  
  - Gradient Boosting (GBM, XGBoost, LightGBM)  
  - Ensemble learning and threshold optimization  
* **Evaluation Metrics:** Accuracy, ROC Curve, AUC, Confusion Matrix  

---

### 🔍 Analytical Workflow

#### 1️⃣ Data Preprocessing & Visualization
- **Cleaning & Feature Engineering:** Removed irrelevant attributes (e.g., `birthDay`, geolocation), standardized names, and created new derived variables.  
- **Outlier Detection:** Applied **3-sigma rule** and boxplots to validate distribution integrity.  
- **Missing Values:** Detected hidden NAs (`""`) and performed **multivariate imputation** with `mice` (Random Forest method).  
- **Visualization:** Explored target (`age_group`) vs predictors (`worth`, `rank`, `industry`, etc.) using `ggplot2` and `VIM`.

#### 2️⃣ Model Training & Prediction
Trained and compared a range of models with consistent preprocessing, partitioning (70/30 split), and cross-validation:

| Model Type | Algorithms | Highlights |
|-------------|-------------|-------------|
| **Generative** | Naive Bayes · LDA · QDA | Baseline models — low accuracy (≈0.55–0.60) due to nonlinear data. |
| **Linear** | Penalized Logistic Regression | Used `glmnet`; coefficients regularized via Lasso/Ridge. |
| **Tree-Based** | Decision Tree · Random Forest | Random Forest achieved **highest accuracy (~0.63)** and most stable predictions. |
| **Boosting** | GBM · XGBoost · LightGBM | Tuned via cross-validation; XGBoost close second with **AUC ≈ 0.63**. |
| **Ensemble** | Model Stacking | Combined outputs, limited incremental gain (ensemble ≈ Random Forest). |

#### 3️⃣ Model Interpretation
- **Feature Importance (Random Forest):** Highlighted `rank`, `worth`, and `primary_education` as key drivers of classification.  
- **Partial Dependence Plots:** Showed *rank* positively correlated with higher age probability; *worth* showed limited influence.  
- **SHAP Values:**  
  - Quantified feature impact on predictions (global and local).  
  - Top factors: `category`, `rank`, `population_country`, `education_primary`.  
  - SHAP dependence plots confirmed *nonlinear relations* between population and age group.  
- **LightGBM Local Interpretability:** Illustrated individual-level contributions with waterfall plots.

#### 4️⃣ Feature Selection & Comparative Insights
- Selected key predictive variables: `category`, `rank`, `worth`, `population_country`, `education_primary`, `rate`.  
- Found minimal influence from `gender`, `selfMade`, and `birthMonth`.  
- Random Forest and XGBoost models consistently outperformed simpler classifiers.

---

### 📊 Key Findings
- **Best Performing Model:** 🏆 Random Forest (Accuracy ≈ 0.63, AUC ≈ 0.63).  
- **Most Influential Features:** `rank`, `category`, `worth`, `education_primary`, `population_country`.  
- **Interpretability:** SHAP and RF plots confirmed model alignment with real-world logic (higher rank → older billionaire).  
- **Challenges:** Slightly limited predictive power due to small sample size and class imbalance, mitigated via subsampling (`ROSE`) and threshold tuning.

---

### 📁 Repository Contents

| File | Description |
|------|--------------|
| **SL.Rmd** | Full R Markdown analysis: preprocessing, model training, interpretation, and comparison. |
| **REPORT.pdf** | 5-page analytical summary with visuals and key findings. |
| **billionaires.csv** | [Billionaires Statistics Dataset (Kaggle)](https://www.kaggle.com/datasets/nelgiriyewithana/billionaires-statistics-dataset) — Public dataset used for analysis. |
| **/additional_data** | Supplementary datasets collected for extended exploration (not required to reproduce the main analysis). |

---

### 👥 Authors
**Jiawei Xu**  
**Iván López Anca**
