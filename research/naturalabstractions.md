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

Coming soon - for now, have a look [here]({{ site.url }}/Paper-AbstractionsHierarchiesOptimalityPrinciple/)


This article builds on the research article [bounded rationality]({{ site.url }}/research/boundedrationality/), which provides a basic introduction to bounded rationality and the information-theoretic framework for bounded rational decision making and inference.

--- draft content below ---

short summary

### The optimal prior
Free-energy framework (from before) is bounded optimal decision-making. Priors are assumed to be given - corresponds to a one-shot decision. If same world-state is encountered over and over again it makes sense to adjust the prior in order to minimize computational cost (=learning?). The basic optimization problem can be extended by taking an average over w and optimizing over the prior as well.

The solution for the prior can be written down in closed form. This leads to a trade-off between large expected utility and low mutual information - the same trade-off as in rate-distortion theory.

### Abstractions and lossy compression 
Forming abstractions and lossy compression are essentially the same problem of discarding irrelevant information and keeping only (a limited amount of) relevant information.

Keeping mutual information low is achieved by finding actions that are good for many world-states, i.e. treating several w as if they were the same (a decision-making abstraction). Inverse temperature governs the granularity of or level of the abstraction.

Abstractions emerge from the structure of the utility function and the computational limitations - emergence of natural abstractions.

### Example
Show the example of natural abstractions from the paper (or perhaps the animal/plant taxonomy?)
