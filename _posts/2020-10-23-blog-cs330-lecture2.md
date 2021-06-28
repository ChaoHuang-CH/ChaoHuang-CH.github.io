---
layout: post
title:  "Deep Multi-task and Meta-learning"
date:   2020-10-27 02:41:36 +0530
categories: Lecture2
type: blog
---
Multi-task Learning:
    An alternative view on the multi-task lerning: split the parameters into shared parameters and task-specific parameters, then choosing how to condition on the meta-data is equivalent to choosing how and where to share the parameters.

    conditioning (some common choises):
        1) concatenation-based conditioning.
        2) additive conditioning. (actually the same to method one)
        3) multi-head architecture.
        4) multiplicative conditioning. (this method is a good idea, because it's more expressive)
        5) there are other more complex choices.
            cross-stitch networks.
            multi-task attention network.
            deep relation network.
            sluice network.
    
    the procedures to optimize the multi-task learning objective:
        1) sample mini-batch of tasks.
        2) sample mini-batch datapoints for rach task.
        3) compute loss on the mini-batch.
        4) backpropagate loss to compute gradient.
        5) apply gradient with your favorite neural net optimizer.

    challenges for multi-task learning:
        1) negative transfer (some times independed networks work best).
            optimization challenges(cross-task inference; tasks may learn at different rate).
            limited representational capacity(need much larger network).
            solution: share less across tasks.
        2) overfitting (you may not share enough)

Meta-Learning:
    two ways to view meta-learning:
        1) mehcanistic way
            deep neural network can read in an entire dataset and predictions for new datapoints.
            training model by meta-dataset, which itself consists many datapoints for each task.
            this view make it easier to implement the meta-learning algorithm.
        2) probabilistic way
            extract prior information from meta-tasks that allows efficent learning for new task.
            by using that info and small dataset to infer most likely posterior parameter.
            this view makes it more easier to understand the meta-learning algorithm.
    
    How do we train meta-train phase and adaption phase?
        based on simple machine learning principle: train and test conditions must match.

Multi-task learning is a special case of meta-learning (can be concluded from thire objectives).

hyperparameter optimization and auto-ML can be regard as meta-learning.