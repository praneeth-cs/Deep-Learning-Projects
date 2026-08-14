# Attention Mechanism - AG News Topic Classification

## Overview

This project applies an additive attention mechanism to multi-class news topic classification using the AG News dataset. A bidirectional LSTM first encodes the sequence, after which the attention layer assigns different weights to sequence positions and produces a weighted context representation for classification. The notebook covers text preprocessing, model development, training, evaluation, error analysis, and attention-weight visualization.

## Dataset

**AG News Dataset**

- 120,000 training articles
- 7,600 test articles
- 4 topic categories
- 30,000 articles per class in the original training set
- Categories:
  - World
  - Sports
  - Business
  - Sci/Tech

The original training set was divided into 96,000 training samples and 24,000 validation samples.

## Dataset Source

TensorFlow Datasets - AG News Subset

https://www.tensorflow.org/datasets/catalog/ag_news_subset

The dataset is downloaded automatically when the notebook is executed and is not included in this repository.

## Notebook Structure

1. Import Required Libraries
2. Load the AG News Dataset
3. Explore the Dataset
4. Preprocess the Text
5. Create TensorFlow Input Pipelines
6. Build the BiLSTM with Attention
7. Train the Model
8. Training Curves
9. Evaluate the Model
10. Classification Report
11. Confusion Matrix
12. Visualize Attention Weights
13. Key Findings
14. Conclusion

## Repository Contents

Attention - AG News Classification/
├── Attention_AG_News_Classification.ipynb
├── README.md
└── requirements.txt

## Model Architecture / Methodology

The model uses the following sequence:

Text
↓
TextVectorization
↓
Embedding
↓
Bidirectional LSTM
↓
Additive Attention
↓
Dense Layer
↓
4-Class Softmax Output

Model configuration:

- Vocabulary size: 20,000
- Maximum sequence length: 200 tokens
- Embedding dimension: 128
- Bidirectional LSTM: 64 units per direction
- Additive attention layer
- Dense classification layer: 64 units
- Output layer: 4 classes
- Adam optimizer
- Sparse categorical crossentropy
- EarlyStopping with restored best weights

## Technologies Used

- Python
- NumPy
- Matplotlib
- Scikit-learn
- TensorFlow
- TensorFlow Datasets
- Jupyter Notebook

## Evaluation Metrics

- Accuracy
- Precision
- Recall
- F1-Score
- Classification Report
- Confusion Matrix
- Attention Weight Visualization

## Results

- **Best Validation Accuracy:** **90.75%**
- **Best Validation Loss:** **0.2772**
- **Best Epoch:** **2**
- **Test Accuracy:** **90.93%**
- **Test Loss:** **0.2659**
- **Weighted F1-Score:** **0.9091**

Class-level performance:

- **World:** F1-score **0.9120**
- **Sports:** F1-score **0.9621**
- **Business:** F1-score **0.8764**
- **Sci/Tech:** F1-score **0.8860**

## Key Findings

- The BiLSTM with attention achieved **90.93% test accuracy** on AG News classification.
- The model reached its best validation performance at **Epoch 2**, after which training accuracy continued increasing while validation performance declined.
- Sports was the strongest-performing category, achieving an F1-score of **0.9621**.
- Business was the most difficult category, achieving an F1-score of **0.8764**.
- Attention visualization provided token-level insight into which parts of selected news articles contributed most strongly to the model's predictions.
- The results demonstrate that attention can produce a focused sequence representation by assigning different weights to different positions in the input text.

## Conclusion

The attention-based BiLSTM achieved strong performance on AG News topic classification while providing an interpretable view of the sequence representation through attention weights. The model achieved **90.93% test accuracy** and maintained balanced performance across the four categories.

The training behaviour also showed clear overfitting after the second epoch, making EarlyStopping important for retaining the model with the strongest validation performance.