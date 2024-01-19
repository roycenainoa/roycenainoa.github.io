---
layout: project
type: project
image: img/micromouse/micromouse-square.jpg
title: "Goats and Tigers"
date: 2023
published: true
labels:
  - Machine Learning
  - Reinforcement Learning
  - Python
summary: "This is an undergraduate project formerly known as Reinforcement Learning for Inferring Strageies that develops a reinforcement learning technique that trains a machine to play a board game known as Huligutta (Goats & Tigers)."
---

The objective of the RL for Inferring Strategies project is to develop a reinforcement learning technique to train a machine to play a strategy game, similar to how a human would play. The technique incorporates machine learning, neural networks, large datasets, and Python programming. The game that is being focused on is called Huligutta (Tigers and Goats) and is popular throughout South Asia. It has two asymmetrical players where either can play as a Tiger or Goat. The win condition as a Tiger is to eat as many Goats, or as a Goat to cause a stalemate. Strategic positional play usually beats tactical greedy algorithms in this game, similarly to Chess or Go. However, analyzing the game from a machine learning viewpoint has not been done before. Furthermore, the game has the advantage of a smaller state space than Chess or Go, making it both novel and challenging. Playing as the Goat is harder than the Tiger. In this semester, we iteratively derive a value function that’s overparameterized that will culminate in a policy (strategy) to beat a greedy Tiger strategy. We initialize a neural network via sequential method to mimic (on a limited number of states) a naive estimation of the value function. The generalization of the value function to other states implicit in the neural network is used in a strategy (policy) to play games as the Goat player, in an automated manner against a greedy Tiger strategy. The success rate of this policy on batches of games is used as the loss to train the neural network via gradient descent.
