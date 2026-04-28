# Reinforcement Learning in a Stochastic 5×5 Gridworld: A Study of Prediction and Control Methods

## Abstract
This project explores reinforcement learning techniques for both prediction (policy evaluation) and control (policy improvement) in a stochastic 5×5 Gridworld environment. The goal is to understand how different algorithms perform in estimating value functions and deriving optimal policies under stochastic transitions and obstacles.

## Project Overview
The Gridworld environment serves as a classic benchmark for reinforcement learning.
In this project, I implemented and compared several Monte Carlo and Temporal-Difference (TD) based algorithms for both prediction and control tasks.
Each method was evaluated in terms of accuracy, stability, and convergence behavior.

## Environment Description
The environment is a custom 5×5 Gridworld with 25 discrete states indexed from 0 to 24 (row-major order).
The agent starts from state 0 and aims to reach the terminal state 24.

###  State and Action Space
**Number of states**: 25
**Start state**: 0
**Terminal state**: 24
**Number of actions**: 4
  * 0 → Up
  * 1 → Right
  * 2 → Down
  * 3 → Left

### Obstacles
The following states are blocked and cannot be entered:
`{6,8,15,17}`

If an action would move the agent into an obstacle, the agent remains in its current state.

###  Boundary Conditions: 

The agent cannot move outside the grid:

1. Moving up from top row states `{0,1,2,3,4}` results in no movement.

2. Moving down from bottom row states `{20,21,22,23}` results in no movement.

3. Moving right from `{4,9,14,19,24}` results in no movement.

4. Moving left from `{0,5,10,15,20}` results in no movement.

In all invalid transitions (boundary or obstacle), the state remains unchanged.

### Reward Structure: 

* Reaching the terminal state (24):

` r=+1.0 `

Episode terminates (done = True)

* Any other transition:

` r=−0.4 `

Episode continues (done = False)




## Implemented Algorithms
### Prediction Methods:

* Monte Carlo (first-visit and every-visit)
* TD(0)
* n-step Temporal Difference
* TD(λ)

### Control Methods:

* Monte Carlo Control (ε‑greedy)
* SARSA
* Q‑Learning

** Each algorithm was applied to learn value functions and optimal policies under ε‑greedy exploration.


## Policies Used for Prediction
In the prediction experiments, value estimation was performed under three different fixed policies, allowing a comparison of how Monte Carlo, TD(0), n‑step TD, and TD(λ) behave under varying policy structures:

### Optimal-like Policy (Target Policy)

A hand‑crafted policy designed to move the agent efficiently toward the terminal state.

This policy serves as a near-optimal baseline for evaluating value estimation accuracy.

## How to Run
```
# Clone the repository
git clone https://github.com/YourUsername/Gridworld-RL.git
cd Gridworld-RL

# Install dependencies
pip install -r requirements.txt

# Run experiments
python main.py
```
Modify configuration parameters in config.py to test different learning rates, ε-values, or episode lengths.

This negative step reward encourages the agent to find the shortest path to the goal.
