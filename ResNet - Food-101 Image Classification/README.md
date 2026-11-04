# ResNet-50 – Food-101 Image Classification

## Overview

This project uses transfer learning with an ImageNet-pretrained ResNet-50 model to classify food images across 101 categories. The model is trained in two stages: first, the classification head is trained while the pretrained backbone is frozen; then, the full network is fine-tuned on Food-101.

The workflow includes dataset exploration, stratified validation splitting, image augmentation, mixed-precision training, checkpoint selection, test evaluation, class-wise performance analysis, confusion matrix visualization, and sample prediction analysis.

The experiment was executed in **Google Colab using an NVIDIA Tesla T4 GPU**.

## Dataset

**Food-101**

- 101 food categories
- 75,750 official training images
- 25,250 official test images
- 1,000 images per category in the complete dataset
- RGB food images

A stratified split of 5,000 images was reserved from the official training set for validation, leaving 70,750 images for model training. The official test split was kept separate for final evaluation.

## Dataset Source

Food-101 Dataset — Torchvision

https://pytorch.org/vision/stable/generated/torchvision.datasets.Food101.html

The dataset is downloaded automatically through Torchvision when the notebook is executed. It is not included in this repository.

## Notebook Structure

1. Import Libraries and Check Runtime
2. Configure Reproducibility and Training
3. Load the Food-101 Dataset
4. Inspect the Dataset
5. Create Training and Validation Splits
6. Define Image Transforms
7. Build DataLoaders
8. Load Pretrained ResNet-50
9. Inspect Model Architecture
10. Prepare Training Utilities
11. Train the Classification Head
12. Fine-Tune ResNet-50
13. Inspect Training History
14. Plot Training and Validation Metrics
15. Load the Best Checkpoint
16. Evaluate on the Test Set
17. Summarize Classification Metrics
18. Analyze Class-wise Performance
19. Plot the Confusion Matrix
20. Run Sample Predictions
21. Visualize Sample Predictions
22. Inspect Prediction Confidence
23. Key Findings
24. Conclusion

## Repository Contents

```text
ResNet - Food-101 Image Classification/
├── ResNet50_Food_101_Image_Classification.ipynb
├── README.md
└── requirements.txt
```

## Model Architecture and Methodology

The project uses ResNet-50 with ImageNet-1K V2 pretrained weights.

- ResNet-50 convolutional backbone
- Pretrained ImageNet feature extractor
- Replaced final fully connected layer with a 101-class classifier
- Total parameters: 23,714,981
- Two-stage transfer learning
- Stratified training-validation split
- Random resized cropping and horizontal flipping
- RandAugment and Random Erasing
- ImageNet normalization
- AdamW optimizer
- Cross-entropy loss with label smoothing
- Cosine learning-rate scheduling
- Automatic mixed-precision training
- Gradient clipping
- Best-checkpoint selection based on validation accuracy

### Training Configuration

| Parameter | Value |
|---|---:|
| Image size | 224 × 224 |
| Batch size | 32 |
| Training epochs | 14 |
| Classification-head epochs | 3 |
| Fine-tuning epochs | 11 |
| Head learning rate | 0.001 |
| Backbone learning rate | 0.0001 |
| Fine-tuning head learning rate | 0.0005 |
| Weight decay | 0.0001 |
| Label smoothing | 0.1 |
| Random seed | 42 |

## Technologies Used

- Python
- PyTorch
- Torchvision
- NumPy
- Pandas
- Matplotlib
- Pillow
- Scikit-learn
- Jupyter Notebook
- Google Colab

## Evaluation Metrics

The model is evaluated using:

- Test loss
- Accuracy
- Macro precision
- Macro recall
- Macro F1-score
- Weighted F1-score
- Class-wise precision, recall, and F1-score
- Confusion matrix
- Prediction confidence analysis

## Results

The best validation checkpoint was selected at epoch 14, achieving a validation accuracy of **83.08%**.

Final evaluation on the official Food-101 test set produced:

| Metric | Result |
|---|---:|
| Test Loss | 0.6293 |
| Test Accuracy | **86.78%** |
| Macro Precision | 86.76% |
| Macro Recall | 86.78% |
| Macro F1-score | 86.70% |
| Weighted F1-score | 86.70% |
| Correct Predictions | 21,913 |
| Incorrect Predictions | 3,337 |

The model correctly classified 21,913 of the 25,250 official test images.

## Key Findings

The fine-tuned ResNet-50 achieved **86.78% test accuracy**, demonstrating strong classification performance across the 101 food categories.

The best validation accuracy was 83.08%. Training accuracy reached 98.11%, indicating a gap between training and validation performance and suggesting some overfitting.

The results show the value of pretrained ImageNet features and staged fine-tuning for a fine-grained image classification task. Class-wise evaluation and the confusion matrix provide additional insight into categories that remain difficult to distinguish.

## Conclusion

The project successfully applied transfer learning with ResNet-50 to the Food-101 image classification task. The final model achieved 86.78% test accuracy and an 86.70% macro F1-score.

Training the classifier head before fine-tuning the full network provided a structured approach to adapting pretrained visual features to food categories. The experiment also incorporated data augmentation, mixed-precision training, validation-based checkpoint selection, and detailed test-set evaluation.

Overall, the results establish a strong ResNet-50 baseline for fine-grained food image classification.