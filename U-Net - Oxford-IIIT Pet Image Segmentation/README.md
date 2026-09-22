# U-Net - Oxford-IIIT Pet Image Segmentation

A PyTorch implementation of U-Net for semantic segmentation on the Oxford-IIIT Pet dataset. The model takes a pet image as input and predicts a class for each pixel: foreground, background, or border.

## Overview

This project focuses on image segmentation rather than image classification. Instead of assigning one label to the whole image, the network produces a pixel-level mask.

The notebook covers the full workflow from loading the dataset and preparing the masks to training the U-Net, checking the training curves, evaluating the model, and looking at predicted segmentation masks.

## Dataset

The project uses the Oxford-IIIT Pet dataset with the segmentation annotations provided with the dataset.

The data used in the notebook is split as follows:

- 2,944 training images
- 736 validation images
- 3,669 test images

Images are resized to 128 × 128 pixels before being used by the model.

The segmentation masks contain three classes:

- Foreground
- Background
- Border

## Dataset Source

Oxford-IIIT Pet Dataset

The dataset is downloaded through Torchvision using the `OxfordIIITPet` dataset loader. It is not included in this repository.

## Notebook Structure

1. Project Overview
2. Import Required Libraries
3. Configure Reproducibility and Runtime
4. Define Dataset Paths and Configuration
5. Load Oxford-IIIT Pet Segmentation Data
6. Create Train, Validation, and Test Splits
7. Build the Segmentation Dataset Pipeline
8. Inspect Sample Images and Masks
9. Define Segmentation Metrics
10. Build the U-Net
11. Inspect the Network Parameters
12. Create DataLoaders
13. Configure Loss, Optimizer, and Scheduler
14. Define Training and Validation Functions
15. Train the U-Net
16. Plot Training History
17. Evaluate the Trained Model
18. Inspect Per-Class IoU
19. Visualize Segmentation Predictions
20. Key Findings
21. Conclusion

## Repository Contents

U-Net - Oxford-IIIT Pet Image Segmentation/
├── UNet_OxfordIIIT_Pet_Image_Segmentation.ipynb
├── README.md
└── requirements.txt

The dataset is downloaded automatically when the notebook is run.

## Model Architecture

The model follows the standard U-Net idea of combining an encoder with a decoder and using skip connections between matching stages.

The encoder starts with RGB input and increases the number of feature channels through the network:

3 → 32 → 64 → 128 → 256 → 512

The decoder then brings the spatial resolution back up:

512 → 256 → 128 → 64 → 32

The encoder features are passed to the decoder through skip connections so that spatial details lost during downsampling can be recovered.

A final 1 × 1 convolution produces three output channels for the three segmentation classes.

The model has 7,763,107 trainable parameters.

## Training

The model was trained with the AdamW optimizer.

The loss combines cross-entropy loss with multiclass Dice loss:

Total Loss = Cross-Entropy Loss + Dice Loss

A cosine annealing learning-rate schedule was used during training. Gradient clipping and mixed-precision training were also used.

The model with the highest validation mean IoU was saved and used for the final test evaluation.

## Training Configuration

Images were resized to 128 × 128 and trained with a batch size of 16.

The main training settings were:

- Epochs: 15
- Learning rate: 0.001
- Weight decay: 0.0001
- Optimizer: AdamW
- Scheduler: CosineAnnealingLR
- Number of classes: 3
- Random seed: 42

## Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- PyTorch
- Torchvision
- Jupyter Notebook

## Runtime

The notebook was executed in Google Colab using an NVIDIA Tesla T4 GPU.

CUDA and mixed-precision training were enabled during the run.

## Evaluation

The model was evaluated using:

- Test loss
- Pixel accuracy
- Mean IoU
- Per-class IoU

The notebook also compares the predicted masks with the ground-truth masks and shows prediction overlays on the original images.

## Results

The best validation mean IoU was 0.7426 at epoch 15.

On the test set, the model achieved:

- Test loss: 0.4639
- Pixel accuracy: 90.27%
- Mean IoU: 74.63%

The class-wise IoU values were:

- Foreground: 81.78%
- Background: 90.19%
- Border: 51.92%

The background class was segmented most accurately, while the border class was the most difficult to predict.

## Key Findings

The model improved steadily during training and reached its best validation mean IoU at the final epoch.

The overall pixel accuracy was high at 90.27%, while the test mean IoU was 74.63%. The difference between these two numbers is expected in segmentation because pixel accuracy can remain high when large regions such as the background are predicted correctly.

Foreground segmentation was also strong, with an IoU of 81.78%. Border segmentation was lower at 51.92%, which was the weakest of the three classes.

The prediction visualizations show that the model learned the general structure of the pets and their surrounding regions, although some boundary areas remain harder to separate accurately.

## Conclusion

This project implements a U-Net segmentation model using PyTorch and the Oxford-IIIT Pet dataset.

After 15 epochs of training, the model reached a validation mean IoU of 0.7426 and a test mean IoU of 0.7463, with a test pixel accuracy of 90.27%.

The results show that the network can produce useful pixel-level masks for foreground, background, and border regions. The main area for improvement is the border class, where finer spatial detail and boundary information are more difficult for the model to capture.