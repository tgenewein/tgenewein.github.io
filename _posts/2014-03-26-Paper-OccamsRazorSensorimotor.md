---
layout: post
title:  "Paper published: Occam's Razor in sensorimotor learning"
date:   2014-03-26 15:00:00
publication: true
pubtype: "paper"
publink: "http://rspb.royalsocietypublishing.org/content/281/1783/20132952"
downloadlink: "http://rspb.royalsocietypublishing.org/content/281/1783/20132952.full-text.pdf"
pubtitle: "Occam's Razor in sensorimotor learning"
doi: "10.1098/rspb.2013.2952"
citeas: "Genewein T, Braun DA (2104) Occam's Razor in sensorimotor learning. Proceedings of the Royal Societey B 281:20132952. DOI: 10.1098/rspb.2013.2952"
excerpt: "Genewein T, Braun DA (2104) Occam's Razor in sensorimotor learning."
tags: [publication, paper, Bayesian model selection, Occam's razor, sensorimotor regression, virtual reality experiment]
---
{% include _toc.html %}

Our paper on sensorimotor regression and the preference of simpler models got published in Proceedings B of the Royal Society.

In the paper we present a sensorimotor regression paradigm that allows for testing whether humans act in line with Occam's razor and *prefer the simpler explanation* if two models explain the data equally well.

## Bayesian model selection
We modeled human choice behavior with Bayesian model selection. In Bayesian model selection, models $M_1$ and $M_2$ are compared by taking their posterior probability ratio (given the data $D$)

$$
\underbrace{\frac{P(M_1|D)}{P(M_2|D)}}_{\text{posterior odds}} = \underbrace{\frac{P(D|M_1)}{P(D|M_2)}}_{\text{Occam factor}} \underbrace{\frac{P(M_1)}{P(M_2)}}_{\text{prior odds}},
$$

where the model evidence or marginal likelihood is given by marginalizing over the model parameters $\theta$

$$
P(D|M_i)=\int P(D|\theta,M_i)P(\theta|M_i) d\theta.
$$

If the ratio of posterior odds is larger than one, model $M_1$ should be preferred - if the posterior odds ratio is smaller than one, the data is in favor of $M_2$.  If the strength of preference is ignored, the previous rule leads to a deterministic model selection mechanism. Additionally, the magnitude of the posterior odds ratio is an indicator of the strength of the preference which can be used to derive stochastic model selection mechanisms (for instance by combination with a softmax selection rule). In case of equal prior probabilities for both models, the quantity that governs model selection is the *Bayes factor*, which is the ratio of marginal likelihoods.

## Bayesian Occam's razor
**TODO**

## Experiment design - marginal likelihood of a Gaussian processes
**TODO**

## Results
We found participants' behavior to be quantitatively consistent with the theoretical model of Bayesian model selection combined with a softmax model selection mechanism.
