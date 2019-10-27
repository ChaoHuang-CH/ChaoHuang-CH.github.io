---
layout: post
title:  "Deep Multi-task and Meta-learning"
date:   2019-10-27 02:41:36 +0530
categories: Lecture1
type: blog
---
Why would we study robots?
    Because robots can teach us things about intelligence.

How can we enable the agents to learn skills from the real world? What are the challenges when agents facing with the real world?
    a) must generalize across tasks, objects, environments etc..
    b) need some common sense to do things well.
    c) supervison can not be taken for granted.

What are the drawbacks of traditional robot reinforcement learning or reinforcement learning?
    a) learn one task in one environment, starding from scratch.
    b) realy on detailed guidance and supervision.
    c) even though there are lots of application, but still one task, from scratch, with supervision.

However, humans are generalists.

Why should we care about multi-tasks learning or meta-learning?
    a) deep learning allows us to handle unstructured inputs (pictures, languages, sensor readings, etc.) without hand-engineering features, with less domain-knowledge. However, in order to obtain broad generalization, deep learning needs large, diverse data and large model.
    b) what if we don't have a large dataset? it will be impratical to learn from scratch for every disease, each robot, each person, each language, each task, etc..
    c) what if our data has a long tail? this setting breaks the standard machine learning paradigms.
    d) what if we need to quickly learn something new about a new person, for a new environment, about a new task, etc.?
    e) what if we want a more general-purpose AI system? And learning from scratch can not cut it.

Given that we all know that multi-task learning is about learning all of the tasks more quickly or more proficently than learning them independly; And meta-learning is about learning a new task more quickly or more proficently by using data/experience on previous tasks. Then you will wonder about what is a task?
    a) definition: (dataset D + loss function L) ==> learned model F.
    b) properties: havd different objects, people, objectives, lighting conditions, words, etc.
    c) bad news: different tasks need to share some structures, if that doesn't hold, you are better off using single-task learning.
    d) good news: there are many tasks with shared structure.
        1) the law of physics underlying in the real world.
        2) people are all organisms with intentions.
        3) the rules of english under english language.
        4) languages all be developed for the same purpose.


