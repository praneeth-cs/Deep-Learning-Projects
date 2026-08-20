# Bidirectional Encoder Representations from Transformers (BERT) - TREC-6 Question Classification

## Overview

This project fine-tunes the pretrained `bert_base_en_uncased` model for six-class question classification using the TREC Question Classification dataset. The objective is to predict the expected answer type of a question as abbreviation, entity, description, human, location, or numeric.

The experiment demonstrates transfer learning with a pretrained Transformer using TensorFlow/Keras and KerasHub.

## Dataset

**TREC Question Classification Dataset**

- 5,452 training questions
- 500 test questions
- 6 coarse-grained answer types
- Classes:
  - ABBR
  - ENTY
  - DESC
  - HUM
  - LOC
  - NUM

The original training set was divided into training and validation sets using stratified sampling.

The executed experiment used:

- **4,906 training questions**
- **546 validation questions**
- **500 test questions**

## Dataset Source

TensorFlow Datasets - TREC

https://www.tensorflow.org/datasets/catalog/trec

The dataset is downloaded automatically when the notebook is executed and is not included in this repository.

## Notebook Structure

1. Import Required Libraries
2. Load the TREC-6 Dataset
3. Explore the Dataset
4. Create Validation Split
5. Build the Pretrained BERT Classifier
6. Prepare Training and Evaluation Data
7. Fine-Tune BERT
8. Training Curves
9. Evaluate the Model
10. Classification Report
11. Confusion Matrix
12. Error Analysis
13. Key Findings
14. Conclusion

## Repository Contents

BERT - TREC-6 Question Classification/
├── BERT_TREC_6_Question_Classification.ipynb
├── README.md
└── requirements.txt

## Model Architecture / Methodology

The project uses a pretrained `bert_base_en_uncased` model provided through KerasHub.

The fine-tuning workflow is:

Raw Questions
↓
KerasHub BERT Preprocessing
↓
Pretrained BERT Encoder
↓
Six-Class Classification Head
↓
Softmax Classification

Training configuration:

- Pretrained model: `bert_base_en_uncased`
- Number of output classes: 6
- Maximum sequence length: 128 tokens
- Optimizer: Adam
- Learning rate: 2e-5
- Batch size: 16
- Epochs: 5 maximum
- EarlyStopping patience: 2
- Best model selected using validation accuracy
- Restore best weights enabled
- Sparse categorical crossentropy loss

## Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- Scikit-learn
- TensorFlow
- TensorFlow Datasets
- Keras
- KerasHub
- Jupyter Notebook

## Evaluation Metrics

- Accuracy
- Precision
- Recall
- Macro F1-Score
- Weighted F1-Score
- Classification Report
- Confusion Matrix
- Error Analysis

## Results

- **Best Validation Accuracy:** **94.51%**
- **Best Epoch:** **4**
- **Validation Loss at Best Epoch:** **0.1983**
- **Test Accuracy:** **96.80%**
- **Test Loss:** **0.1425**
- **Macro Precision:** **0.9740**
- **Macro Recall:** **0.9544**
- **Macro F1-Score:** **0.9633**
- **Weighted F1-Score:** **0.9677**

The model correctly classified **484 of the 500 test questions**, resulting in 16 misclassifications.

## Key Findings

- BERT achieved **96.80% test accuracy** on the TREC-6 question classification task.
- The strongest validation performance occurred at **Epoch 4**, after which validation accuracy declined while training accuracy continued to increase.
- The **0.9633 macro F1-score** indicates strong and consistent performance across the six answer-type categories.
- The small difference between macro F1 and weighted F1 indicates that the overall result was not dominated by the larger classes.
- The remaining errors were concentrated in questions with overlapping or ambiguous semantic cues rather than a broad failure to identify question types.

## Conclusion

The pretrained BERT model successfully learned to classify TREC-6 questions into their expected answer types with high accuracy. The final model achieved **96.80% test accuracy** and a **0.9633 macro F1-score**, demonstrating strong classification performance across all six categories.

The training curves also showed mild overfitting after the fourth epoch, which was controlled by selecting the model using validation accuracy and restoring the best-performing weights. The remaining classification errors illustrate the difficulty of distinguishing questions whose wording supports more than one plausible answer type.

Overall, the experiment demonstrates the effectiveness of pretrained Transformer representations for downstream natural language classification using a relatively small labelled dataset.