#  Stroke Risk Prediction & Model Optimization

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1JDGtAJse3NSY1bDYvO9pEFtvzfzQw3Lv?usp=sharing)

Analyzing clinical risk factors for stroke using ML algorithms to identify high-risk patient profiles

##  Project Overview
The goal of this project is to build a reliable classification model to identify patients at high risk of stroke. Given the clinical nature of the problem, the model was specifically optimized for **Recall** to minimize **False Negatives**, ensuring that potential stroke cases are not overlooked.

---

##  Dataset & Feature Engineering
After initial analysis, **Feature Selection** was performed to focus on the top 10 most impactful variables.

* **Key Features:** Age, Average Glucose Level, Hypertension, and Heart Disease (ranked by absolute coefficients).
* **Pre-processing:** Scaling was applied, and class imbalance was addressed using `class_weight='balanced'`.

---

##  Technical Workflow

### 1. Model Baseline (Logistic Regression)
* Implemented a balanced Logistic Regression to establish a baseline.
* **Optimization:** Used the **F1-Score vs. Threshold** analysis to find the "Best Threshold" that balances precision and recall.

### 2. Clinical Sensitivity Tuning (Target Recall: 82%)
To prioritize patient safety, I implemented a custom threshold selection:
* **Strategy:** Identified all thresholds where Recall>=0.82.
* **Result:** Successfully selected a specific threshold to ensure the model captures at least **82%** of actual stroke cases.

### 3. Advanced Modeling (Random Forest + GridSearchCV)
* Applied **Random Forest Classifier** with hyperparameter tuning.
* **Grid Search:** Optimized `n_estimators`, `max_depth`, and `min_samples_split` using 5-fold cross-validation and `roc_auc` scoring.
* **Final Model:** The `best_estimator_` was used for the final predictions and clinical evaluation.

---

## 📈 Visual Analysis
The project includes several key visualizations to justify model decisions:
* **F1-score vs Threshold:** To find the optimal balance point.
* **Feature Importance Bar Chart:** Ranking the 10 most significant clinical predictors.
* **Precision-Recall Curve:** Visualizing the trade-offs and marking the **Target Recall (0.82)** zone.

---

##  Key Results
* **Robust Evaluation:** Achieved high **ROC-AUC** scores through both Logistic Regression and Tuned Random Forest.
* **Clinical Readiness:** By adjusting the decision threshold, the model is prepared for screening scenarios where high sensitivity is required.

---

##  Tech Stack
* **Language:** Python
* **Libraries:** Scikit-Learn, Pandas, NumPy, Matplotlib, Seaborn
