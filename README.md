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


## Results & Analysis

The implemented prediction methods (Monte Carlo, TD(0), n-step TD, and TD(λ)) were evaluated under three policies: random, custom, and optimal-like.

### Random Policy

The random policy produced strongly negative values, which is expected. because the random agent usually wanders for many steps before reaching the terminal state, accumulating multiple −0.4 penalties and resulting in a highly negative total return. This behavior confirms that the reward structure and environment dynamics are implemented correctly.

### Optimal-like Policy

The optimal-like policy yielded value estimates that closely match the theoretical shortest‑path returns (e.g., −1.8, −1.4, −1.0, …, +1).  
This indicates that:

* State transitions are correct,
* The terminal state is handled properly,
* The step penalty and terminal reward are propagated as expected.

Across this policy, all algorithms (MC, TD(0), TD(λ)) converged to very similar value functions, which is consistent with theory in small tabular environments.

### Custom Policy

* Under the custom policy, meaningful values were obtained only for states that were actually visited.  
* Several states retained a value of 0 because they were never encountered under this policy.  
* This is the correct behavior for both Monte Carlo and TD methods, as they only update states that appear in sampled trajectories.

### Overall Behavior

In general, TD-based methods converged faster due to bootstrapping, while Monte Carlo required more episodes to stabilize. However, all prediction algorithms produced consistent and stable value estimates. Overall, the results align well with theoretical expectations for reinforcement learning in a small stochastic Gridworld environment.

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
