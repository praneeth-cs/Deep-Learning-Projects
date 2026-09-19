# DQN - CartPole Reinforcement Learning

A deep learning project that implements a Deep Q-Network (DQN) in PyTorch to learn how to balance a pole on a moving cart using reinforcement learning.

## Overview

This project demonstrates an end-to-end reinforcement learning workflow using a Deep Q-Network.

Unlike supervised learning, the agent is not given labeled examples or a predefined correct action. Instead, it interacts with the environment, observes the current state, selects an action, receives a reward, and uses that experience to improve its estimate of future rewards.

The notebook covers environment setup, reinforcement learning concepts, DQN architecture, experience replay, epsilon-greedy exploration, target networks, Bellman-based optimization, training progress, evaluation, and inspection of learned Q-values.

The objective is to learn a policy that consistently keeps the pole balanced for the maximum duration allowed by the CartPole environment.

Runtime: Google Colab  
GPU: NVIDIA Tesla T4

## Environment

**CartPole-v1**

CartPole is a classic reinforcement learning environment in which the agent controls the movement of a cart while attempting to keep a pole upright.

The environment provides:

- **4 state variables**
- **2 possible actions**
- A reward of **1 for each time step** that the pole remains balanced
- A maximum episode length of **500 steps**

The four state variables describe:

- Cart position
- Cart velocity
- Pole angle
- Pole angular velocity

The two actions are:

- **Action 0:** Move the cart left
- **Action 1:** Move the cart right

## Environment Source

Gymnasium — CartPole

https://gymnasium.farama.org/

The environment is created automatically when the notebook is executed and does not require a separate dataset download.

## Notebook Structure

The notebook follows the workflow below:

1. **Import Required Libraries**
2. **Configure Reproducibility and Training**
3. **Create the CartPole Environment**
4. **Understand the Reinforcement Learning Setup**
5. **Build the DQN**
6. **Inspect the Network Parameters**
7. **Create the Experience Replay Buffer**
8. **Define Exploration and Action Selection**
9. **Define the DQN Optimization Step**
10. **Train the DQN Agent**
11. **Plot Training Progress**
12. **Evaluate the Trained Agent**
13. **Compare Evaluation Rewards**
14. **Inspect Learned Q-Values**
15. **Key Findings**
16. **Conclusion**

## Repository Contents

DQN - CartPole Reinforcement Learning/
├── DQN_CartPole_Reinforcement_Learning.ipynb
├── README.md
└── requirements.txt

## Model Architecture

The DQN consists of:

- Input layer with 4 state features
- Dense layer with 128 neurons and ReLU activation
- Dense layer with 128 neurons and ReLU activation
- Output layer with 2 Q-values

The two output values represent the estimated long-term value of the two available actions.

The project uses two copies of the network:

- **Policy network** — updated during training
- **Target network** — provides stable Q-value targets

## DQN Methodology

The agent follows the cycle:

**State → Action → Reward → Next State → Q-Value Update**

The project uses:

- Deep Q-Network
- Experience replay
- Target network
- Epsilon-greedy exploration
- Bellman targets
- Smooth L1 loss
- Adam optimizer
- Gradient clipping

Experience replay stores previous state-action transitions and randomly samples batches for training.

The target network is periodically synchronized with the policy network to provide more stable learning targets.

Epsilon-greedy exploration allows the agent to initially explore different actions and gradually transition toward using the action with the highest predicted Q-value.

## Training Configuration

- Environment: **CartPole-v1**
- Training episodes: **600**
- Maximum steps per episode: **500**
- State dimension: **4**
- Action dimension: **2**
- Hidden layers: **128, 128**
- Discount factor (Gamma): **0.99**
- Learning rate: **0.0005**
- Batch size: **64**
- Replay buffer capacity: **50,000**
- Minimum replay size: **1,000**
- Initial epsilon: **1.00**
- Final epsilon: **0.05**
- Epsilon decay steps: **10,000**
- Target network update frequency: **500 steps**
- Random seed: **42**
- Training device: **Google Colab NVIDIA Tesla T4**

## Technologies Used

- Python
- PyTorch
- NumPy
- Pandas
- Matplotlib
- Gymnasium
- Jupyter Notebook
- Google Colab

## Evaluation

The model is evaluated using:

- Episode reward
- 100-episode moving-average reward
- Mean evaluation reward
- Standard deviation of evaluation rewards
- Best evaluation reward
- Minimum evaluation reward

The notebook also visualizes:

- Training reward progression
- DQN training loss
- Epsilon decay
- Evaluation episode rewards
- Learned Q-values

## Results

The DQN was trained for **600 episodes**.

The best 100-episode moving average reached **418.95**, with the highest moving average occurring at the end of training. The exploration rate reached its final value of **0.05**.

During the final evaluation, exploration was disabled and the agent was tested across **20 independent episodes**.

Evaluation results:

- **Mean Reward:** 500.0
- **Standard Deviation:** 0.0
- **Best Reward:** 500.0
- **Minimum Reward:** 500.0

The agent therefore achieved the maximum episode reward in **all 20 evaluation episodes**.

## Key Findings

The DQN progressively learned to balance the pole through repeated interaction with the CartPole environment.

Training rewards increased substantially during the later stages of the run, with multiple episodes reaching the maximum reward of 500.

The final evaluation demonstrated that the learned policy was stable: all 20 evaluation episodes reached 500 reward when exploration was disabled.

The difference between the training moving average and the evaluation result is expected because training retained a small amount of random exploration, while evaluation used a deterministic policy.

## Conclusion

This project demonstrates how a neural network can learn decision-making through reinforcement learning without supervised labels.

By combining a DQN with experience replay, a target network, epsilon-greedy exploration, and Bellman-based updates, the agent learned a policy that consistently balanced the pole for the full 500-step CartPole episode.

The final evaluation achieved a mean reward of **500 across 20 episodes**, demonstrating a successfully learned policy and completing the reinforcement learning component of the project.