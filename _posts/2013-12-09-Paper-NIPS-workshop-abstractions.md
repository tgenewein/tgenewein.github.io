---
layout: post
title:  "Paper presented at NIPS 2013 workshop: Abstraction in Decision-Makers with Limited Information Processing Capabilities"
date:   2013-12-09 16:00:00
publication: true
pubtype: "paper"
publink: "http://arxiv.org/abs/1312.4353"
downloadlink: "http://arxiv.org/pdf/1312.4353v2"
pubtitle: "Abstraction in Decision-Makers with Limited Information Processing Capabilities"
citeas: "Genewein T, Braun DA (2013) Abstraction in Decision-Makers with Limited Information Processing Capabilities, NIPS 2013 workshop on Planning with Information Constraints. arXiv:1312.4353"
excerpt: "Genewein T, Braun DA (2013) Abstraction in Decision-Makers with Limited Information Processing Capabilities. 	arXiv:1312.4353"
tags: [publication, paper, abstractions, bounded rationality, decision-making, free energy]
---
{% include _toc.html %}

Our paper on "Abstraction in decision-makers with limited information processing capabilities" was presented at the NIPS 2013 workshop on [*Planning with Information Constraints*](https://old.nips.cc/Conferences/2013/Program/event.php?ID=3723) - you can find the slides of my talk [here](/Talk-NIPS-workshop-abstraction/).

The paper is about constructing optimal decision-makers that have limited computational capacity. As a consequence of these computational limitations we find that natural levels of abstraction emerge in the agent's behavior.

## Bounded rational decision-making
In classical decision-making an agent is presented with an observation $$w$$ and is then faced with the task of picking an optimal action $$a^*$$ out of a set of actions such that the utility $$U(w,a)$$ is maximized. This is known as the maximum-expected-utility (MEU) principle. The problem with MEU is that finding the best action out of a large set of actions can be computationally very demanding and for an agent with limited computational resources that has to react within a certain time-limit this search problem can easily become infeasible.

To overcome the intractable search-problem over actions the MEU rule can be replaced with a soft maximum rule where the agent does not seek for the single best action but rather picks the first action that fulfills a certain fidelity constraint. In other words: the agent searches through action space according to some search distribution and picks the first action that is *good enough*. This is the central idea behind bounded rational decision-making and it can be implemented in many different ways (heuristics, probabilistic approximation schemes, etc.). In the paper we build upon a quantitative probabilistic framework for bounded rational decision-making that is derived from first principles and (perhaps surprisingly) has strong ties to free energy minimization in thermodynamics. The resulting optimization problem for optimal acting under limited computational resources is mathematically equivalent to the problem formulation in *rate distortion theory*, the information-theoretic framework for lossy compression. In rate distortion theory the goal is to compress information such that a distortion measure is minimized while at the same time not exceeding a limit on the channel capacity. Analogously, the optimality principle for bounded rational acting trades off a large expected utility against low computational cost

$$
p^*(a|w) = \underset{p(a|w)}{\text{arg max}}~\underbrace{\sum_{w,a}p(w)p(a|w)U(w,a)}_{\text{expected utility}} - \underbrace{\frac{1}{\beta} I(w;a)}_{\text{computational cost}}
$$

The trade-off is a variational problem over the optimal policy $$p^*(a|w)$$ that maps world-states $$w$$ to actions $$a$$ such that the expected utility is maximized while at the same time keeping the computational cost low. The computational cost arises because for each $$w$$ the agent has to adapt its behavior from (a prior) $$p(a)$$ to (a posterior) $$p(a|w)$$ and the average computational effort for this adaptation is measured with the mutual information $$I(w;a)$$ which is the average KL-divergence from prior to posterior. The factor $$\beta$$ governs the trade-off and due to the thermodynamic roots of the principle is called the *inverse temperature*.  
The optimization problem has a closed-form solution (actually a set of two self-consistent equations) which is well known in information theory and can be computed with the Blahut-Arimoto algorithm.

See [Research](/research/) for more information on the thermodynamic framework and its connection to rate distortion theory.


## Bounded rationality and abstractions
Abstractions are formed by reducing the information content of an entity until it only contains crucial information. For instance, consider the abstract concept of a chair: chairs can come in many different colors, materials, sizes and even different particular shapes but there is something crucial to an object to make it a chair and distinguish it from a table or a sofa. In a sense the abstract concept is a lossy compression where irrelevant details ("noise" such as color or material) have been discarded. The problem of finding optimal lossy compressions and forming abstractions are thus tightly related. The information-theoretic principle for bounded rational decision-making can be cast as a lossy compression problem, therefore the principle can also be used to form bounded-optimal abstractions. In decision-making, abstractions translate into behavior where several world-states $$w$$ are treated *as if they were the same*, meaning that the agent uses the same policy $$p(a|w)$$ for subsets of world-states.

In the paper we show that the information-theoretic principle for bounded rational acting leads to the formation of behavioral abstractions. Importantly, the inverse temperature $$\beta$$ controls the granularity and thus the level of abstraction. We illustrate this in the paper with an example and show that the abstractions formed by the principle are shaped by the utility-function and the computational limitations of the agent. Interestingly we find that in our example a low number of **levels of abstractions** emerge naturally from the utility-structure where behavior within a level of abstraction does not change qualitatively (but does get more or less stochastic). In-between the levels of abstraction there are steep "phase transitions" where behavior abruptly changes qualitatively. See the paper for more details on the example.
