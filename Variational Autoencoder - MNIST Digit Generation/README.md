# Variational Autoencoder (VAE) - MNIST Digit Generation

## Overview

This project implements a Variational Autoencoder (VAE) to learn a two-dimensional probabilistic latent representation of handwritten digits from the MNIST dataset. Unlike a conventional Autoencoder, the encoder learns the parameters of a probability distribution rather than a single deterministic latent vector. The model combines reconstruction loss with KL-divergence regularization and is evaluated through image reconstruction, latent-space visualization, random sampling, and latent-space traversal.

## Dataset

**MNIST Handwritten Digit Dataset**

- 60,000 training images
- 10,000 test images
- 28 × 28 grayscale images
- 10 digit classes
- Pixel values normalized to the range [0, 1]

The original training set is divided into 48,000 training samples and 12,000 validation samples.

## Dataset Source

TensorFlow / Keras MNIST Dataset

https://www.tensorflow.org/api_docs/python/tf/keras/datasets/mnist

The dataset is downloaded automatically when the notebook is executed and is not included in this repository.

## Notebook Structure

1. Import Required Libraries
2. Load the MNIST Dataset
3. Explore the Dataset
4. Build the Encoder and Decoder
5. Define the VAE
6. Train the VAE
7. Training Curves
8. Evaluate the VAE
9. Reconstruct Test Images
10. Visualize the Latent Space
11. Generate New Digits
12. Latent Space Traversal
13. Key Findings
14. Conclusion

## Repository Contents

Variational Autoencoder - MNIST Digit Generation/
├── Variational_Autoencoder_MNIST_Digit_Generation.ipynb
├── README.md
└── requirements.txt

## Model Architecture / Methodology

The VAE uses a fully connected encoder-decoder architecture with a two-dimensional latent space.

784
↓
256
↓
128
↓
μ, log(σ²)
↓
z ∈ R²
↓
128
↓
256
↓
784

The encoder produces the mean and log-variance of the latent distribution. The reparameterization step samples a latent vector from this distribution before passing it to the decoder.

The model optimizes two objectives:

- Reconstruction loss
- KL divergence

The total VAE loss is the sum of these two components.

## Technologies Used

- Python
- NumPy
- Matplotlib
- Scikit-learn
- TensorFlow
- Jupyter Notebook

## Evaluation Metrics

- Total VAE Loss
- Reconstruction Loss
- KL Divergence
- Validation Loss
- Test Loss
- Original vs Reconstructed Images
- 2D Latent-Space Visualization
- Randomly Generated Samples
- Latent-Space Traversal

## Results

- **Best Validation Loss:** **51.3550**
- **Best Epoch:** **30**
- **Test Total Loss:** **10.6101**
- **Test Reconstruction Loss:** **5.8647**
- **Test KL Loss:** **4.7455**

The learned two-dimensional latent space organized MNIST samples into meaningful regions, while random sampling and latent-space traversal produced new digit-like images.

## Key Findings

- The VAE learned a structured two-dimensional probabilistic latent representation of the MNIST dataset.
- The objective balanced image reconstruction with KL-divergence regularization.
- The latent-space visualization showed meaningful separation and structure among the digit classes.
- Random samples generated from the latent distribution produced recognizable digit-like outputs.
- Latent-space traversal demonstrated continuous changes in generated digit structure across nearby points in the learned representation.

## Conclusion

The Variational Autoencoder successfully demonstrated probabilistic representation learning and generative sampling on MNIST. By learning a distribution rather than a single deterministic encoding, the model produced a structured latent space from which new digit-like samples could be generated.

The experiment shows how KL-divergence regularization and stochastic latent sampling extend the capabilities of conventional Autoencoders from reconstruction toward generative modelling.