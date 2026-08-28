# RoBERTa - BANKING77 Intent Classification

## Overview

This project fine-tunes the pretrained `roberta-base` model for fine-grained intent classification on the BANKING77 dataset.

The task is to classify natural-language banking customer-service queries into one of 77 predefined intents covering areas such as cards, cash withdrawals, transfers, payments, account management, identity verification, and top-ups.

The experiment uses a dedicated training, validation, and test workflow, validation-based checkpoint selection, and detailed post-training analysis.

## Dataset

BANKING77 is a fine-grained single-domain intent classification dataset containing 13,083 banking customer-service queries across 77 intents.

Dataset splits:

- 10,003 training examples
- 3,080 test examples
- 77 intent classes

The official test split is kept separate from model selection. A stratified validation split is created from the training data for checkpoint selection.

## Dataset Source

PolyAI BANKING77

https://huggingface.co/datasets/PolyAI/banking77

The dataset is loaded from the public source data and is not included directly in the repository.

## Project Objective

The objective is to build a pretrained Transformer classifier that can map a banking customer query to the most appropriate operational intent.

Example:

"I do not recognize this cash withdrawal"
→
cash_withdrawal_not_recognised

Because BANKING77 contains 77 closely related intents, the task requires fine-grained semantic classification rather than broad topic detection.

## Notebook Structure

1. Import Required Libraries
2. Load the BANKING77 Dataset
3. Create Stratified Train and Validation Splits
4. Explore the Dataset
5. Load the RoBERTa Tokenizer
6. Tokenize the Dataset
7. Build the RoBERTa Intent Classifier
8. Define Evaluation Metrics
9. Configure Fine-Tuning
10. Fine-Tune RoBERTa
11. Training Curves
12. Final Test Evaluation
13. Classification Report and Confusion Matrix
14. Per-Intent Performance Analysis
15. Confidence Analysis
16. Representative Error Analysis
17. Interactive Intent Prediction
18. Key Findings
19. Conclusion

## Model Architecture

The model uses pretrained `roberta-base` followed by a sequence-classification head with 77 output classes.

Banking Query
↓
RoBERTa Tokenizer
↓
Pretrained RoBERTa Encoder
↓
Sequence Classification Head
↓
77 Intent Classes

The RoBERTa backbone provides pretrained language representations, while the final classification head is fine-tuned for the BANKING77 task.

## Fine-Tuning Configuration

- Model: `roberta-base`
- Maximum sequence length: 128 tokens
- Training batch size: 32
- Evaluation batch size: 32
- Learning rate: 2e-5
- Maximum epochs: 30
- Optimizer: AdamW
- Weight decay: 0.01
- Validation metric for checkpoint selection: Macro F1
- Early stopping patience: 2 epochs
- Mixed precision: enabled when CUDA is available
- Random seed: 42
- Best model weights restored automatically

## Evaluation Metrics

The model is evaluated using:

- Accuracy
- Macro Precision
- Macro Recall
- Macro F1
- Weighted F1
- Per-intent Precision, Recall, and F1
- Confusion Matrix
- Prediction Confidence
- Representative Error Analysis

Macro F1 is used for checkpoint selection so that each of the 77 intents contributes equally to the model-selection decision.

## Results

The executed experiment achieved:

- Test Accuracy: 85.65%
- Test Macro Precision: 86.71%
- Test Macro Recall: 85.65%
- Test Macro F1: 85.62%
- Test Weighted F1: 85.62%
- Test Loss: 0.5967

Best validation performance:

- Best Epoch: 14
- Best Validation Accuracy: 86.61%
- Best Validation Macro F1: 86.88%

The final test set contained 3,080 examples, with 442 classified incorrectly.

## Error Analysis

The remaining errors are concentrated primarily among semantically related intents.

Examples include confusion between:

- `card_arrival`
- `card_delivery_estimate`
- `order_physical_card`
- other closely related card-management intents

Similar ambiguity also appears among transfer, payment, and cash-withdrawal intents.

These errors are more difficult because multiple banking intents can share similar vocabulary while representing different customer-service actions.

## Confidence Analysis

The model was substantially more confident when it was correct than when it was incorrect.

Mean prediction confidence:

- Correct predictions: 0.9326
- Incorrect predictions: 0.7010

This indicates that confidence provides a useful signal for identifying more difficult or ambiguous queries.

## Practical Relevance

Intent classification can serve as an initial routing layer for customer-support systems.

A banking query can first be classified into an intent and then routed to the appropriate workflow, retrieval system, automated response system, or support process.

Customer Query
↓
Intent Classification
↓
Banking Intent
↓
Relevant Support Workflow

## Limitations

BANKING77 is a benchmark dataset and does not capture every type of language that may occur in a live banking environment.

Real-world systems may encounter:

- previously unseen intents
- new terminology
- ambiguous queries
- longer conversations
- multilingual requests
- domain changes over time

Therefore, benchmark performance should not be interpreted as guaranteed performance on live customer-service traffic.

## Conclusion

The fine-tuned RoBERTa model achieved 85.65% test accuracy and 0.8562 macro F1 on the BANKING77 benchmark.

The results demonstrate that pretrained Transformer representations can distinguish a large number of fine-grained banking intents effectively. The remaining errors are concentrated mainly in semantically similar categories, highlighting the importance of per-intent evaluation, confusion analysis, and confidence evaluation for fine-grained intent classification.