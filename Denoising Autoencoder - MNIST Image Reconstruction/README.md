# Denoising Autoencoder (DAE) - MNIST Image Reconstruction

## Overview

This project extends a standard Autoencoder by training a model to reconstruct clean MNIST images from deliberately corrupted inputs. Gaussian noise is added to the input images while the original clean images are retained as reconstruction targets. The project demonstrates robust representation learning, image denoising, latent compression, and reconstruction using TensorFlow/Keras.

## Dataset

**MNIST Handwritten Digit Dataset**

- 60,000 training images
- 10,000 test images
- 28 × 28 grayscale images
- Pixel values normalized to the range [0, 1]
- Class labels are not used as prediction targets

The original training set is divided into 48,000 training samples and 12,000 validation samples.

## Dataset Source

TensorFlow / Keras MNIST Dataset

https://www.tensorflow.org/api_docs/python/tf/keras/datasets/mnist

The dataset is downloaded automatically when the notebook is executed and is not included in this repository.

## Notebook Structure

1. Import Required Libraries
2. Load the MNIST Dataset
3. Create Noisy Inputs
4. Explore Clean and Noisy Images
5. Build the Denoising Autoencoder
6. Train the Model
7. Training Curves
8. Reconstruct Test Images
9. Visual Comparison
10. Reconstruction Error Analysis
11. Latent Representation
12. Model Evaluation
13. Key Findings
14. Conclusion

## Repository Contents

Denoising Autoencoder - MNIST Image Reconstruction/
├── Denoising_Autoencoder_MNIST_Image_Reconstruction.ipynb
├── README.md
└── requirements.txt

## Model Architecture / Methodology

The Denoising Autoencoder uses a fully connected encoder-decoder architecture:

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

- Input dimension: 784
- Latent representation: 64 dimensions
- ReLU activations in hidden layers
- Sigmoid activation in the output layer
- Gaussian input noise
- Noise factor: 0.30
- Adam optimizer
- Mean Squared Error (MSE) reconstruction loss
- EarlyStopping with restored best weights

The model receives noisy images as inputs and uses the corresponding clean images as reconstruction targets.

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
- Test Reconstruction Loss
- Mean Reconstruction Error
- Median Reconstruction Error
- Maximum Reconstruction Error
- Reconstruction Error Distribution
- Clean vs Noisy vs Reconstructed Images

## Results

- **Best Validation Loss:** **0.010612**
- **Best Epoch:** **29**
- **Test Reconstruction Loss:** **0.010230**
- **Mean Reconstruction Error:** **0.010230**
- **Median Reconstruction Error:** **0.009636**
- **Maximum Reconstruction Error:** **0.040900**

The model successfully reconstructed clean MNIST digits from noisy inputs while retaining the main structural characteristics of the original images.

## Key Findings

- The Denoising Autoencoder learned to reconstruct clean images from inputs corrupted with Gaussian noise.
- The model achieved a test reconstruction loss of **0.010230**.
- The best validation loss of **0.010612** was reached at Epoch 29.
- Reconstruction errors varied across samples, with a median error of **0.009636** and a maximum of **0.040900**.
- The 784-dimensional images were compressed into a 64-dimensional latent representation while preserving the dominant structure of the handwritten digits.

## Conclusion

The Denoising Autoencoder demonstrated that an Autoencoder can learn representations that are robust to corrupted inputs rather than simply reproducing clean data. The model successfully reconstructed clean MNIST digits from noisy inputs with a low reconstruction error while maintaining a compact 64-dimensional latent representation.

The results show that the network learned the underlying structural characteristics of the handwritten digits despite the corruption introduced at the input, demonstrating the effectiveness of denoising reconstruction as a representation-learning task.