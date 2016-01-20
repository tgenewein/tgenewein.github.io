---
layout: page
title: Distribution of information processing - hierarchical information processing
share: false
researchtopicpage: true
shorttitle: Hierarchical computation # for display in the sidebar menu
# date: 2016-01-16 13:53:00
permalink: /research/distributedinformationprocessing/
---

{% include _toc.html %}

This article extends the rate-distortion principle for bounded rational decision-making presented in [this research article]({{ site.url }}/research/naturalabstractions/), make sure to read it first if you're unfamiliar with the information-theoretic framework for bounded rationality.

In this article, the information-theoretic framework for bounded rationality is used to model distributed information processing, where the total information processing load is split up onto two processing stages. These two stages can be interpreted as two levels of an information processing hierarchy, where the high-level decision narrows down the search space for the low-level decision.


### Processing information for acting
In the [rate-distortion case]({{ site.url }}/research/naturalabstractions/), a bounded-rational decision maker is presented with world-states $$w$$ and computes actions $$a$$ (or a posterior policy $$p(a \vert w)$$) in order to maximize the (expected) utility $$U(w,a)$$. The computational resources of the agent are bounded by an upper limit on the mutual information:

$$
I(W;A) \leq K
$$

In the [serial action-perception case]({{ site.url }}/research/sensingforacting/), the basic setup is extended by a perceptual variable $$X$$, which leads to a serial chain of two processing stages: a perceptual stage and an action-stage. However, in this setup, the overall information processed is upper-bounded by the capacity of either stage, meaning that the overall information processed cannot be larger than either of the information throughputs of the two serial stages:

$$
I(W;A) \leq \text{min} \lbrace I(W;X), I(X;A) \rbrace 
$$ 

or in other words: if all we care about is maximizing utility, then the serial case requires to pay twice for (at least) the same amount of information processing compared to the rate-distortion case. 

### Distribution of information processing
The goal here is to split the total information processing load onto several elements of limited capacity such that in the end the information processed is larger than the information processed by each element (or processing stage). The approach taken here also introduces an "intermediate" random variable $$M$$, but in contrast to the serial case, the joint-distribution factorizes as follows:

$$
p(w,m,a)=p(w)p(m|w)p(a|w,m)
$$

This opens up the possibility for a distribution of information processing load on two stages, a high-level and a low-level stage:

$$
\underbrace{I(W,M;A)}_{\text{total processing}} = \underbrace{I(W;X)}_{\text{high-level}} + \underbrace{I(W;A|M)}_{\text{low-level}} 
$$

The reason why the first stage is referred to as "high-level" is because it corresponds to a high-level decision that narrows down the search space over actions for the low-level decision of the second stage (more on this further below).  
Crucially, the distribution of information processing also holds when considering the mutual information between $$W$$ and $$A$$, which is the amount of information processing that effectively contributes towards maximizing expected utility:

$$
I(W;A) \leq  \text{min} \lbrace I(W;M), I(M;A) \rbrace + I(W;A|M)
$$


### Hierarchical decision-making: introducing models
In the following we refer to the variable $$M$$ as the *model* and use it to induce (prior) distributions over the action $$A$$ according to $$p(a \vert m)$$. The (low-level) decision-maker uses these prior distributions in addition with information about $$w$$ to compute a (bounded) optimal response $$a$$. Each model can reduce the effective search-space over actions - the difficulty then lies in choosing the correct model, given a world-state $$w$$, but also in finding good distributions $$p(a \vert m)$$. The following three components must be specified:

$$
\begin{align}
\text{Model selector:}&~~~~~~~~p(m|w)\\
\text{Model priors:}&~~~~~~~~p(a|m)\\
\text{Low-level decision-maker:}&~~~~~~~~p(a|w,m)
\end{align}
$$

The low-level decision-maker uses the distribution induced by the model as a prior and computes an optimal action in a bounded rational fashion. Following the [information-theoretic principle for bounded rationality]({{ site.url }}/research/naturalabstractions/), the low-level stage can easily be written down as:

$$
p(a|w,m) = \frac{1}{Z}p(a|m)e^{\beta_2 U(w,a)}
$$

The design of the model-selector $$p(m \vert w)$$ and good model priors $$p(a \vert m)$$ is crucial for the efficiency of the whole system and is in general a non-trivial task. In the section below it is shown how the consequent application of trading off expected utility against computational cost leads to a well-defined, bounded-optimal solution for both problems.  
Note that the model-selector can be considered as another, high-level, decision-maker that narrows down the search-space for the low-level decision-maker - the overall system can thus be considered a simple two-level decision-making hierarchy.

### Information-theoretic bounded rationality
Consequent application of the information-theoretic framework for bounded rationality implies that the expected utility must be traded off against the cost of computation - in this case, computation is required to determine the correct model and another computational step is required to find an action given the prior induced by the model. Formally, the following optimization problem needs to be solved:

$$ 
\begin{align}
p^*(m|w), p^*(a|w,m) = \underset{p(m|w), p(a|w,m)}{\text{arg max}} &\sum_{w,m,a} p(w) p(m|w) p(a|w,m) U(w,a)\\
 &- \frac{1}{\beta_1} I(W;M) - \frac{1}{\beta_2} I(W;A|M)
\end{align}
$$


### Bounded-optimal solution
The objective above, can be solved in closed-form, leading to a set of self-consistent equations:

$$
\begin{align}
p^*(m|w)&=\frac{1}{Z_m}p(m)e^{\beta_1 \Delta F(w,x)}\\
p^*(a|m)&=\sum_w p(w|m)p^*(a|m,w)\\
p^*(a|w,m)&=\frac{1}{Z_a}p(a|m)e^{\beta_2 U(w,a)}
\end{align}
$$

where $$p(w \vert m)$$ is given by Bayes' rule $$p(w \vert m)=\frac{1}{p(w)}p^*(m \vert w)p(m)$$.  
$$\Delta F(w,x)$$ is the free energy of the low-level stage

$$
\Delta F(w,x)=\sum_a p^*(a|w,m) U(w,a) - \frac{1}{\beta_2} D_{\text{KL}}(p^*(a|w,m)||p(a|m))
$$

and acts as a utility for the high-level stage, that is the high-level stage maximizes the free energy trade-off of the low-level stage in a bounded rational fashion. Additionally, $$p(m)=\sum_w p(w)p^*(m \vert w)$$.

### Information-optimal hierarchies
The solution to the optimization problem fully specifies all three components of the two-level hierarchy:

*  a model selector $$p^*(m \vert w)$$
*  model priors $$p^*(a \vert m)$$
*  the low-level decision-maker $$p^*(a \vert w,m)$$

Note that the bounded-optimal low-level decision-maker turns out to be exactly the one that was intuitively motivated earlier (in the paragraph where the model variable was introduced).

Also note that the structure of the hierarchy is governed entirely by the utility-function, the distribution over world-states $$p(w)$$ and the computational limitations of the two stages (controlled by $$\beta_1, \beta_2$$ ). 

##### Further reading (recommended)

To fully understand the resulting hierarchical model, please refer to the more detailed discussion in [this paper]({{ site.url }}/Paper-AbstractionsHierarchiesOptimalityPrinciple/) - it explains why the inverse temperatures must be set in a particular way ($$\beta_1 > \beta_2$$), why it makes sense to limit the cardinality of $$M$$ and why this will lead to the most re-usable and thus most abstract information processing happening in the high level of the hierarchy (thus leading to a hierarchy of abstractions).  
Additionally the paper illustrates the bounded-optimal hierarchy with an intuitive example, which can also be found in [this Jupyter notebook](https://github.com/tgenewein/BoundedRationalityAbstractionAndHierarchicalDecisionMaking/blob/master/NotebooksAndCode/4-ParallelHierarchy.ipynb) (or alternatively can be viewed in the browser [here](http://nbviewer.jupyter.org/github/tgenewein/BoundedRationalityAbstractionAndHierarchicalDecisionMaking/blob/master/NotebooksAndCode/4-ParallelHierarchy.ipynb)).