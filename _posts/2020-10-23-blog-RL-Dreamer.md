---
layout: post
title:  "Reinforcement Learning -- Dreamer"
date:   2020-11-01 02:41:36 +0530
categories: reading
type: blog
---
[paper][paper] tittle: DREAM TO CONTROL: LEARNING BEHAVIORS BY LATENT IMAGINATION.

classification: model-based, off-policy, policy-based, continuous state, continuous action space.

Problem: Intelligent agents can achieve goals in complex environments even though they never encounter the exact same situation twice. This ability requires building representations of the world from past experience that enable generalization to novel situations. World models offer an explicit way to represent an agent’s knowledge about the world in a parametric model that can make predictions about the future. first, how to learn long-horizon behaviors from images purely. second, how to learn the world model effectively from high-dimensional input space.

reasones: While learning world models from high-dimensional sensory inputs is becoming feasible through deep learning, there are many potential ways for deriving behaviors from them. However, considering only rewards within a fixed imagination horizon results in shortsighted behaviors.  Moreover, prior work commonly resorts to derivative-free optimization for robustness to model errors, rather than leveraging analytic gradients offered by neural network dynamics.

solution: We present Dreamer, an agent that learns long-horizon behaviors from images purely by latent imagination. A novel actor critic algorithm accounts for rewards beyond the imagination horizon while making efficient use of the neural network dynamics. For this, we predict state values and actions in the learned latent space. The values optimize Bellman consistency for imagined rewards and the policy maximizes the values by propagating their analytic gradients back through the dynamics. First, Learning the latent dynamics model from the dataset of past experience to predict future rewards from actions and past observations. Second, Learning action and value models from predicted latent trajectories. The value model optimizes Bellman consistency for imagined rewards and the action model is updated by propagating gradients of value estimates back through the neural network dynamics. Third, Executing the learned action model in the world to collect new experience for growing the dataset.

benefits analysis: In comparison to actor critic algorithms that learn online or by experience replay, world models can interpolate past experience and offer analytic gradients of multi-step returns for efficient policy optimization.


Experiment environment: evaluate Dreamer on 20 visual control tasks of the DeepMind Control Suite.

Metrics: rewards from games.

[paper]:https://arxiv.org/abs/1912.01603