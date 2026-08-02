# Convolutional Neural Network (CNN) Classification - Fashion MNIST

A deep learning image classification project that applies a
Convolutional Neural Network (CNN) to classify images from the Fashion
MNIST dataset.

## Overview

This project implements a CNN for multi-class image classification using
the Fashion MNIST dataset. The workflow includes data preprocessing,
model development, training, evaluation, and performance visualization
to demonstrate a complete deep learning pipeline.

## Dataset

**Fashion MNIST Dataset**

-   60,000 training images
-   10,000 test images
-   28 × 28 grayscale images
-   10 clothing categories

### Dataset Source

Fashion MNIST --- TensorFlow / Keras

https://www.tensorflow.org/api_docs/python/tf/keras/datasets/fashion_mnist

The dataset is downloaded automatically when the notebook is executed
and is not stored in this repository.

## Notebook Structure

1.  Import Required Libraries
2.  Load Dataset
3.  Explore Dataset
4.  Preprocess Images
5.  Build CNN Model
6.  Train the Model
7.  Training Curves
8.  Evaluate Model
9.  Classification Report
10. Confusion Matrix
11. Sample Predictions
12. Key Findings
13. Conclusion

## Repository Contents

``` text
├── CNN_Fashion_MNIST_Classification.ipynb
├── README.md
└── requirements.txt
```

## Model Architecture / Methodology

-   Two Convolutional layers with ReLU activation
-   Max Pooling layers
-   Dense hidden layer
-   Dropout regularization
-   Softmax output layer
-   Adam optimizer with Early Stopping

## Technologies Used

-   Python
-   NumPy
-   Matplotlib
-   Seaborn
-   Scikit-learn
-   TensorFlow
-   Jupyter Notebook

## Evaluation Metrics

-   Accuracy
-   Precision
-   Recall
-   F1-Score
-   Classification Report
-   Confusion Matrix

## Results

-   **Test Accuracy:** **90.45%**

The model achieved consistent performance on unseen test data with
stable learning behaviour throughout training.

## Key Findings

-   The CNN achieved 90.45% test accuracy while maintaining a small gap
    between training and validation performance.
-   Classification performance was strongest for visually distinct
    categories and lower for classes with similar visual
    characteristics.
-   Evaluation results indicate that the model generalized well without
    evidence of significant overfitting.

## Conclusion

The implemented CNN successfully learned discriminative image features
from the Fashion MNIST dataset and produced reliable classification
performance across the ten clothing categories. The combination of
preprocessing, regularization, early stopping, and comprehensive
evaluation resulted in a well-balanced image classification model.
