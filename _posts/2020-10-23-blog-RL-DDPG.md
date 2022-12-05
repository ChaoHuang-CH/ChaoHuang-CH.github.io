---
layout: post
title:  "Reinforcement Learning -- DDPG"
date:   2020-10-30 02:41:36 +0530
categories: reading
type: blog
---
[paper][paper] tittle: Deterministic policy gradient algorithms.

<h3>classification</h3> model-free, on or off-policy, policy-based, continuous state, continuous action space.

<h3>Problem</h3> computing the stochastic policy gradient may require more samples, especially if the action space has many dimensions.

<h3>reasones</h3> In the stochastic case, the policy gradient integrates over both state and action spaces, whereas in the deterministic case it only integrates over the state space.

<h3>solution</h3> Policy gradient algorithms are widely used in reinforcement learning problems with continuous action spaces. The basic idea is to represent the policy by a parametric probability distribution that stochastically selects action in state according to parameter vector. In this paper we instead consider deterministic policies.

<h3>benefits analysis</h3> the deterministic policy gradient can be estimated much more efficiently than the usual stochastic policy gradient. To ensure adequate exploration, we introduce an off-policy actor-critic algorithm that learns a deterministic target policy from an exploratory behaviour policy.

<h3>math</h3> the density at state s' after transitioning for t time-stepsfrom state s is denoted as p(s->s';t;\pi). we also denote the improper discounted state distribution by p_{\pi}(s')=\intergration_{S}\sum_{t=0}^{\infinite}\gamma^{t-1}p_0(s)p(s->s';t;\pi). we then can write the performance objective as an expectation: J(\pi_{\theta})=\intergration_{S}p_{\pi}(s)\intergration_{A}\pi_{\theta}(s,a)r(s,a)dads = E_{s \in p_{\pi}, a \in \pi_{\theta}}r(s,a).

Then the performance's gradient is: \delta_{\theta}J(\pi_{\theta})=\intergration_{S}p_{\pi}(s)\intergration_{A}\delta_{\theta}\pi_{\theta}(s,a)Q^{\pi}(s,a)dads.

<h3>Experiment environment</h3>  a high-dimensional bandit; several standard benchmark reinforcement learning tasks with low dimensional action spaces; and a high-dimensional task for controlling an octopus arm.

<h3>Metrics</h3> rewards from games.

[paper]:http://proceedings.mlr.press/v32/silver14.pdf