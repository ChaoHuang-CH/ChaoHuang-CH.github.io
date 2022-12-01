---
layout: post
title:  "Reinforcement Learning -- TRPO"
date:   2020-11-02 02:41:36 +0530
categories: reading
type: blog
---
[paper][paper] tittle: Trust Region Policy Optimization.

classification: model-free, on-policy, policy-based, continuous state, continuous action space.

background: policy optimization can be classified into three broad categories: 
(1) policy iteration methods, which alternate between estimating the value function under the current policy and improving the policy; 
(2) policy gradient methods, which use an estimator of the gradient of the expected return (total reward) obtained from sample trajectories; 
(3) derivative-free optimization methods, such as the cross-entropy method (CEM) and covariance matrix adaptation (CMA), which treat the return as a black box function to be optimized in terms of the policy parameters.

For continuous control problems, methods like CMA have been successful at learning control policies for challenging tasks like locomotion when provided with hand-engineered policy classes with low-dimensional parameterizations. 

math: given two policies \pi and \pi'; J(\pi') = J(\pi) + E_{(s,a) \in \pi'}[\sum_{t=0}^{infinite}\gamma^{t}A_{\pi}(s,a)]. If we use state's unproper visition probability P(s; \pi'), we can rewrite this equation with the sum over states instead of time-steps: J(\pi') = J(\pi) + \sum_{S} [P(s; \pi')\sum_{A}\pi'(s,a)\gamma^{t}A_{\pi}(s,a)]. This equation implies that any policy update \pi → \pi' that has a nonnegative expected advantage at every state s is guaranteed to increase the policy performance.

Problem: Continuous gradient-based optimization has been very successful at learning function approximators for supervised learning tasks with huge numbers of parameters, and extending their success to reinforcement learning would allow for efficient training of complex and powerful policies. The inability of gradient-based methods to consistently beat gradient-free random search is unsatisfying, since gradient-based optimization algorithms enjoy much better sample complexity guarantees than gradient-free methods.

reasones: for the deterministic policy, improves the policy if there is at least one state-action pair with a positive advantage value and nonzero state visitation probability, otherwise the algorithm has converged to the optimal policy. However, in the approximate setting, it will typically be unavoidable, due to estimation and approximation error, that there will be some states s for which the expected advantage is negative.

solution: we first prove that minimizing a certain surrogate objective function guarantees policy improvement with non-trivial step sizes.

benefits analysis: These algorithms are scalable and can optimize nonlinear policies with tens of thousands of parameters, which have previously posed a major challenge for model-free policy search.

issue one: the relationship (equatipon) between the objective function of two given policies \pi and \pi' depends on state's improper visitation probability, which is difficult to optimize directly. -- solution: instead of useing \pi' to calculate state's improper visitation probability, we gonna use \pi. L_{\pi}(\pi') = J(\pi) + \sum_{S} [P(s; \pi)\sum_{A}\pi'(s,a)\gamma^{t}A_{\pi}(s,a)].

issue two: given that L_{\pi}(\pi) = J(\pi), implies that a sufficiently small step \pi → \pi' that improves L_{\pi} will also improve J(), but does not give us any guidance on how big of a step to take. -- solution: conservative policy iteration, for which they could provide explicit lower bounds on the improvement of J(). \pi' = argmax_{\pi'}L_{\pi}(\pi'), then the new policy will be \pi_{new} = (1-a)\pi + a\pi'. And the lower bound is: J(\pi_{new}) > L_{\pi}(\pi_{new}) - (2M\gamma)a^2/(1-\gamma)^2.

issue three: Since mixture policies are rarely used in practice, this result is crucial for extending the improvement guarantee to practical problems. -- solution:the improve bound can be extended to general stochastic policies, rather than just mixture polices, by replacing "a" with distance measure between \pi and \pi', and changing the constant M appropriately.  total variation divergence: D_{TV}^{max}(\pi, \pi')=max_{s}D_{TV}[\pi(*|s),\pi'(*|s)]. 

issue four: Given that D_{TV}(p,q)^2 <= D_{KL}(p,q), Trust region policy optimization uses a constraint on the KL divergence rather than a penalty to robustly allow large updates.

Experiment environment: Simulated Robotic Locomotion in Mujoco, Atari games, 

Metrics: rewards from games.

[paper]:https://arxiv.org/pdf/1502.05477.pdf