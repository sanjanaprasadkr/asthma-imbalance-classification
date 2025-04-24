# Asthma Emergency Room Visit Classification

This repository contains all code and documentation related to a classification project built on the **2021 BRFSS Asthma Call-back Survey (ACBS)** dataset. The primary goal of this project is to predict whether an individual has visited an emergency room or urgent care center due to asthma in the past 12 months.

## Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Objectives](#objectives)
- [Preprocessing Pipeline](#preprocessing-pipeline)
- [Feature Engineering and Selection](#feature-engineering-and-selection)
- [Modeling and Evaluation](#modeling-and-evaluation)
- [Tools Used](#tools-used)
- [Files in This Repository](#files-in-this-repository)

---

## Overview

This project addresses the problem of **class imbalance** in healthcare datasets and evaluates multiple modeling strategies to enhance predictive performance for a binary classification task. The focus is on classifying individuals based on whether they visited an emergency or urgent care facility due to asthma.

---

## Dataset

- Source: **2021 BRFSS Asthma Call-back Survey (ACBS)**
- Size: 7473 rows × 359 columns
- Target Variable: `Class` (1 = Visited ER/Urgent Care; 0 = Did Not)
- Type: Mixed (categorical + numeric)

---

## Objectives

1. Clean and preprocess the dataset for modeling.
2. Handle class imbalance through resampling techniques.
3. Perform feature selection using multiple approaches.
4. Evaluate multiple classification models (KNN, Decision Trees, AdaBoost, SVM, Random Forest, XGBoost).
5. Compare performance using weighted metrics and ROC-AUC.

---

## Preprocessing Pipeline

Detailed preprocessing was implemented in `project_code.R`, including:

- Removal of irrelevant or highly correlated columns.
- Conversion of low-cardinality variables to categorical type.
- Factor encoding and target variable binarization.
- Imputation:
  - Mode for categorical variables
  - Median for numeric variables
- Outlier handling using:
  - Capping (1st and 99th percentiles)
  - Log transformation for right-skewed distributions
- Z-score standardization for numeric variables.

Rare category detection for factor variables was also conducted.

---

## Feature Engineering and Selection

Three feature selection techniques were used on resampled and clustered datasets:

- **Boruta** (wrapper method using random forests)
- **Random Forest Importance**
- **Linear Discriminant Analysis (LDA)**

Each technique generated subsets used for further training and testing.

---

## Modeling and Evaluation

Classification models were trained and evaluated using repeated cross-validation and ROC-AUC as the primary metric. Models include:

- K-Nearest Neighbors (KNN)
- Decision Trees (RPart)
- AdaBoost
- Support Vector Machine (SVM with RBF kernel)
- Random Forest
- XGBoost

Each model was evaluated on:
- Sensitivity (Recall)
- Specificity
- Precision
- F1 Score
- Matthews Correlation Coefficient (MCC)
- Kappa Statistic
- ROC-AUC (weighted)

Weighted metrics were calculated considering class imbalance.

---

## Tools Used

- **R Programming Language**
- Libraries: `caret`, `Boruta`, `xgboost`, `ggplot2`, `dplyr`, `pROC`, `MASS`, `kknn`

---

## Files in This Repository

- `project_code.R`: Full pipeline including preprocessing, feature selection, modeling, and evaluation.
- `Rao_Yash_Prasad_Sanjana_IntermediateReport.pdf`: Project write-up detailing methodology, visualizations, and preprocessing rationale.

---

## Authors

- **Sanjana Prasad** 
- **Yash Rao**
(MET CS699 - Data Mining, Fall 2024)

