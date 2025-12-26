# Stroke Risk Prediction using Machine Learning

This project implements a machine learning pipeline to estimate the risk of stroke using demographic and clinical data.  
The focus is on building a reliable, interpretable, and well-evaluated model while addressing real-world healthcare data challenges such as missing values and class imbalance.

> ⚠️ This project is intended for **educational and analytical purposes only** and is **not a medical diagnostic tool**.

---

## 📌 Problem Statement

Stroke is a major health concern worldwide, and early risk identification can help in preventive healthcare planning.  
The goal of this project is to train a machine learning model that learns patterns from historical healthcare data and estimates the likelihood of stroke based on patient attributes.

---

## 📊 Dataset Overview

The dataset consists of anonymized patient records with the following characteristics:

- Numerical features: age, BMI, average glucose level
- Binary features: hypertension, heart disease
- Categorical features: gender, work type, smoking status, residence type
- Target variable: `stroke` (binary)

### Key Challenges
- Missing values in BMI
- Strong class imbalance (stroke cases are rare)
- Mixed data types requiring preprocessing

---

## 🧹 Data Preprocessing

The following preprocessing steps were applied:

- Dropped non-informative identifier column (`id`)
- Imputed missing BMI values using the median
- Applied one-hot encoding for categorical variables
- Used stratified train–test split to preserve class distribution

---

## ⚖️ Handling Class Imbalance

Since stroke cases form a small minority of the dataset:

- Stratified sampling was used during data splitting
- Class weighting was applied in Logistic Regression
- `scale_pos_weight` was used in XGBoost to emphasize minority class learning
- Accuracy alone was avoided as the primary metric

---

## 🤖 Modeling Approach

### Baseline Model
**Logistic Regression**
- Used as a baseline to validate data quality
- Provides interpretability and reference performance

### Final Model
**XGBoost Classifier**
- Captures non-linear relationships
- Handles structured tabular data effectively
- Performs well under class imbalance

---

## 🎯 Threshold Calibration

The default decision threshold (0.5) was found to be conservative for stroke detection.  
To improve medical relevance:

- Prediction probabilities were analyzed
- The threshold was tuned to **0.4**
- This improved recall for stroke cases while maintaining strong overall performance

---

## 📈 Evaluation Metrics

Model performance was evaluated using:

- Precision, Recall, and F1-score
- ROC-AUC for overall class separation

Evaluation was performed on unseen test data to ensure generalization.

---

## 🧠 Interpretation & Use Case

The model estimates **stroke risk probabilities** based on input features.  
It is intended as a **decision-support or early screening aid**, not as a replacement for clinical diagnosis.

This project demonstrates how machine learning can assist healthcare analysis when applied responsibly.

---

## 🛠️ Technologies Used

- Python
- Pandas, NumPy
- Scikit-learn
- XGBoost
- Jupyter Notebook

---

## ✅ Conclusion

This project showcases a complete and responsible machine learning workflow for healthcare data, including preprocessing, imbalance handling, baseline comparison, advanced modeling, and threshold tuning.

It emphasizes not only model performance but also explainability and domain-aware decision-making.

---

## 📄 License

This project is open for educational and non-commercial use.
