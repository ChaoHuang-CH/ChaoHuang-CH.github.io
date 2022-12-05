---
layout: post
title:  "Reinforcement Learning -- ACER"
date:   2020-11-05 02:41:36 +0530
categories: reading
type: blog
---
[paper][paper] tittle: SAMPLE EFFICIENT ACTOR-CRITIC WITH EXPERIENCE REPLAY.

<h3>classification</h3>: model-free, off-policy, policy-based, continuous state, continuous/discrete action space.

<h3>background</h3>: In particular, every time an agent acts upon the environment, an expensive simulation step is conducted. Thus to reduce the cost of simulation, we need to reduce the number of simulation steps (i.e. samples of the environment). This need for sample efficiency is even more compelling when agents are deployed in the real world.

<h3>Problem</h3>: experinece replay buffer has been used in deep Q learning to reduce sample correlation ans increase sample efficiency.  However, we need to do better than deep Q-learning, because it has two important limitations. First, the deterministic nature of the optimal policy limits its use in adversarial domains. Second, finding the greedy action with respect to the Q function is costly for large action spaces. 

Policy gradient methods have been at the heart of significant advances in AI and robotics. Many of these methods are restricted to continuous domains or to very specific tasks such as playing Go. The existing variants applicable to both continuous and discrete domains, such as the on-policy asynchronous advantage actor critic (A3C) are sample inefficient.

<h3>reasones</h3>: xxx

<h3>solution</h3>: introduce an actor critic with experience replay (ACER) based on recent advances in deep neural networks, variance reduction techniques, the off-policy Retrace algorithm and parallel training of RL agents. Yet, crucially, its success hinges on innovations advanced in this paper: truncated importance sampling with bias correction, stochastic dueling network architectures, and efficient trust region policy optimization.

<h3>benefits analysis</h3>: nearly matches the state-of-the-art performance of deep Q-networks with prioritized replay on Atari, and substantially outperforms A3C in terms of sample efficiency on both Atari and continuous control domains.

<h3>issue one</h3>: when calculating policy gradients, we can use advantage function A, state-action value Q, discounted reward R, or TD residual, without introducing bias. These choices will however have different variance. Moreover, in practice we will approximate these quantities with neural networks thus introducing additional approximation errors and biases. Typically, the policy gradient estimator using R will have higher variance and lower bias whereas the estimators using function approximation will have higher bias and lower variance. solution -- Combining R with the current value function approximation to minimize bias while maintaining bounded variance is one of the central design principles behind ACER. another example is: A3C combines both k-step returns and function approximation on a single trajectory sample to trade-off variance and bias.

Experiment environment: Artari.

Metrics: rewards from games.

[paper]:https://arxiv.org/pdf/1611.01224.pdf