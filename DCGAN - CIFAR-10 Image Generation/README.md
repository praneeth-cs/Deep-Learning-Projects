# DCGAN - CIFAR-10 Image Generation

A deep learning project that implements a Deep Convolutional Generative Adversarial Network (DCGAN) to generate synthetic 32×32 RGB images using the CIFAR-10 dataset.

## Overview

This project demonstrates an end-to-end generative modelling workflow using a convolutional Generator and Discriminator trained adversarially.

The notebook covers dataset exploration, image normalization, DCGAN architecture design, adversarial loss functions, generator and discriminator optimization, training progression, generated-image visualization, latent-space interpolation, and qualitative evaluation.

The project is implemented using TensorFlow and executed using a Google Colab NVIDIA Tesla T4 GPU.

## Dataset

**CIFAR-10 Dataset**

The dataset contains:

- 50,000 training images
- 10,000 test images
- 10 object categories
- 32 × 32 RGB images

The ten classes are:

- airplane
- automobile
- bird
- cat
- deer
- dog
- frog
- horse
- ship
- truck

The class labels are used for dataset exploration only. The DCGAN is trained as an unconditional generative model and does not receive class labels during training.

### Dataset Source

CIFAR-10 — TensorFlow / Keras

https://www.tensorflow.org/api_docs/python/tf/keras/datasets/cifar10

The dataset is downloaded automatically when the notebook is executed and is not included in this repository.

## Notebook Structure

The notebook follows the workflow below:

1. **Import Required Libraries**
2. **Configure Reproducibility and Training**
3. **Load the CIFAR-10 Dataset**
4. **Explore the Dataset**
5. **Preprocess the Images**
6. **Build the Generator**
7. **Build the Discriminator**
8. **Inspect the Model Architectures**
9. **Define GAN Losses and Optimizers**
10. **Define the Adversarial Training Step**
11. **Train the DCGAN**
12. **Visualize Training Progress**
13. **Evaluate Final Generated Samples**
14. **Latent Space Interpolation**
15. **Fixed-Noise Comparison**
16. **Training Findings**
17. **Conclusion**

## Repository Contents

DCGAN - CIFAR-10 Image Generation/
├── DCGAN_CIFAR10_Image_Generation.ipynb
├── README.md
└── requirements.txt

## Model Architecture

The project consists of two neural networks trained against each other.

### Generator

The Generator receives a 100-dimensional random latent vector and transforms it into a 32 × 32 RGB image.

The architecture progressively increases spatial resolution:

- Dense projection
- Reshape to 4 × 4 feature representation
- Transposed convolution to 8 × 8
- Transposed convolution to 16 × 16
- Transposed convolution to 32 × 32
- `tanh` output activation

Batch normalization and LeakyReLU activations are used in the intermediate Generator layers.

### Discriminator

The Discriminator receives either a real CIFAR-10 image or a generated image and produces a real/fake score.

The architecture progressively reduces spatial resolution:

- 32 × 32 input
- Convolution to 16 × 16
- Convolution to 8 × 8
- Convolution to 4 × 4
- Flatten
- Single output score

LeakyReLU activations and batch normalization are used in the convolutional layers.

## Methodology

The DCGAN is trained using adversarial optimization.

For every training step:

1. Random latent vectors are sampled.
2. The Generator produces synthetic images.
3. The Discriminator evaluates real images.
4. The Discriminator evaluates generated images.
5. Generator and Discriminator losses are calculated.
6. Gradients are computed separately.
7. Both networks are updated.

Binary cross-entropy is used for the adversarial objectives.

One-sided label smoothing is applied to real examples, and the Generator and Discriminator use separate Adam optimizers.

## Technologies Used

- Python
- NumPy
- Matplotlib
- TensorFlow
- Keras
- Jupyter Notebook
- Google Colab
- NVIDIA Tesla T4 GPU

## Evaluation

Because this is a generative modelling task, conventional classification accuracy is not applicable.

The project evaluates the model using:

- Generator loss
- Discriminator loss
- Generated-image progression
- Final generated-image grids
- Fixed-noise comparison
- Latent-space interpolation
- Qualitative image diversity
- Qualitative image recognizability
- Visual inspection for artifacts and mode collapse

## Results

The final experiment trained the DCGAN for **100 epochs**.

The final recorded losses were approximately:

- **Generator Loss:** 3.6709
- **Discriminator Loss:** 0.5055

The model successfully completed the full training run on the Google Colab NVIDIA Tesla T4 GPU.

Generated samples developed increasingly structured visual patterns during training. However, the final images remained limited in fine-grained object detail and did not consistently produce highly recognizable CIFAR-10 objects.

The latent-space interpolation experiment produced changing generated outputs as the latent representation was varied, providing an additional qualitative view of the learned generator.

## Key Findings

The DCGAN successfully learned non-trivial visual statistics from CIFAR-10 and progressed beyond pure random noise during training.

The second training configuration produced a more balanced adversarial interaction during the early stages of training, but the Discriminator gradually became stronger as training continued.

By the final epoch, the Generator loss had increased to approximately **3.67**, while the Discriminator loss had decreased to approximately **0.51**. This indicates that the Discriminator remained highly effective at distinguishing real images from generated samples during the later stages of training.

Increasing the training duration from 50 to 100 epochs therefore did not produce a proportional improvement in generation quality. The experiment demonstrates that GAN training depends on maintaining a balance between the Generator and Discriminator rather than simply increasing the number of training epochs.

The generated samples showed variation and did not exhibit obvious catastrophic mode collapse, but image quality remained limited by the compact DCGAN architecture and adversarial training objective.

## Conclusion

This project demonstrates the implementation and training of a Deep Convolutional Generative Adversarial Network for unconditional image generation on CIFAR-10.

The DCGAN successfully trained for 100 epochs and learned meaningful structure from the image distribution. However, the later training dynamics showed increasing Discriminator dominance, which limited continued improvement in the Generator.

The experiment highlights an important characteristic of GANs: successful training requires a stable balance between the Generator and Discriminator. A longer training schedule does not necessarily produce better generated images when the adversarial objectives become unbalanced.

The results provide a useful DCGAN baseline and establish a foundation for investigating more stable generative approaches such as WGAN-GP.