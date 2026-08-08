# Long Short-Term Memory (LSTM) - IMDb Sentiment Analysis

## Overview

This project applies a Long Short-Term Memory (LSTM) network to perform binary sentiment classification on the IMDb movie review dataset. The objective is to demonstrate how gated recurrent architectures improve upon traditional Recurrent Neural Networks by retaining long-term contextual information throughout a sequence. The notebook covers data preprocessing, model development, training, evaluation and prediction analysis using TensorFlow/Keras.

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
6. Build LSTM Model
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
LSTM - IMDb Sentiment Analysis/
├── LSTM_IMDB_Sentiment_Analysis.ipynb
├── README.md
└── requirements.txt
```

---

## Model Architecture / Methodology

- Embedding Layer
- Long Short-Term Memory (LSTM)
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

- **Best Validation Accuracy:** **87.54%**
- **Test Accuracy:** **87.08%**

Compared with the previous SimpleRNN implementation, the LSTM produced a substantial improvement in both validation and test performance while exhibiting stronger generalization.

---

## Key Findings

- LSTM improved test accuracy by approximately **6.3%** compared with the SimpleRNN baseline.
- Balanced precision and recall indicate consistent performance across both sentiment classes.
- The gated memory mechanism enabled better retention of long-range contextual information.
- Remaining errors were primarily associated with ambiguous or context-dependent reviews rather than simple long-sequence limitations.

---

## Conclusion

The LSTM architecture demonstrated a clear advantage over the vanilla Recurrent Neural Network on the IMDb sentiment classification task. By preserving long-term dependencies through gated memory cells, the model achieved higher predictive performance and stronger generalization, establishing a solid foundation for comparison with the upcoming GRU implementation.