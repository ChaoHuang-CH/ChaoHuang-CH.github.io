---
layout: post
title:  "Meta Learning -- Basics and Background"
date:   2022-01-05 02:41:36 +0530
categories: reading
type: blog
---
Meta learning definitions, evaluation, and toolkit.

<h3>Introduction</h3> The success of the deep learning has supported a variety of applications (e.g., urban civilization, self-driven vehicles, medicine discovery). It has stimulated machine intelligence into a novel revolution in human technology history. With the benefits of deep learning, voice assistants, automated route planning, and pattern recognition in medical images have become natural parts of human lives and social development. 

However, the current machinelearning paradigm specifies a single task by training a hand-designed model, where the constraints are obvious; for example: (1) Expensive data consumption and requirements of computing resources limit many kinds of research in specific fields. (2) Interpretability of the “black box” remains weak. The learning mechanism of hierarchy structure in the deep neural network still contains many unknown processes and a lack of transparency. (3) Potential helpful knowledge (e.g., prior knowledge) cannot directly fuse into a deep learning strategy, which thus stays self-isolated from general knowledge.

<h3>Definitions</h3> Meta-learning, also referred to as learning to learn, has been frequently highlighted through its involvement in versatile research and implementations in recent years. Meta-learning can be formally defined from multiple points of view, here we mainly focuses on the two most common perspectives: task distribution and bilevel optimization. Task distribution emphasizes learning across a set of tasks to stimulate better generalization ability for each task. Like most machine-learning paradigm, there are two stages in meta-learning: meta-training and meta-testing. Unlike machine-learning methods, each dataset needs an elaborate design. In contrast to the single-level optimization in traditional machine learning and deep learning, meta-learning maintains a bilevel optimization with an inner loop (i.e., training on a base model like a regular machine-learning or deep-learning paradigm) and an outer loop (i.e., training on a meta-learning paradigm). The practical goal of training a meta-learner usually falls into two categories: creating an optimal initialization and/or learning a meta-policy to guide the further learning procedures.

<h3>Evaluation -- advantages and problems</h3> --advantages, including: (1) Data efficiency with only minimal training data for each task. (2) Fast adaptation usually occurs within a couple of gradient steps, in contrast to the timeconsuming training processes needed in machine learning and deep learning. (3) Good generalization and robustness with unseen tasks promote metalearning applicability in research. --problems, including: (1) Meta-overfitting occurs when the meta-knowledge learned from source tasks cannot generalize well into target tasks—the meta-learner generalizes well from the meta-training tasks but performs poorly in adapting to unseen tasks. Memorization issues can cause meta-overfitting: instead of learning to adapt to different tasks based on the meta-training tasks, the meta-learner is memorizing a function toprocess all meta-training data. Careful design of mutually exclusive meta-training tasks can offer one solution to avoid this problem. another solution is to learning without memorization. (2) task heterogeneity. Some good performances are based on narrow task diversity or modality (e.g., assumption of a unimodal setup), while generalization of various tasks is still difficult. Potential solutions are reducing the task uncertainty and heterogeneity through a hierarchically structured meta-learning approach or using adaptive task-sampling methods to enhance the model’s generalization ability. (3) expensive computing process, bilevel optimization may cause computer memory hunger and longer training time (since each outer loop demands a couple of inner loops), further limiting research to only few-shot regimes rather than many-shot setups. (4): lack of training task resources (i.e., task families) persists for specific meta-learning problems or application fields.

<h3>Toolkit</h3> pip install torchmeta