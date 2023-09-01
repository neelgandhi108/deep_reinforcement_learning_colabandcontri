
## Project Objective

This project focuses on developing multi-agent reinforcement learning agents to play tennis collaboratively. In this environment, two agents control rackets to bounce a ball over a net. Each time an agent successfully hits the ball over the net, it receives a reward of +0.1. Conversely, if the ball hits the ground or goes out of bounds, a penalty of -0.01 is incurred. The primary goal of each agent is to maintain the ball in play, promoting collaborative and cooperative behavior.

The task is episodic, and the aim is for the agents to achieve an average score of +0.5 over 100 consecutive episodes, taking the maximum score over both agents into account.

## Environment Overview

The environment is built on the Unity ML-Agents framework, which enables training intelligent agents through various machine learning techniques such as reinforcement learning, imitation learning, and neuroevolution. In this specific tennis environment, two agents interact with a ball and a net. Each agent receives a local observation, and the goal is to hit the ball over the net while keeping it within bounds.

-   **Set-up**: A two-player game with agents controlling rackets to bounce the ball over a net.
-   **Goal**: Agents aim to bounce the ball between each other without letting it drop or go out of bounds.
-   **Agent Reward Function**:
    -   +0.1 reward for hitting the ball over the net.
    -   -0.1 penalty if the ball hits the ground or goes out of bounds.
-   **Observation Space**: 8 variables capturing ball and racket position and velocity.
-   **Action Space**: 2 continuous actions corresponding to movement toward/away from the net and jumping.
-   **Training Approach**: Decentralized training with centralized execution, allowing extra information during training without using it during testing.

## Agent Implementation

To tackle this collaborative tennis challenge, a multi-agent reinforcement learning algorithm called **Multi-Agent Deep Deterministic Policy Gradient (MADDPG)** is employed.

### Deep Deterministic Policy Gradient (DDPG) Background

MADDPG is based on the DDPG algorithm, which involves learning a Q-function and a policy concurrently. It leverages off-policy data and the Bellman equation to learn the Q-function, which in turn is used to learn the policy.

### Multi-Agent Deep Deterministic Policy Gradient (MADDPG)

MADDPG extends DDPG to multi-agent settings. The approach involves centralizing the training process while maintaining decentralized execution. This allows the policy to utilize additional information during training without depending on it during testing.

The algorithm employs three key techniques:

1.  **Clipped Double-Q Learning**: MADDPG uses two Q-functions and takes the minimum Q-value as the target in the Bellman error loss functions. This helps mitigate the overestimation of Q-values.
    
2.  **Delayed Policy Updates**: Unlike DDPG, MADDPG updates the policy less frequently than the Q-function. Specifically, the policy is updated once for every two Q-function updates.
    
3.  **Target Policy Smoothing**: MADDPG introduces noise to the target action, making it more challenging for the policy to exploit Q-function errors.
    

### Code Implementation

The code is developed in Python 3.6 using the PyTorch 0.4.0 framework. The key components of the implementation include:

-   `model.py`: Definition of the Actor and Critic classes, each comprising local and target neural networks.
    
-   `maddpg_agent.py`: Implementation of the MADDPG algorithm.
    
    -   Creation of DDPG agents with instanced neural networks.
    -   Definition of `step()` and `act()` methods for the agents.
    -   Implementation of the `maddpg_learn()` method for learning.
-   `ddpg_agent.py`: Implementation of the DDPG agent and the Replay Buffer memory.
    
-   `memory.py`: Implementation of the Replay Buffer memory used for experience replay.
    
-   `utils.py`: Helper functions for encoding and decoding states and actions in the Replay Buffer.
    
-   `hyperparameters.py`: Definition of hyperparameters used in the training process.
    
-   `TennisProject.ipynb`: A Jupyter notebook that facilitates the instantiation and training of the MADDPG agents, along with the plotting of results.
    

## MADDPG Parameters and Results

The implementation uses various hyperparameters and architectural choices for the neural networks. Some of the important hyperparameters include the learning rates, network architecture, buffer size, batch size, noise parameters, and more. These parameters have been tuned to achieve the desired level of performance.

Training the agents involves several milestones, with adjustments made to hyperparameters to optimize learning. The key milestones include:

1.  Initial Implementation: Agents started to learn around 3000 episodes, eventually solving the environment in 4287 episodes with an average score of 0.50.
    
2.  Learning Frequency Adjustment: By updating the policy three times consecutively every four episodes and boosting the critic learning rate, the environment was solved in 2989 episodes with an average score of 0.51.
    
3.  Batch Normalization: Incorporating batch normalization further improved learning, leading to the environment being solved in 2487 episodes with an average score of 0.51.
    

## Future Enhancements

Two potential directions for future enhancements are:

1.  **Twin Delayed DDPG (TD3)**: Implementing the TD3 algorithm could lead to better performance. TD3 addresses overestimation issues by introducing dual Q-functions and delayed policy updates.
    
2.  **Prioritized Experience Replay**: Incorporating prioritized experience replay may improve learning efficiency by replaying important experiences more frequently.
    

By exploring these avenues, the agents' performance and robustness could be further improved, pushing the boundaries of collaborative multi-agent reinforcement learning in the tennis environment.