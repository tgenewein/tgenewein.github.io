---
layout: page
title: Natural abstractions through bounded rationality
share: false
researchtopicpage: true
shorttitle: Natural abstractions # for display in the sidebar menu
# date: 2016-01-16 13:53:00
permalink: /research/naturalabstractions/
---

{% include _toc.html %}

This article builds on the research article [bounded rationality]({{ site.url }}/research/boundedrationality/), which provides a basic introduction to bounded rationality and the information-theoretic framework for bounded rational decision making and inference.


### The optimal prior
The basic (free energy) principle of bounded rationality (introduced in the [previous research article]({{ site.url }}/research/boundedrationality/)) formalizes a trade-off between large expected utility and low computational cost. The principle assumes a prior or initial policy over actions $$p_0(a)$$ (before computation). Here, the principle is extended by searching for the optimal prior. 

When considering a single world-state $$w$$, the optimal prior is trivial to find, it is given by the optimal posterior (that deterministically maximizes utility). A more interesting question is which distribution over actions $$a$$ is optimal *on average* across all $$w$$. This leads to the follwoing optimization problem:

$$
\underset{p(a|w), p_0(a)}{\text{arg max}} \sum_{w,a} p(w) p(a|w) U(w,a) - \frac{1}{\beta} \sum_w p(w) D_{\text{KL}}(p(a|w)||p_0(a))
$$ 

The solution to the optimization over the prior is independent of the posterior and is given by the marginal distribution:

$$
p_0^*(a) = \sum_w p(a|w)p(w) = p(a)
$$

Pluggin this result back into the optimization problem leads to:

$$
p^*(a|w) = \underset{p(a|w)}{\text{arg max}} \underbrace{\sum_{w,a} p(w,a) U(w,a)}_{\text{expected utility}} - \frac{1}{\beta} \underbrace{I(W;A)}_{\text{computational demand}}
$$ 

where $$I(W;A)$$ denotes the mutual information between the random variables $$W$$ and $$A$$ which is given as the average KL-divergence between $$p(a)$$ and $$p(a\vert w)$$.  
The new optimization problem formalizes again a trade-off between high expected utility and low computational demand, however, the computational demand is now measured through the mutual information (an *average* KL divergence). The inverse temperature $$\beta$$ still plays the role of translating computational demand into a *cost of computataion* and thus governs the trade-off between the two terms.


### Closed-form solution
Similar to the free-energy case in the previous article, the optimization problem has a closed-form solution - in the form of two self-consistent equations:

$$
\begin{align}
p^*(a|w)&=\frac{1}{Z}p(a)e^{\beta U(w,a)}\\
p(a)&=\sum_w p^*(a|w)p(w) 
\end{align}
$$

with the partition sum $$Z=\sum_a p(a)e^{\beta U(w,a)}$$.  
The solutions can be obtained from arbitrary initializations by iterating the two equations until convergence - this scheme is known in information theory as the Blahut-Arimoto algorithm and is guaranteed to converge to the correct solution.


### Abstractions and lossy compression 
Perhaps surprisingly, the optimization problem presented above is mathematically equivalent to the optimization problem in **rate-distortion theory**, the information-theoretic framework for *lossy compression*. In rate-distortion theory, the goal is to transmit information over a channel of insufficient capacity in order to minimize a distortion function (equivalent to maximizing a utility function). Since the channel capacity is insufficient, some information must be discarded. Rate-distortion theory formalizes how to discard irrelevant information and transmit relevant information in order to minimze distortion as far as possible.  
In the principle for bounded rational decision-making, the goal is very similiar: information about $$w$$ must be processed in order to pick a good action $$a$$. Since the agent has limited computational capacity and cannot process $$w$$ fully, it should process the most relevant information about $$w$$ in order to maximize utility. Thus the problems of optimal lossy compression and optimal bounded rational decision-making are not only mathematically strongly related but also conceptually. 

Interestingly, the rate-distortion principle for bounded rational decision-making leads to the emergence of natural abstractions: in order to keep the mutual information between world-states and actions low, the decision-maker cannot afford to pick actions that are very specific (and thus informative) about a world-state. Rather, the decision-maker favors actions that are "good" under a number of world-states, thus treating several world-states as if they were the same (by responding to all of them with the same policy). This leads to the emergence of abstractions where certain different $$w$$ are treated as if they were the same. Importantly, the abstractions emerge from the structure of the utility function and their granularity is driven by the computational resources of the agent (governed by the inverse tempereature $$\beta$$). 


##### Further reading
An intuitive example for the emergence of abstractions and a more in-depth discussion can be found in [this paper]({{ site.url }}/Paper-AbstractionsHierarchiesOptimalityPrinciple/). The paper contains an example - showing how different natural levels of abstraction emerge, depending on $$\beta$$ - in the form of a [Jupyter notebook](https://github.com/tgenewein/BoundedRationalityAbstractionAndHierarchicalDecisionMaking/blob/master/NotebooksAndCode/2-RateDistortionForDecisionMaking.ipynb) (use [this link](http://nbviewer.jupyter.org/github/tgenewein/BoundedRationalityAbstractionAndHierarchicalDecisionMaking/blob/master/NotebooksAndCode/2-RateDistortionForDecisionMaking.ipynb) if you simply want to view the notebook in your browser).   
