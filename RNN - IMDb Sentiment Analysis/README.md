# Recurrent Neural Network (RNN) - IMDb Sentiment Analysis

## Overview
This project implements a vanilla Recurrent Neural Network (SimpleRNN) for binary sentiment classification on the IMDb movie review dataset. The objective is to establish a baseline sequence model and highlight the strengths and limitations of traditional RNNs before progressing to LSTM and GRU architectures.

## Dataset
IMDb Movie Review Dataset

## Dataset Source
TensorFlow/Keras (`tensorflow.keras.datasets.imdb`)

## Notebook Structure
1. Data Loading
2. Exploration
3. Preprocessing
4. Model Development
5. Training
6. Evaluation
7. Error Analysis
8. Discussion
9. Key Findings
10. Conclusion

## Repository Contents
- RNN_IMDB_Sentiment_Analysis.ipynb
- README.md
- requirements.txt

## Model Architecture / Methodology
- Embedding Layer
- SimpleRNN (64 units)
- Dense (32, ReLU)
- Dense (1, Sigmoid)
- Adam Optimizer
- EarlyStopping (validation loss)

## Technologies Used
- Python
- TensorFlow
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook

## Evaluation Metrics
- Binary Crossentropy Loss
- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

## Results
- Test Accuracy: **80.79%**
- Weighted F1-score: **0.8077**

The model learned meaningful sequential patterns while exhibiting increasing overfitting after the initial epochs.

## Key Findings
The SimpleRNN achieved balanced classification performance across both sentiment classes. Misclassified reviews were typically longer or contained mixed sentiment, illustrating the limited ability of vanilla RNNs to preserve long-range contextual information.

## Conclusion
This project establishes a baseline for sequence modelling using recurrent neural networks. While the model effectively captures short-term dependencies, its performance suggests that gated architectures such as LSTMs are better suited for learning longer contextual relationships.
