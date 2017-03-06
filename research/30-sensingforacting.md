---
layout: page
title: Sensing for acting - likelihood function synthetization
share: false
researchtopicpage: true
shorttitle: Sensing for acting # for display in the sidebar menu
# date: 2016-01-16 13:53:00
permalink: /research/sensingforacting/
---

{% include _toc.html %}


This article extends the rate-distortion principle for bounded rational decision-making presented in [this research article]({{ site.url }}/research/naturalabstractions/), make sure to read it first if you're unfamiliar with the information-theoretic framework for bounded rationality.

In this research article, the basic principle of trading off gains in expected utility against the computational demand that these gains imply, is consequently applied to a two-stage serial information processing chain. One interpretation of this chain is that the first stage of the chain acts as a perceptual stage that extracts information about the world-state which is used to subsequently drive the second stage that computes a (bounded) optimal action. The key insight, derived by analyzing this processing chain under the information-theoretic framework for bounded rationality is that optimal perception under limited computational resources is shaped by action and cannot be achieved by simply trying to represent the world-state as faithfully as possible. As a result, perception and action become tightly coupled and cannot be treated as two independent problems.

### Decoupled inference and decision-making
Consider the following problem: given a world-state $$w$$, an agent with limited computational resources should compute an action $$a$$ in order to maximize the utility $$U(w,a)$$. However, in contrast to the [previous problem setup]({{ site.url }}/research/naturalabstractions/), the world-state is not accessible directly, but it can be transformed into an internal percept $$x$$ by a perceptual stage. The percept can then be used to drive a subsequent decision-making stage. Formally, the following conditional independences hold:


$$
p(w,x,a)=p(w)p(x|w)p(a|x)
$$

which can also be represented as the graphical model $$W \rightarrow X \rightarrow A$$.

The classical approach is to treat perception as an inference problem and compute the most likely world-state, given the current percept using Bayesian inference:

$$
p(w|x)=\frac{p(x|w)p(w)}{p(x)}
$$

The subsequent decision-maker should then maximize the expected utility under the posterior belief over $$w$$: $$U(x,a) = \sum_w p(w \vert x) U(w,a)$$. Since the decision-maker has limited computational resources, it can be modeled with the information-theoretic framework for bounded rationality. From the [previous research article]({{ site.url }}/research/naturalabstractions/) it follows that the decision-making stage is given by:

$$
p^*(a|x) = \frac{1}{Z}p(a)e^{\beta_2 U(x,a)}
$$

Using this approach, the likelihood function $$p(x\vert w)$$ must be specified by the designer of the system. Commonly, the likelihood function is chosen in order to maximize predictive power, that is $$w$$ should be represented as faithfully as possible through $$x$$. Note that we assume that the perceptual stage is also limited in computational capacity which prevents a one-to-one mapping from $$w$$ to $$x$$.

In the following we will see how the consequent application of trading-off utility against computational cost leads to a well-defined likelihood function that is tightly coupled to the action-stage of the system.

### Information-theoretic bounded rationality
Within the information-theoretic framework for bounded rationality, gains in expected utility must be traded off against the cost of computation, which is measured in terms of mutual information. For the perception-action system this means that both the computation of the decision-making stage but also the computation of the perceptual stage must be taken into account, leading to the following objective:

$$
\begin{align}
p^*(x|w), p^*(a|x) = \underset{p(x|w), p(a|x)}{\text{arg max}} &\sum_{w,x,a} p(w) p(x|w) p(a|x) U(w,a)\\
 &- \frac{1}{\beta_1} I(W;X) - \frac{1}{\beta_2} I(A;X)
\end{align}
$$

where the mutual information terms measure the (average) computational demand of the perception- and the action-stage respectively and the inverse temperatures $$\beta_1, \beta_2$$ translate computational demand into cost of computation.


### Likelihood function synthetization
The optimization problem given in the previous paragraph has a closed-form solution, given by the set of self-consistent equations:

$$
\begin{align}
p^*(x|w)&=\frac{1}{Z_x}p(x)e^{\beta_1 \Delta F(w,x)}\\
p^*(a|x)&=\frac{1}{Z_a}p(a)e^{\beta_2 \sum_w p(w|x) U(w,a)}
\end{align}
$$

where $$p(w \vert x)$$ is given by Bayes' rule $$p(w \vert x)=\frac{1}{p(w)}p^*(x \vert w)p(x)$$.  
$$\Delta F(w,x)$$ is the free energy (difference) of the action stage

$$
\Delta F(w,x)=\sum_a p^*(a|x) U(w,a) - \frac{1}{\beta_2} D_{\text{KL}}(p^*(a|x)||p(a))
$$

and acts as a utility for the perceptual stage, that is the perceptual stage maximizes the free energy trade-off of the action-stage in a bounded rational fashion. Additionally, $$p(x)=\sum_w p(w)p^*(x \vert w)$$ and $$p(a)=\sum_{w,x} p(w)p^*(x \vert w)p^*(a \vert x)$$.


Importantly, the solution given by the self-consistent equations specifies the (bounded-optimal) likelihood function $$p^*(x \vert w)$$ for inference over the world-state $$w$$. The bounded-optimal decision-maker is identical to the bounded rational decision-maker the was intuitively specified in the section earlier, where inference and decision-making were decoupled and the decision maker was maximizing the posterior expected utility in a bounded rational fashion.


### Optimal perception is shaped by action
By inspecting the solution for the bounded optimal likelihood function $$p^*(x \vert w)$$, it can be seen that the free energy trade-off of the downstream action stage (that is trading off high expected utility against low computational demand) plays the role of a utility for the perception stage, since the solution of the perception stage follows a bounded optimal solution that consists of a prior times the exponential of the "utility" multiplied by the inverse temperature:

$$
\text{posterior}\propto \text{prior}~e^{\beta~\text{utility}}
$$

Crucially, this means that bounded-optimal perception has the goal of **enabling the action-stage to operate as efficiently as possible** (by maximizing its free energy). This is in contrast to many classical approaches that assign perception the role of representing the world-state $$w$$ as faithfully as possible (given the model's limitations) and simply decouple perception and action. 



##### Further reading
An illustrative example that compares classical, decoupled perception and action against a bounded-optimal perception-action system can be found in [this paper]({{ site.url }}/Paper-AbstractionsHierarchiesOptimalityPrinciple/). The example is also found in this [Jupyter notebook](https://github.com/tgenewein/BoundedRationalityAbstractionAndHierarchicalDecisionMaking/blob/master/NotebooksAndCode/3-SerialHierarchy.ipynb) (use [this link](http://nbviewer.jupyter.org/github/tgenewein/BoundedRationalityAbstractionAndHierarchicalDecisionMaking/blob/master/NotebooksAndCode/3-SerialHierarchy.ipynb) if you simply want to view the notebook in your browser).   
