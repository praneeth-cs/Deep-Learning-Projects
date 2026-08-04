# Transfer Learning - MobileNetV2 Image Classification

## Overview

This project applies Transfer Learning using a pretrained MobileNetV2 model to classify images from the CIFAR-10 dataset. Rather than training an entire convolutional neural network from scratch, the pretrained ImageNet feature extractor is frozen while a custom classification head is trained for the target task. The notebook covers preprocessing, model development, training, evaluation, and prediction analysis using TensorFlow/Keras.

## Dataset

**CIFAR-10 Dataset**

- 50,000 training images
- 10,000 test images
- 10 object categories
- RGB images

## Dataset Source

TensorFlow / Keras CIFAR-10 Dataset

https://www.tensorflow.org/api_docs/python/tf/keras/datasets/cifar10

The dataset is downloaded automatically when the notebook is executed and is not included in this repository.

## Notebook Structure

1. Import Required Libraries
2. Load Dataset
3. Explore Dataset
4. Create Validation Set
5. Preprocess Images
6. Build Transfer Learning Model
7. Train the Model
8. Training Curves
9. Evaluate Model
10. Classification Report
11. Confusion Matrix
12. Sample Predictions
13. Misclassified Examples
14. Key Findings
15. Conclusion

## Repository Contents

```text
Transfer Learning - MobileNetV2 Image Classification/
├── Transfer_Learning_MobileNetV2_Image_Classification.ipynb
├── README.md
└── requirements.txt
```

## Model Architecture / Methodology

- MobileNetV2 pretrained on ImageNet
- Frozen feature extraction backbone
- Custom dense classification head
- Transfer Learning
- Stratified train-validation split
- TensorFlow `tf.data` pipeline
- Early Stopping
- Adam optimizer

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

- **Test Accuracy:** **87.35%**

Transfer learning produced a substantial improvement over the previous CNN trained from scratch while maintaining stable convergence and strong generalization.

## Key Findings

The pretrained MobileNetV2 feature extractor significantly outperformed the custom CNN baseline, improving test accuracy from **77.86%** to **87.35%**. Classification performance was strongest for visually distinctive classes, while cats and dogs remained the most difficult categories due to their visual similarity.

## Conclusion

This project demonstrates the effectiveness of transfer learning for image classification. By reusing pretrained ImageNet features, the model achieved substantially better performance than a CNN trained from scratch while requiring only the classification head to be optimized.