# WGAN-GP - CelebA Face Generation

## Overview

This project implements a Wasserstein Generative Adversarial Network with Gradient Penalty (WGAN-GP) to generate synthetic 64×64 RGB face images using the CelebA dataset.

The project extends the earlier DCGAN work by replacing the conventional binary-classification GAN objective with the Wasserstein objective and gradient penalty. The notebook focuses on adversarial training stability, generator and critic design, generated-image progression, latent-space interpolation, and qualitative evaluation.

Runtime: Google Colab  
Recommended GPU: NVIDIA Tesla T4  
Image Resolution: 64 × 64 RGB

## Dataset

**CelebA Dataset**

The CelebA dataset contains more than 200,000 celebrity face images with multiple facial attributes and standardized train, validation, and test partitions.

For this project, the images are resized to 64×64 RGB before being supplied to the WGAN-GP pipeline.

## Dataset Source

Kaggle — CelebA Dataset

https://www.kaggle.com/datasets/jessicali9530/celeba-dataset

The dataset is downloaded automatically through the Kaggle API when the notebook is executed and is not included in this repository.

## Notebook Structure

1. Import Required Libraries
2. Configure Reproducibility and Training
3. Load the CelebA Dataset
4. Inspect the Dataset
5. Preprocess the Images
6. Build the Generator
7. Build the Critic
8. Inspect the Model Architectures
9. Define the WGAN-GP Objective
10. Define the WGAN-GP Training Steps
11. Train the WGAN-GP
12. Visualize Training Progress
13. Evaluate Final Generated Faces
14. Latent Space Interpolation
15. Fixed-Noise Comparison
16. Key Findings
17. Conclusion

## Model Architecture / Methodology

- Wasserstein Generative Adversarial Network with Gradient Penalty
- Convolutional generator
- Convolutional critic
- 128-dimensional latent space
- 64×64 RGB output images
- Wasserstein critic objective
- Gradient penalty for Lipschitz constraint
- Adam optimizer
- Five critic updates per generator update
- Gradient penalty weight of 10
- 30,000 training images
- 20-epoch primary experiment
- Fixed-noise visualization
- Latent-space interpolation

## Training Configuration

- Image size: 64×64
- Batch size: 64
- Latent dimension: 128
- Training images: 30,000
- Epochs: 20
- Generator learning rate: 1e-4
- Critic learning rate: 1e-4
- Adam beta1: 0.0
- Adam beta2: 0.9
- Critic steps: 5
- Gradient penalty weight: 10.0

## Technologies Used

- Python
- NumPy
- Matplotlib
- TensorFlow
- Kaggle API
- Jupyter Notebook
- Google Colab

## Evaluation

Generative quality is evaluated primarily through qualitative inspection of generated image grids.

The notebook includes:

- Training loss curves
- Wasserstein loss
- Gradient penalty
- Generated-image progression
- Final generated face grid
- Latent-space interpolation
- Fixed-noise comparison

No FID or other automated image-quality metric was used in the final experiment.

## Results

The 20-epoch experiment produced recognizable synthetic faces with visible facial structure. The model successfully learned broad characteristics of the CelebA face distribution, although the generated images remained limited in fine detail at 64×64 resolution.

A separate 50-epoch experiment was also performed. Extending training from 20 to 50 epochs did not improve the generated samples. Instead, the later checkpoint produced visibly worse faces, demonstrating that additional adversarial training can move the generator away from a better qualitative state.

The 20-epoch run was therefore selected as the primary result for this project.

## Key Findings

WGAN-GP successfully learned to generate recognizable face-like images from CelebA while providing a more stable training objective than a conventional GAN formulation.

The gradient penalty remained controlled during training, while the generated samples demonstrated progressive learning of facial structure.

The comparison between the 20-epoch and 50-epoch experiments showed that more training does not necessarily produce better generative quality. Monitoring generated samples and selecting an appropriate checkpoint is therefore important when training GANs.

The experiment also highlighted the computational cost of WGAN-GP, particularly when using multiple critic updates and gradient-penalty calculations on a limited Google Colab NVIDIA Tesla T4 GPU.

## Conclusion

This project demonstrates a practical implementation of WGAN-GP for CelebA face generation. The model successfully learned meaningful facial structure and generated recognizable synthetic faces using a 128-dimensional latent space and 64×64 RGB output.

The project also demonstrates an important characteristic of adversarial training: increasing the number of epochs is not guaranteed to improve image quality. In this experiment, the 20-epoch result was visually preferable to the 50-epoch result, making checkpoint selection an important part of the evaluation process.

Overall, the project provides a practical introduction to Wasserstein GANs, gradient penalties, adversarial training dynamics, and qualitative evaluation of generated images under limited computational resources.