---
layout: post
title:  "Reinforcement Learning -- Double DQN"
date:   2020-10-28 02:41:36 +0530
categories: reading
type: blog
---
[paper][paper] tittle: Deep Reinforcement Learning with Double Q-learning.

<h3>classification</h3>: model-free, off-policy, value-based, continuous state, discrete action space.

<h3>Problem</h3>: the popular Q-learning algorithm is known to overestimate action values under certain conditions.

<h3>reasones</h3>: First, it includes a maxmization step over estimated action values, which tends to prefer overestimated to underestimated values. Second, previously, overestimations have been attributed to insufficiently flexible function approximation and noise. Third, in this paper, we unify these views and show overestimations can occur when the action values are inaccurate, irrespective of the source of approximation error.

<h3>problem's results</h3>: first, If all values would be uniformly higher then the relative action preferences are preserved and we would not expect the resulting policy to be any worse. second, optimism in the face of uncertainty is a well-known exploration technique. third, If the overestimations are not uniform and not concentrated at states about which we wish to learn more, then they might negatively affect the quality of the resulting policy.

<h3>solution</h3>: the max operator used in loss function to obtain target value $Y = r + \gamma max_{a'}Q(s',a';\thate)$, uses the same values both to select and to evaluate an action. This makes it more likely to select overestimated values, resulting in overoptimistic value estimates. To
prevent this, we can decouple the selection from the evaluation: $Y = r + \gamma Q(s',argmax_{a}Q(s',a;\theta');\thate)$.

<h3>analysis</h3>: first, upper bound --  if the action values contain random errors uniformly distributed in an interval $[−\si, \si]$ then each target is overestimated up to $\gamma \si (m−1)/(m+1)$, where m is the number of actions. second, lower bound -- estimation errors of any kind can induce an upward bias, regardless of whether these errors are due to environmental noise, function approximation, non-stationarity, or any other source. $\sum_{a}(Q(s,a) - V_{*}(s))=0$, estimation unbiased. $\sum_{a}(Q(s,a) - V_{*}(s))^2 = mC$, estimation error. under these conditions, $max_{a}Q(s,a) >= V_{*}(s) + \sqrt{C/(m-1)}$.

Experiment environment: Atari 2600 platform.

Metrics: estimation of state-action values.

[paper]:https://arxiv.org/pdf/1509.06461v3.pdf