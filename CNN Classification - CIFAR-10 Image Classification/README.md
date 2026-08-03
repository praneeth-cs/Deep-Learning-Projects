# Convolutional Neural Network (CNN) Classification - CIFAR-10 Image Classification

## Overview

This project implements a Convolutional Neural Network (CNN) for multi-class image classification using the CIFAR-10 dataset. The workflow includes preprocessing, model development, training, evaluation, and prediction analysis using TensorFlow/Keras.

## Dataset

**CIFAR-10 Dataset**

- 50,000 training images
- 10,000 test images
- 32 × 32 RGB images
- 10 object categories

## Dataset Source

TensorFlow / Keras CIFAR-10 Dataset

https://www.tensorflow.org/api_docs/python/tf/keras/datasets/cifar10

The dataset downloads automatically when the notebook is executed and is not stored in this repository.

## Notebook Structure

1. Import Required Libraries
2. Load Dataset
3. Explore Dataset
4. Preprocess Images
5. Build CNN Model
6. Train the Model
7. Training Curves
8. Evaluate Model
9. Classification Report
10. Confusion Matrix
11. Sample Predictions
12. Key Findings
13. Conclusion

## Repository Contents

```
├── CNN_CIFAR10_Image_Classification.ipynb
├── README.md
└── requirements.txt
```

## Model Architecture / Methodology

- Convolutional and Max Pooling layers
- Dropout regularization
- Dense classifier
- Adam optimizer
- Early Stopping

## Technologies Used

- Python
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- TensorFlow
- Jupyter Notebook

## Evaluation Metrics

- Accuracy
- Precision
- Recall
- F1-Score
- Classification Report
- Confusion Matrix

## Results

- **Test Accuracy:** **77.86%**

The model demonstrated stable learning with good generalization to unseen images.

## Key Findings

The CNN achieved 77.86% test accuracy and generalized well with only a modest gap between training and validation performance. Vehicles and visually distinctive objects were classified more reliably than visually similar animal classes such as cats and dogs.

## Conclusion

The project successfully demonstrates a complete CNN image classification workflow on CIFAR-10. The model provides a solid baseline for image classification and establishes a strong foundation before progressing to transfer learning.
