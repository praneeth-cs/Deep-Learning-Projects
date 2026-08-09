# Gated Recurrent Unit (GRU) - IMDb Sentiment Analysis

## Overview

This project applies a Gated Recurrent Unit (GRU) network to perform binary sentiment classification on the IMDb movie review dataset. The objective is to evaluate how a simplified gated recurrent architecture compares with both a vanilla Recurrent Neural Network (RNN) and a Long Short-Term Memory (LSTM) network while using an identical preprocessing pipeline and evaluation methodology.

---

## Dataset

**IMDb Movie Review Dataset**

- 25,000 training reviews
- 25,000 testing reviews
- Binary sentiment classification
- Reviews encoded as integer sequences

---

## Dataset Source

TensorFlow / Keras IMDb Dataset

https://www.tensorflow.org/api_docs/python/tf/keras/datasets/imdb

The dataset is downloaded automatically when the notebook is executed and is not included in this repository.

---

## Notebook Structure

1. Import Required Libraries
2. Load Dataset
3. Explore Dataset
4. Create Validation Set
5. Preprocess Data
6. Build GRU Model
7. Train Model
8. Training Curves
9. Evaluate Model
10. Classification Report
11. Confusion Matrix
12. Error Analysis
13. Discussion
14. Key Findings
15. Conclusion

---

## Repository Contents

```text
GRU - IMDb Sentiment Analysis/
├── GRU_IMDB_Sentiment_Analysis.ipynb
├── README.md
└── requirements.txt
```

---

## Model Architecture / Methodology

- Embedding Layer
- Gated Recurrent Unit (GRU)
- Dense Classification Head
- Binary Sentiment Classification
- Train / Validation / Test Split
- Sequence Padding
- EarlyStopping
- Adam Optimizer

---

## Technologies Used

- Python
- NumPy
- Matplotlib
- Scikit-learn
- TensorFlow
- Jupyter Notebook

---

## Evaluation Metrics

- Accuracy
- Precision
- Recall
- F1-Score
- Classification Report
- Confusion Matrix

---

## Results

- **Best Validation Accuracy:** **86.72%**
- **Test Accuracy:** **85.66%**

The GRU substantially improved upon the vanilla Recurrent Neural Network while achieving performance comparable to the LSTM using a simpler gated architecture.

---

## Key Findings

- The GRU achieved competitive performance while using a simpler recurrent architecture than the LSTM.
- Test accuracy improved by approximately **4.9 percentage points** over the SimpleRNN baseline.
- Classification performance remained balanced across both sentiment classes.
- The LSTM remained the strongest-performing model on this dataset, indicating that its dedicated memory cell provided an advantage for modelling longer contextual dependencies.

---

## Conclusion

The GRU successfully demonstrated that a simplified gated recurrent architecture can achieve strong sentiment classification performance while reducing architectural complexity. Although it did not surpass the LSTM on the IMDb dataset, it significantly outperformed the vanilla Recurrent Neural Network and highlighted the trade-off between computational simplicity and predictive performance.