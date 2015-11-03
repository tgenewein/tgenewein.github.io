---
layout: post
title:  "Paper presented @ NIPS: A Nonparametric Conjugate Prior Distribution for the Maximizing Argument of a Noisy Function"
date:   2012-12-08 15:00:00
publication: true
pubtype: "paper"
publink: "http://www.adaptiveagents.org/argmaxprior"
downloadlink: "http://papers.nips.cc/paper/4536-a-nonparametric-conjugate-prior-distribution-for-the-maximizing-argument-of-a-noisy-function.pdf"
pubtitle: "A Nonparametric Conjugate Prior Distribution for the Maximizing Argument of a Noisy Function"
#doi: "10.1098/rspb.2013.2952"
citeas: "Ortega, P.A., Grau-Moya, J., Genewein, T., Balduzzi, D., Braun, D.A. (2012) A Nonparametric Conjugate Prior Distribution for the Maximizing Argument of a Noisy Function. Neural Information Processing Systems (NIPS) 2012"
excerpt: "Ortega, P.A., Grau-Moya, J., Genewein, T., Balduzzi, D., Braun, D.A. (2012) A Nonparametric Conjugate Prior Distribution for the Maximizing Argument of a Noisy Function."
tags: [publication, paper, argmax prior, optimization, bounded rationality]
---
Our paper on a *nonparametric conjugate prior distribution* for *maximizing a noisy function* was accepted and presented at NIPS 2012 in Lake Tahoe.

Many approaches to finding the maximizing argument of a noisy function use a parametric or nonparametric model for the underlying (noise-free) function. Observations are then used to update the parameters of the model (commonly Bayesian inference is performed over the parameters). The model of the underlying function is then used to find new test-points to gather more information - the most simple approach is simply taking the maximum of the modeled function and evaluating the true (noisy) function with this argument. More sophisticated implementations include some kind of exploration ($\epsilon$-greedy, picking points where uncertainty is highest like UCB or max expected information gain).  
In our paper we do not attempt to model the underlying function but rather to model our belief over the location of the maximum (the argument) directly. This belief is modeled in a nonparametric fashion and updated in light of new observations in a Bayesian way - leading to a nonparametric conjugate prior over the "location" of the maximum of the noisy function (that is the maximizing argument).

Find a very nice explanation on [Pedro Ortega's homepage](http://www.adaptiveagents.org/argmaxprior) (including MATLAB code).
