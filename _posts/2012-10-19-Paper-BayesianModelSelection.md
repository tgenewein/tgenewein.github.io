---
layout: post
title:  "Paper published: A sensorimotor paradigm for Bayesian model selection"
date:   2012-10-19 15:00:00
publication: true
pubtype: "paper"
publink: "http://journal.frontiersin.org/article/10.3389/fnhum.2012.00291/"
downloadlink: "http://www.frontiersin.org/Journal/DownloadFile/1/148532/33743/1/21/fnhum-06-00291_pdf"
pubtitle: "A sensorimotor paradigm for Bayesian model selection"
doi: "10.3389/fnhum.2012.00291"
citeas: "Genewein T, Braun DA (2012) A sensorimotor paradigm for Bayesian model selection. Frontiers in Human Neuroscience 6:291. doi: 10.3389/fnhum.2012.00291"
excerpt: "Genewein T, Braun DA (2012) A sensorimotor paradigm for Bayesian model selection."
tags: [publication, paper, Bayesian model selection, virtual reality experiment]
---
Our paper on a sensorimotor paradigm for Bayesian model selection got published in Frontiers in Human Neuroscience.

In the paper we present a sensorimotor paradigm that allows for testing whether human choice behavior is quantiatively consistent with Bayesian model selection. In Bayesian model selection, models $$M_1$$ and $$M_2$$ are compared by taking their posterior probability ratio (given the data $$D$$)

$$
\underbrace{\frac{P(M_1|D)}{P(M_2|D)}}_{\text{posterior odds}} = \underbrace{\frac{P(D|M_1)}{P(D|M_2)}}_{\text{Bayes factor}} \underbrace{\frac{P(M_1)}{P(M_2)}}_{\text{prior odds}},
$$

where the model evidence or marginal likelihood is given by marginalizing over the model parameters $$\theta$$

$$
P(D|M_i)=\int P(D|\theta,M_i)P(\theta|M_i) d\theta.
$$

If the ratio of posterior odds is larger than one, model $$M_1$$ should be preferred - if the posterior odds ratio is smaller than one, the data is in favor of $$M_2$$.  If the strength of preference is ignored, the previous rule leads to a deterministic model selection mechanism. Additionally, the magnitude of the posterior odds ratio is an indicator of the strength of the preference which can be used to derive stochastic model selection mechanisms (for instance by combination with a softmax selection rule). In case of equal prior probabilities for both models, the quantity that governs model selection is the *Bayes factor*, which is the ratio of marginal likelihoods.

In the paper, we designed a virtual-reality experiment that required participants to report their belief about the model $$M_i$$ after observing some data $$D$$. Importantly, the experiment was designed such that we did not ask participants to report their belief over the parameter $$\theta$$ but rather "integrate out" the parameter dimension . To do so, we set up an experiment with a separate model- and parameter-dimension and presented an ambiguous stimulus that was compatible with a whole range of $$\theta$$-values. This required participants to "integrate out" the parameters compatible with the stimulus, similar to the marginalization when computing the model evidence.

We found participants' behavior to be quantitatively consistent with the theoretical model of Bayesian model selection combined with a softmax model selection mechanism.
