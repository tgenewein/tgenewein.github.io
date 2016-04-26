---
layout: post
title:  "Paper published: Bio-inspired feedback-circuit implementation of discrete, free energy optimizing, winner-take-all computations"
date:   2016-03-29 15:00:00
publication: true
pubtype: "paper"
publink: "http://link.springer.com/article/10.1007/s00422-016-0684-8"
downloadlink: "http://link.springer.com/content/pdf/10.1007%2Fs00422-016-0684-8.pdf"
pubtitle: "Bio-inspired feedback-circuit implementation of discrete, free energy optimizing, winner-take-all computations"
doi: "10.1007/s00422-016-0684-8"
citeas: "Genewein T, Braun DA (2016). Bio-inspired feedback-circuit implementation of discrete, free energy optimizing, winner-take-all computations. Biological Cybernetics. doi: 10.1007/s00422-016-0684-8"
excerpt: "Genewein T, Braun DA (2016). Bio-inspired feedback-circuit implementation of discrete, free energy optimizing, winner-take-all computations."
tags: [publication, paper, bounded rationality, free energy, dynamical system, replicator equation]
---

Our paper on bio-inspired feedback circuits for free-energy optimization was published. In the paper we explore the idea that a free energy minimization (which is the basis of an information theoretic framework for bounded rational inference and decision-making, see the corresponding [Research article](/research/boundedrationality/)) can be described by a dynamical system. 

Bounded rational decision-making (including Bayesian inference as a special case) requires the accumulation of utility (or evidence), to transform a prior strategy (or belief) into a posterior probability distribution over actions (or hypotheses). Crucially, this process cannot be simply realized by independent integrators, since the different hypotheses and actions also compete with each other. In continuous time, this competitive integration process can be described by a special case of the replicator equation (known from evolutionary biology for describing evolutionary competition between different populations). Here we investigate simple analog electric circuits that implement the underlying differential equation under the constraint that we only permit a limited set of building blocks that we regard as biologically interpretable, such as capacitors, resistors, voltage-dependent conductances and voltage- or current-controlled current and voltage sources. The appeal of these circuits is that they intrinsically perform normalization without requiring an explicit divisive normalization. 

However, even in idealized simulations, we find that these circuits are very sensitive to internal noise as they accumulate error over time. In the paper, we discuss in how far neural circuits could implement these operations that might provide a generic competitive principle underlying both perception and action. In short: the problem is that any naive implementation of the replicator equation requires synaptic weights to change on the same time-scale with which the (perceptual) input to the system varies. This cannot be mapped to any of the standard models of neural competitive integration (e.g. pooled-inhibition models). The paper provides a novel point of view on competitive utility (or evidence) integration that could be interesting for researchers working on the neurophysiological basis of decision-making.