---
layout: post
title:  "Reinforcement Learning -- DQN"
date:   2020-10-27 02:41:36 +0530
categories: reading
type: blog
---
[paper][paper] tittle: human-level control through deep reinforcement learning.

<h3>classification</h3> model-free, off-policy, value-based, continuous state, discrete action space.

The goal is to find one optimal policy that maximizes cumulative future reward: $Q(s,a)=max_{\pi}E[r_t + \gamma r_{t+1} + \gamma^2 r_{t+2} + ...]$. In this paper, a deep Neural Network was used to approximate the optimal action-value function.

The q-learning update uses the following loss function: $L(\theta)=E_{(s,a,r,s') \in U(D)}[(r + \gamma max_{a'}Q(s',a'; \theta') - Q(s,a; \theta))^2]$. 

<h3>Experiment environment</h3> Atari 2600 platform.

<h3>Metrics</h3> rewards from game.

[paper]:http://web.stanford.edu/class/psych209/Readings/MnihEtAlHassibis15NatureControlDeepRL.pdf