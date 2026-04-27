# Reinforcement Learning in a Stochastic 5×5 Gridworld: A Study of Prediction and Control Methods

## Abstract
This project explores reinforcement learning techniques for both prediction (policy evaluation) and control (policy improvement) in a stochastic 5×5 Gridworld environment. The goal is to understand how different algorithms perform in estimating value functions and deriving optimal policies under stochastic transitions and obstacles.

## Project Overview
The Gridworld environment serves as a classic benchmark for reinforcement learning.
In this project, I implemented and compared several Monte Carlo and Temporal-Difference (TD) based algorithms for both prediction and control tasks.
Each method was evaluated in terms of accuracy, stability, and convergence behavior.

## Environment Description
* Size: 5×5 Gridworld
* Terminal State: cell 24
* Obstacles: cells 6, 8, 15, and 17
* Transition Dynamics: stochastic — each agent’s action may result in a random neighboring move with certain probability
* Reward Function: includes penalties for invalid or obstacle states, positive reward for reaching the terminal state
