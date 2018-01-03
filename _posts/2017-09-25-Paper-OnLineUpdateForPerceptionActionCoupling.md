---
layout: post
title:  "Paper presented @ IROS 2017: An Information-Theoretic On-Line Update Principle for Perception-Action Coupling"
date:   2017-09-25 14:30:00
publication: true
pubtype: "paper"
publink: "http://ieeexplore.ieee.org/document/8202240/?reload=true"
#downloadlink: ""
pubtitle: "An Information-Theoretic On-Line Update Principle for Perception-Action Coupling"
doi: "10.1109/IROS.2017.8202240"
citeas: "Peng Z, Genewein T, Leibfried F, Braun DA (2017). An Information-Theoretic On-Line Update Principle for Perception-Action Coupling. IROS 2017. doi: 10.1109/IROS.2017.8202240"
excerpt: "Peng Z, Genewein T, Leibfried F, Braun DA (2017). An Information-Theoretic On-Line Update Principle for Perception-Action Coupling."
tags: [publication, paper, rate distortion, bounded rationality, perception-action]
---
Our paper: *An Information-Theoretic On-Line Update Principle for Perception-Action Coupling* was presented at this year's IROS in Vancouver. The paper builds upon the [information-theoretic principle for perception-action coupling](/research/sensingforacting/) where a decision-maker is conceptualized as two serial information-processing channels: the first channel extracts relevant information about the "world-state" from the sensory stream and forms a "percept". Subsequently an action-stage picks an action based on the internal percept in order to maximize utility or reward in a bounded rational fashion. 

The theoretical groundwork for this paper has been layed in [our 2015 Frontiers paper]({{site.url}}/Paper-AbstractionsHierarchiesOptimalityPrinciple/) but back then applications were limited to discrete toy-problems with a very low-dimensional state- and action-space. In this paper we derive a gradient-based on-line update rule to optimize the information-theoretic optimality principle for perception-action coupling. This allows using neural networks as powerful parametric models, which is the first step towards large-scale, continuous and high-dimensional applications of our principle. In the paper, we show that the gradient-based updates converge to equivalent solutions on a toy example used in our previous paper. Finally, we use the principle to simultaneously learn (bounded) optimal perceptual representations and action-policies for a simple visuomotor grasping task with a simulated NAO robot. Importantly, the perceptual stage of the robot is implemented with a neural network. 

