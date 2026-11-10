<h1 align="center">Deep Learning Projects</h1>

<p align="center">
  24 deep learning projects, from basic neural networks to transformers, generative models, and reinforcement learning.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/TensorFlow-FF6F00?style=flat&logo=tensorflow&logoColor=white" alt="TensorFlow">
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white" alt="PyTorch">
  <img src="https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=jupyter&logoColor=white" alt="Jupyter">
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat" alt="MIT License">
</p>

---

## Overview

This repository contains the deep learning projects I completed while studying the field. Each project focuses on one architecture and applies it to a standard dataset, covering the full workflow from data preparation and model design to training, evaluation, and analysis of the results.

The projects are grouped by area below. Each one is self-contained in its own folder, with a Jupyter notebook, a README describing the approach and results, and a `requirements.txt` file.

## Contents

- [Neural Network Fundamentals](#neural-network-fundamentals)
- [Computer Vision](#computer-vision)
- [Sequence Models and NLP](#sequence-models-and-nlp)
- [Generative Models](#generative-models)
- [Graph Neural Networks and Reinforcement Learning](#graph-neural-networks-and-reinforcement-learning)
- [Getting Started](#getting-started)
- [License](#license)

## Neural Network Fundamentals

| Project | Dataset | Framework | Result |
|---------|---------|-----------|--------|
| [ANN Classification - Customer Churn Prediction](ANN%20Classification%20-%20Customer%20Churn%20Prediction) | Bank Customer Churn | TensorFlow | 86.8% accuracy, 0.869 ROC-AUC |
| [ANN Regression - Medical Cost Prediction](ANN%20Regression%20-%20Medical%20Cost%20Prediction) | Medical Insurance Costs | TensorFlow | R² of 0.837 |

## Computer Vision

| Project | Dataset | Framework | Result |
|---------|---------|-----------|--------|
| [CNN Classification - Handwritten Digit Recognition](CNN%20Classification%20-%20Handwritten%20Digit%20Recognition) | MNIST | TensorFlow | 99.14% accuracy |
| [CNN Classification - Fashion MNIST](CNN%20Classification%20-%20Fashion%20MNIST) | Fashion-MNIST | TensorFlow | 90.45% accuracy |
| [CNN Classification - CIFAR-10 Image Classification](CNN%20Classification%20-%20CIFAR-10%20Image%20Classification) | CIFAR-10 | TensorFlow | 77.86% accuracy |
| [Transfer Learning - MobileNetV2 Image Classification](Transfer%20Learning%20-%20MobileNetV2%20Image%20Classification) | CIFAR-10 | TensorFlow | 87.35% accuracy |
| [ResNet - Food-101 Image Classification](ResNet%20-%20Food-101%20Image%20Classification) | Food-101 | PyTorch | 86.78% accuracy |
| [ViT - CIFAR-100 Image Classification](ViT%20-%20CIFAR-100%20Image%20Classification) | CIFAR-100 | PyTorch | 91.92% accuracy |
| [U-Net - Oxford-IIIT Pet Image Segmentation](U-Net%20-%20Oxford-IIIT%20Pet%20Image%20Segmentation) | Oxford-IIIT Pet | PyTorch | 74.63% mean IoU |
| [YOLO - Pascal VOC Object Detection](YOLO%20-%20Pascal%20VOC%20Object%20Detection) | Pascal VOC | PyTorch | 84.47% mAP@0.50 |

## Sequence Models and NLP

| Project | Dataset | Framework | Result |
|---------|---------|-----------|--------|
| [RNN - IMDb Sentiment Analysis](RNN%20-%20IMDb%20Sentiment%20Analysis) | IMDb Reviews | TensorFlow | 80.79% accuracy |
| [LSTM - IMDb Sentiment Analysis](LSTM%20-%20IMDb%20Sentiment%20Analysis) | IMDb Reviews | TensorFlow | 87.08% accuracy |
| [GRU - IMDb Sentiment Analysis](GRU%20-%20IMDb%20Sentiment%20Analysis) | IMDb Reviews | TensorFlow | 85.66% accuracy |
| [Attention - AG News Classification](Attention%20-%20AG%20News%20Classification) | AG News | TensorFlow | 90.93% accuracy |
| [Transformer - 20 Newsgroups Classification](Transformer%20-%2020%20Newsgroups%20Classification) | 20 Newsgroups | TensorFlow | 62.41% accuracy |
| [BERT - TREC-6 Question Classification](BERT%20-%20TREC-6%20Question%20Classification) | TREC-6 | TensorFlow / KerasHub | 96.80% accuracy |
| [RoBERTa - BANKING77 Intent Classification](RoBERTa%20-%20BANKING77%20Intent%20Classification) | BANKING77 | PyTorch / Transformers | 85.65% accuracy |

## Generative Models

| Project | Dataset | Framework | Result |
|---------|---------|-----------|--------|
| [Autoencoder - MNIST Image Reconstruction](Autoencoder%20-%20MNIST%20Image%20Reconstruction) | MNIST | TensorFlow | 0.0055 reconstruction MSE |
| [Denoising Autoencoder - MNIST Image Reconstruction](Denoising%20Autoencoder%20-%20MNIST%20Image%20Reconstruction) | MNIST | TensorFlow | 0.0102 reconstruction MSE |
| [Variational Autoencoder - MNIST Digit Generation](Variational%20Autoencoder%20-%20MNIST%20Digit%20Generation) | MNIST | TensorFlow | New digits sampled from a 2D latent space |
| [DCGAN - CIFAR-10 Image Generation](DCGAN%20-%20CIFAR-10%20Image%20Generation) | CIFAR-10 | TensorFlow | 32×32 images generated over 100 epochs |
| [WGAN-GP - CelebA Face Generation](WGAN-GP%20-%20CelebA%20Face%20Generation) | CelebA | TensorFlow | 64×64 synthetic faces |

## Graph Neural Networks and Reinforcement Learning

| Project | Dataset | Framework | Result |
|---------|---------|-----------|--------|
| [GCN - Cora Node Classification](GCN%20-%20Cora%20Node%20Classification) | Cora | PyTorch | 78.70% accuracy |
| [DQN - CartPole Reinforcement Learning](DQN%20-%20CartPole%20Reinforcement%20Learning) | CartPole-v1 | PyTorch / Gymnasium | 500 reward in 20 of 20 evaluation episodes |

Results are reported on each project's test set, except for the generative models, which are evaluated mainly by the quality of their outputs. Full metrics, training details, and analysis are in each project's README.

## Getting Started

**Requirements:** Python 3.10 or later and Jupyter. Several projects were trained on a GPU in Google Colab, which is recommended for the larger models.

Clone the repository:

```bash
git clone https://github.com/praneeth-cs/Deep-Learning-Projects.git
cd Deep-Learning-Projects
```

Each project lists its own dependencies in its `requirements.txt` file. Most datasets are downloaded automatically when the notebook runs.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
