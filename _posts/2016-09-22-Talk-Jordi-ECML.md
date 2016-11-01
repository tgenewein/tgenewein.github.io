---
layout: post
title:  "Talk by Jordi Grau-Moya @ ECML 2016"
date:   2016-09-22 11:00:00
publication: true
pubtype: "talk"
publink: "https://www.springerprofessional.de/en/planning-with-information-processing-constraints-and-model-uncer/10652396"
downloadlink: "https://arxiv.org/pdf/1604.02080v1.pdf"
pubtitle: "Planning with Information-Processing Constraints and Model Uncertainty in Markov Decision Processes"
citeas: "Grau-Moya J, Leibfried F, Genewein T, Braun D.A. (2016) Planning with Information-Processing Constraints and Model Uncertainty in Markov Decision Processes. ECML PKDD 2016, Riva del Garda, Italy, Proceedings, Part II"
excerpt: "Talk by Jordi Grau-Moya on our paper: Planning with Information-Processing Constraints and Model Uncertainty in Markov Decision Processes"
tags: [publication, talk, bounded rationality, decision-making, model uncertainty, MDP, planning]
---
[Jordi Grau-Moya](http://graumoya.com/) presented our paper on *Planning with Information-Processing Constraints and Model Uncertainty in Markov Decision Processes* at ECML 2016. In the paper, the [free energy principle for decision-making](/research/boundedrationality) is used to model different traits of (human) decision-making in a Markov decision-process (MDP): 

*  **bounded rationality**, that is decision-making under limited computational resources. In the MDP setting this corresponds to agents, that cannot produce deterministic policies but rather have some degree of stochasticity (noise) in their action-selection/-execution.
*  **model uncertainty** - the agent is aware that its (state-transition-) model of the environment does not precisely reflect the true world and thus allows optimistic or pessimistic deviations from that model to drive exploration.

The application of the free-energy principle to planning in the MDP setting leads to a value-iteration like scheme, that allows to model both bounded rationality but also model uncertainty. Interestingly, the degree of bounded rationality but also the degree of model uncertainty is governed by a continuous parameter. For model-uncertainty, this parameter can produce exploration behavior on a a continuum between optimism, indifference or pessimism in the face of uncertainty, which could be very interesting for a general robot-learning framework where the model-uncertainty attitude is governed by the task-setting (an autonomous car should probably explore in a very conservative fashion, whereas a simulated robot can potentially explore with great optimism to speed up learning).