# Autoencoder (AE) - MNIST Image Reconstruction

## Overview

This project implements a fully connected Autoencoder to learn a compact representation of handwritten digits from the MNIST dataset. The model compresses each 28×28 image into a 64-dimensional latent representation and reconstructs the original image from this compressed representation. The project demonstrates unsupervised representation learning, dimensionality reduction, and image reconstruction using TensorFlow/Keras.

## Dataset

**MNIST Handwritten Digit Dataset**

- 60,000 training images
- 10,000 test images
- 28 × 28 grayscale images
- Pixel values normalized to the range [0, 1]
- Class labels are not used as the reconstruction target

A validation set is created from the training data during preprocessing.

## Dataset Source

TensorFlow / Keras MNIST Dataset

https://www.tensorflow.org/api_docs/python/tf/keras/datasets/mnist

The dataset is downloaded automatically when the notebook is executed and is not included in this repository.

## Notebook Structure

1. Import Required Libraries
2. Load the MNIST Dataset
3. Explore the Dataset
4. Build the Autoencoder
5. Train the Model
6. Training Curves
7. Reconstruct Test Images
8. Visual Comparison
9. Reconstruction Error Analysis
10. Latent Representation
11. Model Evaluation
12. Discussion
13. Key Findings
14. Conclusion

## Repository Contents

```text
Autoencoder - MNIST Image Reconstruction/
├── Autoencoder_MNIST_Image_Reconstruction.ipynb
├── README.md
└── requirements.txt
```

## Model Architecture / Methodology

The Autoencoder uses a fully connected encoder-decoder architecture:

```text
784
 ↓
256
 ↓
128
 ↓
64  ← Latent Representation
 ↓
128
 ↓
256
 ↓
784
```

- Input dimension: 784
- Latent representation: 64 dimensions
- ReLU activations in hidden layers
- Sigmoid activation in the output layer
- Adam optimizer
- Mean Squared Error (MSE) reconstruction loss
- EarlyStopping with restored best weights

The model is trained to reconstruct each input image rather than predict its digit class.

## Technologies Used

- Python
- NumPy
- Matplotlib
- Scikit-learn
- TensorFlow
- Jupyter Notebook

## Evaluation Metrics

- Mean Squared Error (MSE)
- Training Loss
- Validation Loss
- Mean Reconstruction Error
- Reconstruction Error Distribution
- Original vs Reconstructed Images

## Results

- **Mean Reconstruction Error:** **0.005511**
- **Minimum Validation Loss:** **0.005753**
- **Latent Representation:** **64 dimensions**
- **Original Representation:** **784 dimensions**

The Autoencoder successfully reconstructed the main structural characteristics of the MNIST digits while compressing the original 784-dimensional input into a 64-dimensional latent representation.

## Key Findings

- The model achieved a mean reconstruction error of **0.005511** on the test set.
- Validation loss reached **0.005753**, indicating low reconstruction error on unseen validation data.
- Training and validation loss showed consistent convergence without a substantial generalization gap.
- The 784-dimensional input was compressed into a 64-dimensional latent representation while retaining the dominant visual structure of the digits.
- Reconstructed images preserved the overall identity and shape of the handwritten digits, although some fine visual details were lost.
- Reconstruction error varied between samples, with less typical or visually complex digits producing larger errors.

## Conclusion

The Autoencoder successfully learned a compact representation of MNIST images without using class labels as prediction targets. By reducing each 784-dimensional image to a 64-dimensional latent representation, the model retained the primary structural information required to reconstruct the original images with low reconstruction error.

This project establishes the foundation for more advanced representation-learning approaches, including denoising Autoencoders and Variational Autoencoders, where the latent representation becomes the central focus of the modelling process.