---
layout: page
title: Bounded rational decision making
share: false
researchtopicpage: true
shorttitle: Bounded rationality # for display in the sidebar menu
# date: 2015-09-09 13:53:00
permalink: /research/boundedrationality/
---

{% include _toc.html %}

In a nutshell, bounded rational decision-making is about finding optimal actions under restricted computational resources. One of the main difficulties is finding good (mathematical) formalizations of the notion of computational resources. Most proposed solutions to model bounded rationality fall into one of two categories:

  *  **meta-reasoning**: the decision-maker reasons about its computational limitations and adjusts its decision-making strategy accordingly. One problem is that meta-resoning is also subject to the computational limitations of the agent which would require another level of meta-meta-resoning (which is again subject to limitations and thus leads to an infinite depth of meta-levels).
  *  **implicit boundedness**: the decision-maker does not reason about its computational limitations and acts according to some internal principle - the limitations only become apparent from an external point-of-view. Approximate computation schemes and heuristics fall into this category.

The information-theoretic framework for bounded rationality presented here also falls in the latter category. The appeal of this particular framework is that it provides a solid theory grounded on first principles (with explicit assumptions) that explicitly quantifies the *cost of computation*.   

### Optimal decision-making and rationality
In classical decision-making with context, a utility function $$U(w,a)$$ is given and the decision-maker is faced with the task of finding an optimal action $$a^+$$ in response to the context (or world-state) $$w$$:

$$
a^+ = \underset{a}{\text{arg max}}~U(a,w).
$$

An decision-maker following this strategy is referred to as a *rational* agent. 

### The problem with rational decision-making
Finding the optimal action $$a^+$$ boils down to evaluating the utility-function for every possible action and picking the action that yields maximum utility... which is exactly the problem: for an agent with limited computational resources it can easily become computationally infeasible to evaluate the utility function for every possible action $$a$$. Consider for instance a soccer playing humanoid robot that has to react within a narrow time-limit to an incoming pass - even with current state-of-the-art hardware it would be impossible to go through all possible movement-trajectories within a few hundred milliseconds (yet humans can solve such a problem easily). 

In so-called *needle-in-a-haystack* problems where only one action is valid and all other actions are invalid, there is no way to alleviate the search-problem for the optimal action. However, in many practical scenarios there are several actions that yield a "good" utility-value given the current context $$w$$ (again, think of the soccer playing robot: there will possibly be many different movements that are satisfying, not necessarily optimal but also not far from the optimum in terms of utility). The idea behind bounded rationality is finding the best solution among all solutions that **are computable** within the limitations of the agent because ultimately the bounded agent cannot do better than that. The problem is how to properly formalize this idea. There have been many attempts to wrap the idea of bounded rationality into a nice computational framework: e.g. meta-reasoning schemes, approximation-schemes or heuristics. The next section introduces a computational framework for bounded rationality that is very explicit about the underlying assumptions and grounded on first principles.

### An information-theoretic framework for decision-making
Goal: design an agent that finds the best action $$a^*$$ (in terms of utility-value) among the set of actions that the agent can afford to evaluate. To do so, the agent must follow some search strategy through action-space. In the information-theoretic framework for bounded rationality, this search strategy is explicitly specified as (the prior) $$p_0(a)$$. The resulting optimal strategy is stochastic and is formalized as (the posterior) $$p^*(a|w)$$. The agent has to invest computation in order to transform the prior- into the posterior-policy. In exchange for the computation, the agent's goal is to receive a higher expected utility $$\sum_a p(a|w)U(w,a)$$. The amount of computation (in bits or nats) is given by the Kullback-Leibler divergence between prior and posterior and for a bounded rational agent this KL divergence is upper-bounded. This allows to write down the following constrained optimization problem:

$$
p^*(a|w) = \underset{p(a|w)}{\text{arg max}} \sum_a p(a|w) U(w,a)~~\text{subj. to:}~D_{\text{KL}}(p(a|w)||p_0(a)) < K
$$ 

The constrained optimization problem can be transformed into an unconstrained problem

$$
p^*(a|w) = \underset{p(a|w)}{\text{arg max}} \underbrace{\sum_a p(a|w) U(w,a)}_{\text{expected utility}} - \frac{1}{\beta} \underbrace{D_{\text{KL}}(p(a|w)||p_0(a))}_{\text{computational demand}}
$$ 

The unconstrained problem formalizes a fundamental trade-off: maximize expected utility while at the same time keeping the computational demands low. The factor $$\beta$$ translates computational demand (in bits or nats) into a *cost of computation* (in utils) and is referred to as **inverse temperature** (the reason being strong similarities of the optimization problem with a free energy minimization in thermodynamics - see the publication [here]({{ site.url }}/Paper-NIPS-workshop-abstractions/) for a more detailed discussion).

### Solving the optimization problem
The unconstrained optimization problem has a closed-form solution:

$$
p^*(a|w)=\frac{1}{Z}p_0(a)e^{\beta U(w,a)}
$$

where the normalizing constant $$Z=\sum_a p_0(a)e^{\beta U(w,a)}$$ (the partition sum).

The inverse temperature $$\beta$$ acts as a rationality parameter and governs the trade-off between large expected utility and low computational demand.

*  $$\beta \rightarrow 0$$: no computational resources, agent follows prior policy
*  $$\beta \rightarrow \infty$$: unlimited computational resources, (fully rational) agent deterministically picks globally best action $$a^+$$
*  $$0 < \beta < \infty$$: agent trades off expected utility against cost of computation


The solution to the optimization problem can be translated into an elegant sampling scheme, where the agent proposes actions according to $$p_0(a)$$ and then (probabilistically) tests them in a rejection step against a fidelity constraint. Importantly, the fidelity constraint is also governed by $$\beta$$ which thus directly controls the number of samples that the agent can afford (higher $$\beta$$ means more computational resources which means more samples). Informally, the sampling scheme translates into: search through the action space according to $$p_0(a)$$ and accept the first action that satisfies the fidelity constraint. From the agent's internal perspective, there is no notion of computational cost, all that matters is the fidelity constraint - yet, the scheme produces samples from the optimal posterior policy. An explanation of the sampling scheme and a more detailed discussion is found in [this paper]({{ site.url }}/Paper-AbstractionsHierarchiesOptimalityPrinciple/).


### Decision-making and inference
The information-theoretic framework for bounded rationality can be used to tackle both, decision-making but also inference problems. Assume that we use a log-likelihood function as the utility $$U(w,a) = \log q(w|a)$$. Plugging this into the solution of the optimization principle and setting $$\beta=1$$ yields Bayes' rule as a special-case solution:

$$
p^*(a|w)=\frac{p_0(a)e^{\log q(w|a)}}{Z} = \frac{q(w|a)p_0(a)}{\sum_a q(w|a)p_0(a)}
$$


##### Further reading
More on the information-theoretic framework for bounded rationality and it's connection to thermodynamics can be found in [this paper]({{ site.url }}/Paper-AbstractionsHierarchiesOptimalityPrinciple/).  
The paper also includes an [interactive example](https://github.com/tgenewein/BoundedRationalityAbstractionAndHierarchicalDecisionMaking/blob/master/NotebooksAndCode/1-FreeEnergyForBoundedRationalDecisionMaking.ipynb) (as a Jupyter notebook) - alternatively, use [this link](http://nbviewer.jupyter.org/github/tgenewein/BoundedRationalityAbstractionAndHierarchicalDecisionMaking/blob/master/NotebooksAndCode/1-FreeEnergyForBoundedRationalDecisionMaking.ipynb) for simply viewing the notebook.

Continue with the next research article on [natural abstractions]({{ site.url }}/research/naturalabstractions/), where the basic principle is extended to find the optimal prior $$p_0(a)$$. This extension of the principle can lead to the emergence of natural abstractions in the bounded-optimal solution.
