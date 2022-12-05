---
layout: post
title:  "Reinforcement Learning -- Dueling DQN"
date:   2020-10-29 02:41:36 +0530
categories: reading
type: blog
---
[paper][paper] tittle: Dueling Network Architectures for Deep Reinforcement Learning.

<h3>classification</h3>: model-free, off-policy, value-based, continuous state, discrete action space.

<h3>Problem</h3>:  In some states, it is of paramount importance to know which action to take, but in many other states the choice of action has no repercussion on what happens. Proposed method has issue of identifiability.

reasones: xxx

problem's results: xxx

<h3>solution</h3>: The proposed network architecture, which we name the dueling architecture, explicitly separates the representation of state values and (state-dependent) action advantages. This dueling network should be understood as a single Q network with two streams that replaces the popular single-stream Q network in existing algorithms. The dueling network automatically produces separate estimates of the state value function and advantage function, without any extra supervision. To address this issue of identifiability, we can force the advantage function estimator to have zero advantage at the chosen action.

<h3>benefits analysis</h3>: the dueling architecture can learn which states are (or are not) valuable, without having to learn the effect of each action for each state. This is particularly useful in states where its actions do not affect the environment in any relevant way. 

Experiment environment: Atari 2600 platform.

Metrics: rewards from games.

[paper]:https://arxiv.org/pdf/1511.06581.pdf