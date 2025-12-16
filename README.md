# Exploratory-Data-Analysis-of-Breast-Cancer-Wisconsin

My attempt on performing EDA and a little bit of modeling with Logistic Regression. \
you can view the .ipynb notebook of the project [here](https://github.com/jimmyreturnz/Exploratory-Data-Analysis-of-Breast-Cancer-Wisconsin/blob/main/breastcancer_wisconsin.ipynb)

## Overview

This project is about applying the process of Exploratory Data Analysis (EDA) and basic Model Training for classifying breast cancer diagnoses (Malignant vs. Benign) 
using the **Breast Cancer Wisconsin** dataset, with the goal of **maximizing recall** since it is a medical data. 

## 1. Loading Data + Basic Checkings 
   **Data Source**: [Breast Cancer Wisconsin](https://www.kaggle.com/datasets/uciml/breast-cancer-wisconsin-data) \
   **Data Integrity**: No null values \
   **Target Encoding**: The categorical diagnosis column was converted to a binary format: \
   &emsp;**Malignant** (M): 1 \
   &emsp;**Benign** (B): 0 \
   **Class Imbalance**: The data showed a slight imbalance: 357 Benign (0) records and 212 Malignant (1) records. \
   **Feature Count**: The raw data contained 569 rows and 32 columns (including id and diagnosis). \
   **Correlation Analysis**: There might be high multicollinearity as can be observed from heatmap. 

## 2. Feature Selection and Dimensionality Reduction
  This project tried to reduce the number of features while retaining predictive power for 3 times in total. 
  1. Initial Filtering (Random Forest Importance) \
  &emsp;Used randomforest to rank feature importance. Features with importance more than 0.01 were kept, \
  &emsp;reducing the feature count from 30 to 23 columns. 
  2. Variance Thresholding \
  &emsp;Applied Viariance Threshold (0.1). Reduced from 23 columns to 16 columns. 
  3. Remove High Multicollinearity Columns. \
  &emsp;Features with Pearson correlation coefficient greater than 0.9 were dropped. \
  &emsp;Reduced the final feature count to just 4 key predictors: radius_mean, texture_mean, perimeter_se, smoothness_worst

## 3. Model Training + Hyperparameter Tuning
  Logistic Regression model were fitted to 3 datasets with different columns after dimensionality reduction. \
  The project then proceeds to perform GridSearchCV to optimize C (regularization strength) \
  for logistic regression on model V3 (data_very_reduced). 
  
## 4. Final V3 Model Performance (with Best Params)
  &emsp;Accuracy: 0.9240 \
  &emsp;Precision (Malignant): 0.92 \
  &emsp;Recall (Malignant): 0.87 
