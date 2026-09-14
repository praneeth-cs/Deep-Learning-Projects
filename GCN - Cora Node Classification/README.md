# GCN - Cora Node Classification

A deep learning project that implements a Graph Convolutional Network (GCN) for semi-supervised node classification on the Cora citation network.

## Overview

This project demonstrates an end-to-end Graph Neural Network workflow using a two-layer Graph Convolutional Network implemented in PyTorch.

Each node in the Cora network represents a research paper, while citation relationships between papers form the graph edges. Each paper is also represented by a vector of word-based features. The GCN combines these node features with information from neighboring papers to predict the research category of each paper.

The notebook covers dataset loading, graph construction, feature preprocessing, adjacency normalization, GCN architecture design, semi-supervised training, model evaluation, confusion analysis, and visualization of learned node embeddings.

The project uses the standard Cora semi-supervised setup, where only 140 labeled nodes are used to calculate the training loss, while validation and test nodes are held out for model evaluation.

Runtime: Google Colab  
GPU: NVIDIA Tesla T4

## Dataset

**Cora Citation Network**

The Cora dataset contains:

- **2,708** research papers
- **1,433** word-based features per paper
- **5,429** citation relationships
- **7** research categories

Each research paper is represented as a graph node, and citation relationships form the edges connecting the nodes.

### Target Classes

The seven research categories are:

- Case-Based
- Genetic Algorithms
- Neural Networks
- Probabilistic Methods
- Reinforcement Learning
- Rule Learning
- Theory

### Training Setup

The project uses the standard semi-supervised Cora evaluation protocol:

- **140** labeled nodes for training
- **500** nodes for validation
- **1,000** nodes for testing

The remaining nodes remain part of the graph and can contribute structural information during message passing, but their labels are not used when calculating the training loss.

## Dataset Source

Cora Citation Network

https://linqs-data.soe.ucsc.edu/public/lbc/cora.tgz

The dataset is downloaded automatically when the notebook is executed and is not included in this repository.

## Notebook Structure

The notebook follows the workflow below:

1. **Import Required Libraries**
2. **Configure Reproducibility and Training**
3. **Download and Load the Cora Dataset**
4. **Explore the Dataset**
5. **Prepare Node Features and Labels**
6. **Build the Citation Graph**
7. **Create Train, Validation, and Test Masks**
8. **Move Data to the Training Device**
9. **Build the Graph Convolutional Network**
10. **Inspect Model Parameters**
11. **Train the GCN**
12. **Plot Training Curves**
13. **Evaluate the Model on the Test Set**
14. **Classification Report**
15. **Confusion Matrix**
16. **Visualize Learned Node Embeddings**
17. **Graph Structure and Degree Distribution**
18. **Key Findings**
19. **Conclusion**

## Repository Contents

GCN - Cora Node Classification/
├── GCN_Cora_Node_Classification.ipynb
├── README.md
└── requirements.txt

## Model Architecture

The GCN consists of:

- Graph Convolution layer with 16 hidden units
- ReLU activation
- Dropout layer with a rate of 0.50
- Second Graph Convolution layer
- Output layer with 7 class predictions

The graph convolution layers combine transformed node features with information propagated through the normalized citation graph.

The model is trained using:

- Adam optimizer
- Cross-entropy loss
- Weight decay
- Validation-loss monitoring
- Early stopping
- Best-validation-checkpoint restoration

## Methodology

The overall workflow is:

**Node Features → Citation Graph → Adjacency Normalization → Graph Convolution → Learned Node Representations → Classification**

The citation graph is treated as an undirected graph for message passing, and self-loops are added so that each node can retain information from its own feature representation.

The adjacency matrix is symmetrically normalized before being used by the graph convolution layers.

During training, only the 140 labeled training nodes contribute to the supervised loss. However, the GCN processes the entire graph, allowing information from neighboring papers to influence node representations.

## Training Configuration

- Hidden dimension: **16**
- Dropout: **0.50**
- Learning rate: **0.01**
- Weight decay: **0.0005**
- Maximum epochs: **200**
- Early stopping patience: **30**
- Random seed: **42**
- Training device: **Google Colab NVIDIA Tesla T4**

## Technologies Used

- Python
- PyTorch
- NumPy
- Pandas
- Matplotlib
- NetworkX
- Scikit-learn
- Jupyter Notebook
- Google Colab

## Evaluation Metrics

The model is evaluated using:

- Test Loss
- Accuracy
- Macro Precision
- Macro Recall
- Macro F1 Score
- Weighted F1 Score
- Classification Report
- Confusion Matrix

Additional analysis includes:

- Training and validation curves
- Class-specific prediction errors
- Learned node embedding visualization
- Node degree distribution

## Results

The final GCN achieved:

- **Test Loss:** 0.8057
- **Test Accuracy:** 78.70%
- **Macro Precision:** 75.99%
- **Macro Recall:** 79.93%
- **Macro F1:** 77.51%
- **Weighted F1:** 78.77%

The best validation loss was **0.8699** at **epoch 200**, with a validation accuracy of **75.40%**.

Training accuracy reached approximately **94.29%**, while test accuracy was **78.70%**. This difference shows that the model learned the labeled training nodes effectively but still faced a generalization gap when predicting unseen nodes.

Class-level performance varied across the seven research categories. **Genetic Algorithms** achieved the strongest F1 score at **92.40%**, while **Theory** was the most difficult category with an F1 score of **68.80%**.

## Key Findings

The GCN successfully combined paper features and citation relationships to perform semi-supervised node classification.

The model achieved **78.70% test accuracy** despite using only **140 labeled nodes** to calculate the training loss.

The results demonstrate the value of graph structure in addition to conventional feature information. Neighboring papers can provide useful contextual information that helps the model distinguish between research categories.

The class-level results also show that some research categories are more difficult to distinguish than others, with the strongest performance occurring on Genetic Algorithms and the weakest performance occurring on Theory.

## Conclusion

This project demonstrates how Graph Convolutional Networks can learn from both node features and relationships between connected data points.

Using the Cora citation network, the GCN achieved **78.70% test accuracy** and a **77.51% macro F1 score** in a semi-supervised setting with only 140 labeled training nodes.

The project provides a practical introduction to Graph Neural Networks, graph convolution, message passing, adjacency normalization, node embeddings, and semi-supervised node classification.