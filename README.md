
#   Reinforcement Learning for Collaborative Game Play

This repository showcases the implementation and outcomes of Project 3 in Udacity's Deep Reinforcement Learning Nanodegree: Collaboration and Competition.

GitHub Repository: [https://github.com/neelgandhi108/deep_reinforcement_learning_colabandcontri](https://github.com/neelgandhi108/deep_reinforcement_learning_colabandcontri)

## Project Objective

![Tennis Agents](https://user-images.githubusercontent.com/10624937/42135623-e770e354-7d12-11e8-998d-29fc74429ca2.gif)


The project revolves around a scenario where two agents control rackets aiming to keep a ball in play by bouncing it over a net. Successful bounces earn a reward of +0.1, while allowing the ball to hit the ground or sending it out of bounds incurs a penalty of -0.01. The primary objective for each agent is to sustain the ball's playtime.

The task is episodic, and the environment is considered solved when the average score over 100 consecutive episodes, after taking the maximum score of both agents, exceeds +0.5.

## Employing Deep Reinforcement Learning

Reinforcement learning involves algorithms that learn to achieve specific goals or maximize certain metrics over multiple steps. In this project, we deploy a variant of the DDPG algorithm, known as Multi-Agent Deep Deterministic Policy Gradient (MADDPG). This algorithm is outlined in the paper [Multi-Agent Actor-Critic for Mixed Cooperative-Competitive Environments](https://arxiv.org/abs/1706.02275).

## Environment Details

The environment is built upon Unity's ML-agents framework, designed to facilitate training of intelligent agents using reinforcement learning. The environment provided by Udacity for this project closely resembles the [Tennis](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#tennis) environment showcased in Unity's ML-Agents GitHub repository.

The observation space is comprised of 8 variables capturing the positions and velocities of the ball and rackets. Each agent has its own local observation, and the available actions include movement toward or away from the net and jumping.

## Solving the Environment

The environment is deemed successfully solved when the average score, considering the maximum score across both agents, is +0.5 or greater over a span of 100 episodes.

### Download Environment

Download the appropriate environment for your operating system using the links below:

-   Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux.zip)
-   Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis.app.zip)
-   Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86.zip)
-   Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86_64.zip)

After downloading, unzip the environment archive in the 'project's environment' directory and adjust the path to the UnityEnvironment in the code.

### Train the Agent

Execute the provided notebook within the Udacity Online Workspace for "Project #3 Collaboration and Competition." Alternatively, set up a local environment, make the necessary adjustments for the UnityEnvironment path in the code, and run the notebook.

Please note that manual interaction with the environment and watching the trained agent play are not supported in the Udacity Online Workspace.

### Miscellaneous: Configuration Used

The agent in this project was trained on a Linux GPU server running Docker containers via Nvidia Docker 2. Jupyter Lab notebooks were accessed remotely through a web interface or SSH. However, due to limitations in providing both GPU access and a display for the agent, the headless/no visualization version of the Unity environment was used for training. For further details, consult the [Unity documentation](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Using-Docker.md).
