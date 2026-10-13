# Vision Transformer (ViT) – CIFAR-100 Image Classification

## Overview

This project fine-tunes a pretrained Vision Transformer (ViT-Small) for image classification on CIFAR-100. Instead of training the model from scratch, it uses visual representations learned through ImageNet pretraining and adapts the classifier to recognize 100 CIFAR-100 classes.

The notebook includes dataset preparation, augmentation, model configuration, training, validation, checkpoint selection, test evaluation, class-wise analysis, confusion-matrix visualization, and prediction-confidence analysis. The objective is to evaluate how transfer learning improves classification performance on a small-image dataset.

## Dataset

CIFAR-100 contains 60,000 color images across 100 classes, with 600 images per class. Each original image is 32 × 32 pixels and belongs to one of 20 superclasses.

The dataset is divided into three subsets:

| Split | Images | Purpose |
|---|---:|---|
| Training | 45,000 | Model fine-tuning |
| Validation | 5,000 | Model selection and performance monitoring |
| Test | 10,000 | Final evaluation |

The training and validation sets are created from the official 50,000-image training split using a fixed random seed. The official 10,000-image test split is retained for final evaluation.

### Dataset Source

- [CIFAR-100 Dataset — University of Toronto](https://www.cs.toronto.edu/~kriz/cifar.html)
- [PyTorch CIFAR-100 Dataset Documentation](https://docs.pytorch.org/vision/stable/generated/torchvision.datasets.CIFAR100.html)

The notebook downloads the dataset through `torchvision.datasets.CIFAR100`.

## Model Architecture and Methodology

The project uses the pretrained checkpoint `vit_small_patch16_224.augreg_in21k_ft_in1k`, loaded through the `timm` library. The model has 21,704,164 parameters, with the classification head adapted to the 100 CIFAR-100 classes.

The original CIFAR-100 images are transformed to 224 × 224 pixels to match the pretrained model's input configuration. Training augmentation includes random resized cropping, horizontal flipping, RandAugment, and random erasing. Evaluation uses deterministic resizing and center cropping.

Fine-tuning uses AdamW with separate learning rates for the pretrained backbone and the classification head. Label smoothing, weight decay, gradient clipping, mixed-precision training, warmup, and cosine learning-rate decay are used to support stable optimization and generalization.

### Training Configuration

| Parameter | Value |
|---|---|
| Model | Pretrained ViT-Small |
| Pretraining | ImageNet-21k, followed by ImageNet-1k fine-tuning |
| Input resolution | 224 × 224 |
| Patch size | 16 × 16 |
| Batch size | 64 |
| Training epochs | 30 |
| Backbone learning rate | 0.00003 |
| Classifier learning rate | 0.0003 |
| Optimizer | AdamW |
| Weight decay | 0.05 |
| Label smoothing | 0.1 |
| Warmup fraction | 0.05 |
| Random seed | 42 |
| Mixed precision | Enabled on CUDA |
| DataLoader workers | 2 |

## Notebook Structure

The notebook is organized into 22 sections:

1. Install Libraries and Check Runtime
2. Configure Reproducibility and Training
3. Load CIFAR-100 and Create Dataset Splits
4. Inspect the Dataset
5. Load the Pretrained Vision Transformer
6. Inspect Model Architecture
7. Prepare Training Utilities
8. Train and Validate the Model
9. Inspect Training History
10. Plot Training and Validation Metrics
11. Load the Best Checkpoint
12. Evaluate on the Test Set
13. Summarize Classification Metrics
14. Analyze Class-wise Performance
15. Plot the Confusion Matrix
16. Select Test Images
17. Run Sample Predictions
18. Visualize Predictions
19. Inspect Prediction Confidence
20. References and Result Context
21. Key Findings
22. Conclusion

## Technologies Used

- Python
- PyTorch
- Torchvision
- `timm`
- NumPy
- Pandas
- Matplotlib
- Pillow
- Scikit-learn
- Hugging Face Hub

## Runtime Environment

The completed experiment was executed in Google Colab with the following environment:

| Component | Version or Configuration |
|---|---|
| Python | 3.13.15 |
| PyTorch | 2.11.0+cu130 |
| Torchvision | 0.26.0+cu130 |
| timm | 1.0.30 |
| CUDA | 13.0 |
| GPU | NVIDIA Tesla T4 |

The pretrained checkpoint is downloaded from Hugging Face when the model is initialized. An internet connection is therefore required when the weights are not already cached.

## Evaluation Metrics

The notebook evaluates the selected checkpoint using:

- **Test loss:** Cross-entropy loss with label smoothing.
- **Accuracy:** Proportion of correctly classified test images.
- **Macro precision and recall:** Unweighted averages of class-level precision and recall.
- **Macro F1-score:** Unweighted average of the class-level F1-scores.
- **Weighted F1-score:** F1-score averaged according to class support.
- **Class-wise performance:** Precision, recall, F1-score, and support for each category.
- **Confusion matrix:** Distribution of classification errors among the 100 classes.
- **Prediction confidence:** Comparison of confidence scores for correct and incorrect predictions.

## Results

The best validation checkpoint was selected at epoch 24 and then evaluated on the official test split.

| Metric | Result |
|---|---:|
| Best validation accuracy | 92.22% |
| Test loss | 1.0327 |
| Test accuracy | 91.92% |
| Test macro precision | 91.96% |
| Test macro recall | 91.92% |
| Test macro F1-score | 91.90% |
| Test weighted F1-score | 91.90% |
| Correct test predictions | 9,192 / 10,000 |
| Incorrect test predictions | 808 / 10,000 |

The model reached 97.54% training accuracy and 92.02% validation accuracy by the end of training. The difference indicates some overfitting, although validation performance remained strong.

### Class-wise Performance

The strongest class-wise F1-scores included Tank at 99.50%, Sunflower at 99.00%, and Orange, Butterfly, and Skunk at 98.50%.

The most challenging classes included Maple Tree at 71.00%, Oak Tree at 71.20%, Boy at 74.90%, and Girl at 75.00%. These results highlight the difficulty of distinguishing visually similar categories.

Mean prediction confidence was 88.84% for correct predictions and 63.20% for incorrect predictions. Some errors nevertheless received high confidence, suggesting that prediction confidence is not perfectly calibrated.

## Key Findings

The pretrained ViT-Small model substantially improved performance over the previous from-scratch ViT experiment, which achieved 51.61% test accuracy. This comparison highlights the benefit of transfer learning for CIFAR-100 classification.

The best validation accuracy occurred at epoch 24 rather than at the final epoch. Selecting the checkpoint according to validation performance ensured that final evaluation used the strongest recorded validation model.

Class-wise metrics revealed that performance varies across categories, especially among visually similar objects and human categories. The confidence analysis also showed that incorrect predictions generally had lower confidence, while some high-confidence errors remained.

## Conclusion

This project demonstrates an effective transfer-learning workflow for CIFAR-100 using a pretrained Vision Transformer. The final model achieved 91.92% test accuracy and a 91.90% macro F1-score, substantially improving on the earlier from-scratch implementation.

The experiment also illustrates the importance of pretrained weights, data augmentation, learning-rate scheduling, validation-based checkpoint selection, and class-wise evaluation. Further work could investigate confidence calibration, stronger training strategies, and targeted improvements for visually similar classes.