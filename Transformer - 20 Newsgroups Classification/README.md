# Transformer Encoder (Transformer) - 20 Newsgroups Classification

## Overview

This project implements a compact Transformer encoder for multi-class text classification on the 20 Newsgroups dataset. The model uses token and positional embeddings, multi-head self-attention, residual connections, layer normalization, feed-forward networks, and regularization through dropout and AdamW weight decay.

The experiment focuses on understanding the behaviour of a Transformer encoder trained from scratch for document classification without using a pretrained language model.

## Dataset

**20 Newsgroups Dataset**

- 18,846 documents
- 20 topic categories
- 11,314 original training documents
- 7,532 test documents
- Headers, footers, and quoted text removed before modelling
- Original training data split into training and validation sets using stratified sampling

The executed experiment used:

- **10,182 training documents**
- **1,132 validation documents**
- **7,532 test documents**

## Dataset Source

Scikit-learn 20 Newsgroups Dataset

https://scikit-learn.org/stable/modules/generated/sklearn.datasets.fetch_20newsgroups.html

The dataset is downloaded automatically when the notebook is executed and is not included in this repository.

## Notebook Structure

1. Import Required Libraries
2. Load the 20 Newsgroups Dataset
3. Explore the Dataset
4. Preprocess the Text
5. Create TensorFlow Input Pipelines
6. Build the Transformer Encoder
7. Train the Transformer
8. Training Curves
9. Evaluate the Model
10. Classification Report
11. Confusion Matrix
12. Error Analysis
13. Key Findings
14. Conclusion

## Repository Contents

Transformer - 20 Newsgroups Classification/
├── Transformer_20_Newsgroups_Classification.ipynb
├── README.md
└── requirements.txt

## Model Architecture / Methodology

The model uses the following architecture:

Text
↓
TextVectorization
↓
Token + Positional Embedding
↓
Transformer Encoder Block
↓
Transformer Encoder Block
↓
Masked Global Average Pooling
↓
Dense Layer
↓
20-Class Softmax Output

Configuration:

- Maximum vocabulary size: 20,000
- Sequence length: 256 tokens
- Token embedding dimension: 128
- Attention heads: 4
- Feed-forward dimension: 256
- Transformer encoder blocks: 2
- Dropout rate: 0.20
- Optimizer: AdamW
- Learning rate: 0.0003
- Weight decay: 0.00005
- Loss: Sparse categorical crossentropy
- EarlyStopping based on validation accuracy
- Best model weights restored after training

Padding-aware attention and masked global average pooling are used so padded sequence positions do not contribute to the learned document representation.

## Technologies Used

- Python
- NumPy
- Matplotlib
- Scikit-learn
- TensorFlow
- Jupyter Notebook

## Evaluation Metrics

- Accuracy
- Precision
- Recall
- F1-Score
- Macro Average F1-Score
- Weighted Average F1-Score
- Confusion Matrix
- Class-wise Accuracy
- Error Analysis

## Results

- **Best Validation Accuracy:** **70.41%**
- **Best Epoch:** **4**
- **Validation Loss at Best Epoch:** **1.2826**
- **Test Accuracy:** **62.41%**
- **Test Loss:** **1.7888**
- **Macro F1-Score:** **0.6170**
- **Weighted F1-Score:** **0.6280**

Class-level performance varied substantially.

Strongest classes by F1-score:

- **rec.sport.hockey:** **0.8582**
- **rec.sport.baseball:** **0.7866**
- **talk.politics.mideast:** **0.7545**
- **misc.forsale:** **0.7325**

Weakest classes by F1-score:

- **talk.religion.misc:** **0.2688**
- **alt.atheism:** **0.4148**
- **talk.politics.misc:** **0.4207**
- **sci.electronics:** **0.4832**

The model performed substantially better on categories with more distinctive topical vocabulary and struggled more on semantically overlapping categories.

## Key Findings

- The Transformer successfully learned useful representations for multi-class document classification from scratch.
- Validation accuracy reached **70.41% at Epoch 4**, after which training accuracy continued increasing while validation performance stopped improving, indicating overfitting.
- The final test accuracy was **62.41%**, with a weighted F1-score of **0.6280**.
- Performance varied considerably across categories, with **rec.sport.hockey** achieving the strongest F1-score of **0.8582** and **talk.religion.misc** the weakest at **0.2688**.
- Closely related categories involving religion, politics, and technical topics were more difficult to distinguish than categories with highly distinctive vocabulary.
- The difference between training and validation performance demonstrates the difficulty of training a Transformer from scratch on a relatively modest text classification dataset without pretrained language representations.

## Conclusion

The Transformer encoder demonstrated the core mechanics of self-attention-based sequence modelling, including positional information, multi-head self-attention, residual connections, normalization, feed-forward processing, and regularized optimization.

The model achieved **62.41% test accuracy** and a **0.6280 weighted F1-score** on the 20 Newsgroups dataset. Although the model learned useful topic representations, the substantial gap between training and validation performance showed that generalization remained a limiting factor.

The class-wise results further showed that performance depended strongly on topic overlap and vocabulary distinctiveness. Categories with clearer lexical signals were classified more reliably, while semantically related categories produced considerably more confusion.