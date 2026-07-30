# Artificial Neural Network (ANN) Regression - Medical Cost Prediction

A deep learning regression project that predicts individual medical
insurance charges using an Artificial Neural Network (ANN) based on
demographic and lifestyle attributes.

## Overview

This project implements an end-to-end ANN regression workflow including
exploratory data analysis, preprocessing, model development, training
with early stopping, and evaluation on unseen test data.

## Dataset

**Medical Cost Personal Dataset**

The dataset contains **1,338 records** with features including age, sex,
BMI, number of children, smoking status, and region.

**Target Variable**

-   `charges`

### Dataset Source

Medical Cost Personal Dataset --- Kaggle

https://www.kaggle.com/datasets/mirichoi0218/insurance

## Notebook Structure

1.  **Import Required Libraries**
2.  **Load Dataset**
3.  **Explore Dataset**
4.  **Exploratory Data Analysis**
5.  **Prepare Features and Target**
6.  **Train, Validation, and Test Split**
7.  **Feature Preprocessing**
8.  **Build Artificial Neural Network**
9.  **Train the Model**
10. **Training and Validation Curves**
11. **Evaluate Model on Test Set**
12. **Actual vs Predicted**
13. **Residual Analysis**
14. **Key Findings**
15. **Conclusion**

## Repository Contents

``` text
├── ANN_Medical_Cost_Prediction.ipynb
├── insurance.csv
├── README.md
└── requirements.txt
```

## Model Architecture

-   Input layer
-   Dense layer (64 neurons, ReLU)
-   Dropout (0.20)
-   Dense layer (32 neurons, ReLU)
-   Dropout (0.10)
-   Single linear output neuron

The model is trained using the Adam optimizer with Mean Squared Error
(MSE) loss and Early Stopping based on validation loss.

## Technologies Used

-   Python
-   NumPy
-   Pandas
-   Matplotlib
-   Seaborn
-   Scikit-learn
-   TensorFlow
-   Keras
-   Jupyter Notebook

## Evaluation Metrics

-   Mean Absolute Error (MAE)
-   Root Mean Squared Error (RMSE)
-   R² Score

## Results

The trained ANN achieved approximately:

-   **MAE:** 3245.70
-   **RMSE:** 5025.59
-   **R² Score:** 0.8373

The model explains approximately **84%** of the variance in medical
insurance charges and generalizes well to unseen data.

## Key Findings

-   The ANN explained approximately **83.7%** of the variance in medical
    insurance charges on the test set.
-   Training and validation loss converged smoothly, indicating stable
    learning.
-   The model produced reliable predictions while larger errors were
    mainly observed for higher-cost insurance cases.

## Conclusion

This project demonstrates the effectiveness of an Artificial Neural
Network for structured regression problems. Through appropriate
preprocessing, regularization, early stopping, and evaluation on unseen
data, the model achieved strong predictive performance and provides a
reproducible deep learning workflow suitable for portfolio presentation.
