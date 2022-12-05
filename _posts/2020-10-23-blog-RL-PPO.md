---
layout: post
title:  "Reinforcement Learning -- PPO"
date:   2020-11-03 02:41:36 +0530
categories: reading
type: blog
---
[paper][paper] tittle: Proximal Policy Optimization Algorithms.

<h3>classification</h3> model-free, on-policy, policy-based, continuous state, continuous action space.

<h3>background</h3> Q-learning (with function approximation) fails on many simple problems1 and is poorly understood, vanilla policy gradient methods have poor data effiency and robustness; and trust region policy optimization (TRPO) is relatively complicated, and is not compatible with architectures that include noise (such as dropout) or parameter sharing (between the policy and value function, or with auxiliary tasks).

<h3>Problem</h3> This paper seeks to improve the current state of affairs by introducing an algorithm that attains the data efficiency and reliable performance of TRPO, while using only first-order optimization.

<h3>reasones</h3> In TRPO,  an objective function (the “surrogate” objective) is maximized subject to a constraint on the size of the policy update. This problem can efficiently be approximately solved using the conjugate gradient algorithm, after making a linear approximation to the objective and a quadratic approximation to the constraint. Hence, to achieve our goal of a first-order algorithm that emulates the monotonic improvement of TRPO, we can use a penalty instead of a constraint. The reason why TRPO uses a hard constraint rather than a penalty because it is hard to choose a single value of β that performs well across different problems—or even within a single problem, where the the characteristics change over the course of learning.

<h3>solution</h3> Clipped Surrogate Objective. Let r_t(\theta) represents the probability ratio (\pi')/(\pi). Then the surrogate objective function in TRPO is L = E(r_t(\theta)A). Without a constraint, maximization of L() would lead to an excessively large policy update; hence, we now consider how to modify the objective, to penalize changes to the policy that move r_t(\theta) away from 1. The main objective we propose is the following: L = E[min(r_t(\theta)A, clip(r_t(\theta), 1-a, 1+a)A)].

<h3>benefits analysis</h3> The new methods, which we call proximal policy optimization (PPO), have some of the benefits of trust region policy optimization (TRPO), but they are much simpler to implement, more general, and have better sample complexity (empirically).

<h3>issue one</h3> xxx

<h3>Experiment environment</h3>  Continuous Domain: Humanoid Running and Steering.

<h3>Metrics</h3> rewards from games.

[paper]:https://arxiv.org/pdf/1707.06347.pdf