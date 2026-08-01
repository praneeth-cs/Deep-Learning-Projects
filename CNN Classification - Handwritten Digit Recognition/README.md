# Convolutional Neural Network (CNN) Classification - Handwritten Digit Recognition

A deep learning image classification project that uses a Convolutional Neural Network (CNN) to recognize handwritten digits from the MNIST dataset.

## Overview

This project demonstrates an end-to-end computer vision workflow using a CNN including preprocessing, model development, training, evaluation, and visualization.

## Dataset

**MNIST Handwritten Digits Dataset**

- 60,000 training images
- 10,000 test images
- 28 × 28 grayscale images

### Dataset Source

MNIST Handwritten Digits Dataset — TensorFlow / Keras

https://www.tensorflow.org/api_docs/python/tf/keras/datasets/mnist

The dataset is downloaded automatically when the notebook is executed for the first time.

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

```text
├── CNN_Handwritten_Digit_Recognition.ipynb
├── README.md
└── requirements.txt
```

## Model Architecture

- Input Layer
- Conv2D (32, ReLU)
- MaxPooling2D
- Conv2D (64, ReLU)
- MaxPooling2D
- Flatten
- Dense (128, ReLU)
- Dropout (0.30)
- Softmax Output

The model uses the Adam optimizer, categorical cross-entropy loss, and Early Stopping.

## Technologies Used

- Python
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- TensorFlow
- Keras
- Jupyter Notebook

## Evaluation Metrics

- Accuracy
- Precision
- Recall
- F1 Score
- Classification Report
- Confusion Matrix

## Results

- **Test Accuracy:** 99.14%

The CNN achieved excellent performance with consistently high precision, recall, and F1-scores across all digit classes.

## Key Findings

- Test accuracy reached approximately **99.14%**.
- Training and validation performance converged smoothly.
- Very few misclassifications were observed.
- The CNN effectively learned spatial features from handwritten digits.

## Conclusion

This project demonstrates the effectiveness of Convolutional Neural Networks for handwritten digit recognition and provides a reproducible deep learning workflow suitable for computer vision tasks.
