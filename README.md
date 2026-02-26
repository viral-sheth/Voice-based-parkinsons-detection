# Voice-Based Detection & Cross-Domain Modeling of Parkinson’s Disease

## Overview

This project develops an end-to-end machine learning pipeline for early detection and longitudinal progression modeling of Parkinson’s Disease (PD) using structured acoustic biomarkers derived from voice recordings.

Beyond achieving strong within-dataset performance, this work focuses on **cross-dataset generalization**, evaluating how models trained on controlled clinical recordings perform on real-world home-collected telemonitoring data. The study highlights the impact of domain shift, dataset bias, and validation methodology in healthcare AI systems.

---

## Problem Motivation

Parkinson’s Disease is often diagnosed after noticeable motor symptoms appear, although subtle vocal impairments emerge much earlier. Voice signals provide a:

- Non-invasive  
- Low-cost  
- Scalable biomarker  

This project investigates whether acoustic features can reliably:

1. Detect Parkinson’s Disease (classification)  
2. Predict disease severity via UPDRS scores (regression)  
3. Generalize across recording environments (clinical → home)

---

## Datasets

### 1. UCI Parkinson’s Dataset

- 195 recordings  
- 31 subjects (23 PD, 8 Healthy)  
- 22 acoustic features (jitter, shimmer, HNR, RPDE, DFA, PPE, etc.)  
- Used for binary classification  

### 2. Parkinson’s Telemonitoring Dataset

- ~5,875 longitudinal recordings  
- 42 PD patients  
- Motor UPDRS & Total UPDRS scores  
- Used for severity regression and progression modeling  

All evaluation used **subject-wise splitting** to prevent data leakage.

---

## Methodology

### Preprocessing

- StandardScaler normalization  
- PCA for dimensionality reduction  
- Variance Inflation Factor (VIF) analysis for multicollinearity  
- Feature alignment across datasets  
- Patient-level train/test separation  

### Classification Models

- Logistic Regression  
- Support Vector Machine (RBF)  
- Random Forest  
- Gradient Boosting  
- GroupKFold cross-validation  

### Regression Models

- Linear Regression  
- Ridge (L2 Regularization)  
- Lasso (L1 Regularization)  
- Random Forest Regressor  
- Gradient Boosting Regressor  

### Cross-Dataset Evaluation

- Clinical → Telemonitoring transfer  
- Reverse transfer (severity → diagnosis)  
- Domain shift analysis via t-SNE  
- Feature attribution using SHAP  

---

## Results

### Parkinson’s Detection (Clinical Dataset)

- Accuracy: 93%  
- F1-score: 0.96  
- ROC-AUC: 0.98  

### Cross-Dataset Generalization

- Recall (Clinical → Home): 88%  
- Demonstrates robustness across recording environments  

### Severity Regression (Telemonitoring Dataset)

- Motor UPDRS: Test MAE ≈ 5.9  
- Total UPDRS: Test MAE ≈ 7.9  
- Regularized models outperformed tree ensembles under subject-wise validation  

### Domain Shift Insights

- t-SNE revealed clear separation between clinical and home recordings  
- SHAP confirmed jitter, PPE, and DFA as primary predictive biomarkers  

---

## Key Contributions

- Designed a leakage-aware ML pipeline using patient-level validation  
- Quantified domain shift between clinical and real-world environments  
- Demonstrated asymmetric transfer learning behavior  
- Integrated Explainable AI (SHAP) to validate clinical feature importance  
- Highlighted challenges of severity prediction vs binary detection  



