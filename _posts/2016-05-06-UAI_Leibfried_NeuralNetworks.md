---
layout: post
title:  "Paper by F. Leibfried: Bounded rational decision-making in feedforward neural networks"
date:   2016-05-06 11:00:00
publication: false
excerpt: "Information-theoretic framework for bounded rationality applied to feedforward neural networks, by Felix Leibfried."
tags: [bounded rationality, information theory, neural networks, convnets, regularization]
---

[Felix Leibfried](http://www.felixleibfried.com/) just published a very interesting application of the [information-theoretic principle for bounded rationality](/research/naturalabstractions/) to feedforward neural networks (including convolutional neural networks). This work will be presented in a plenary talk at [UAI 2016](http://www.auai.org/uai2016/index.php).

In a nutshell, the information-theoretic optimality principle (similar to the rate-distortion principle, see [here](/research/naturalabstractions/)) was used to derive a gradient-based on-line update rule to learn the parameters of a neural network. In the principle, gains in utility must be traded off against the computational cost that these gains incur

$$
\underset{p_\theta(a|w)}{\text{arg max}} \underbrace{\sum_{w,a} p_\theta(w,a) U(w,a)}_{\text{expected utility}} - \frac{1}{\beta} \underbrace{I(W;A)}_{\text{computational demand}},
$$ 

where a parametric model $$p_\theta(a\vert w)$$ is used to describe the stochastic mapping from an input $$w$$ to an output $$a$$. In the paper, Felix shows how to derive a gradient-ascent rule for finding a (locally) optimal $$\theta$$. Then, the paper shows how to apply the same principle and derive an on-line gradient-based update rule when using a feedforward neural network for the parametric model. Interestingly, the result is an update-rule very similar to the (well-known) error-backpropagation with an additional regularization-term that results from the mutual information constraint (that formalizes limited computational capacity). 

This result adds an interesting angle to the notion of limited computational resources: an alternative way to interpret computational limitations is to view them as a regularizer, that (sort of) artificially imposes computational limitations in order to be robust. This regularizer reflects the computational limitation that results from having small sample sizes - with an infinitely large sample size, corresponding to no computational limitation, the regularizer is not needed. However, under limited sample size (limited information to update the parameters), a regularizer "emulates" limited computational resources that reflect the lack of rich parameter-update information.  

The paper concludes by showing simulations that apply the learning rule to a regular multi-layer perceptron as well as a convolutional neural network on the MNIST data set. 

