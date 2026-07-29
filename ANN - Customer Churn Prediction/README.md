# Artificial Neural Network (ANN) - Customer Churn Prediction

A deep learning project that implements an Artificial Neural Network to predict whether a bank customer is likely to churn based on demographic, account, and behavioral attributes.

## Overview

This project demonstrates an end-to-end binary classification workflow using a fully connected Artificial Neural Network (ANN).

The notebook covers exploratory data analysis, preprocessing, neural network design, training with early stopping, model evaluation, decision-threshold optimization, and error analysis.

The objective is to predict the `Exited` variable:

- `0` — Customer remained with the bank
- `1` — Customer exited the bank

## Dataset

**Bank Customer Churn Dataset**

The dataset contains **10,000 customer records** with demographic, account, and behavioral attributes.

Target variable:

- `Exited`

Identifier fields such as `RowNumber`, `CustomerId`, and `Surname` are excluded from model training.

### Dataset Source

Churn Modelling Dataset — Kaggle

https://www.kaggle.com/datasets/aakash50897/churn-modellingcsv

## Notebook Structure

The notebook follows the workflow below:

1. **Import Required Libraries**
2. **Load Dataset**
3. **Explore Dataset**
4. **Prepare Features and Target**
5. **Target Distribution**
6. **Exploratory Data Analysis**
7. **Train, Validation, and Test Split**
8. **Feature Preprocessing**
9. **Build Artificial Neural Network**
10. **Train the Model**
11. **Training and Validation Curves**
12. **Evaluate Model on Test Set**
13. **Confusion Matrix**
14. **ROC Curve**
15. **Decision Threshold Analysis**
16. **Compare Default and Optimized Thresholds**
17. **Error Analysis**
18. **Key Findings**
19. **Conclusion**

## Repository Contents

```text
├── ANN_Customer_Churn_Prediction.ipynb
├── Churn_Modelling.csv
├── README.md
└── requirements.txt
```

## Model Architecture

The ANN consists of:

- Input layer
- Dense layer with 64 neurons and ReLU activation
- Dropout layer with a rate of 0.30
- Dense layer with 32 neurons and ReLU activation
- Dropout layer with a rate of 0.20
- Single sigmoid output neuron for binary classification

The network is trained using the Adam optimizer and binary cross-entropy loss. Early stopping monitors validation loss and restores the best-performing model weights.

## Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- TensorFlow
- Keras
- Jupyter Notebook

## Evaluation Metrics

The model is evaluated using:

- Accuracy
- Precision
- Recall
- F1 Score
- ROC-AUC
- Confusion Matrix

## Results

At the default **0.50 decision threshold**, the ANN achieved approximately:

- **Accuracy:** 86.8%
- **Precision:** 78.3%
- **Recall:** 48.5%
- **F1 Score:** 59.9%
- **ROC-AUC:** 86.9%

Validation-set threshold analysis selected **0.35** as a better threshold based on F1 score. On the test set, this produced approximately:

- **Accuracy:** 86.2%
- **Precision:** 68.0%
- **Recall:** 60.7%
- **F1 Score:** 64.1%
- **ROC-AUC:** 86.9%

The optimized threshold substantially improved churn recall and F1 score while producing only a small reduction in overall accuracy.

## Key Findings

The model demonstrated good discrimination between churners and non-churners, with a ROC-AUC of approximately **0.87**.

The default threshold favored precision but missed a substantial proportion of actual churners. Lowering the threshold to **0.35** improved recall from approximately **48.5% to 60.7%** and increased the F1 score from approximately **59.9% to 64.1%**.

This demonstrates why accuracy alone is insufficient for evaluating an imbalanced classification problem and why decision thresholds should be selected according to the objective of the application.

## Conclusion

The project demonstrates how an Artificial Neural Network can be applied to structured customer data for binary churn prediction.

The ANN achieved good overall classification performance, while validation-based threshold optimization produced a more useful balance between precision and recall. The project also demonstrates the importance of proper data splitting, preprocessing without leakage, regularization, early stopping, multiple evaluation metrics, and decision-threshold analysis.


