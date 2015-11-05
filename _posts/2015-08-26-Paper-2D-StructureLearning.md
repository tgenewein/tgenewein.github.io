---
layout: post
title:  "Paper published: structure learning in Bayesian sensorimotor integration."
date:   2015-08-26 14:31:51
publication: true
pubtype: "paper"
publink: "http://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1004369"
downloadlink: "http://www.ploscompbiol.org/article/fetchObject.action?uri=info:doi/10.1371/journal.pcbi.1004369&representation=PDF"
pubtitle: "Structure Learning in Bayesian Sensorimotor Integration"
doi: "10.1371/journal.pcbi.1004369"
citeas: "Genewein T, Hez E, Razzaghpanah Z, Braun DA (2015) Structure Learning in Bayesian Sensorimotor Integration. PLoS Comput Biol 11(8): e1004369. doi: 10.1371/journal.pcbi.1004369"
excerpt: "Genewein T, Hez E, Razzaghpanah Z, Braun DA (2015) Structure Learning in Bayesian Sensorimotor Integration."
tags: [publication, paper, structure learning, sensorimotor integration, virtual reality experiment]
---
{% include _toc.html %}

Our paper on structure learning in Bayesian sensorimotor integration got published in PLoS Computational Biology. In the experiment we showed that humans are able to extract higher-level statistical invariants in a sensorimotor task. Additionally we showed how a hierarchical Bayesian model could explain human behavior in the task (including extraction of statistical invariants).

## What is structure learning?
Humans do extraordinarily well at extracting re-usable knowledge when learning a concrete motor task. For instance, when learning how to ride a mountain bike, humans can easily learn how to ride a different type of bike (e.b. a racing bike). The idea is that both tasks share some common structure, that is higher-level statistical invariants and that humans can extract these invariants and use them to quickly adapt to novel but similar tasks ("*learning to learn*"). This poses the question of how to separate knowledge into a concrete, task-specific and a more abstract, invariant part. One approach to tackle this problem is by using hierarchical Bayesian models, where the higher-level statistical invariants are captured in the upper levels of the hierarchical model (typically through distributions over the parameters of the prior, so called hyper-priors, that are shared across tasks). Adapting to novel tasks but also inferring the parameters of the hyper-prior can then be performed with (hierarchical) Bayesian inference. For more on this see for instance [Learning overhypotheses with hierarchical Bayesian models](http://dx.doi.org/10.1111/j.1467-7687.2007.00585.x), Kemp, Perfors, Tenenbaum (2007) Developmental Science.

## Experimental study
In our experiment we investigate structure learning, that is the extraction of higher-level statistical invariants, in a sensorimotor task. We used our 3D virtual reality setup to design a reaching task with a visuomotor shift. This means that participants had to reach from a start-point to a target using a virtual cursor. Crucially, the cursor did not represent their hand-position veridically but could be shifted horizontally and vertically (the reaching movement was orthogonal to the horizontal-vertical plane). This shift was drawn from a 2D Gaussian distribution in each trial. Participants would not see their virtual hand-position represented by the cursor during the movement but halfway through the movement they would receive brief visual feedback about the cursor position. This feedback can be combined with the experience from the previous trials (the learned prior) in order to initiate a corrective movement in order to hit the target. It has been shown previously that in such a task humans integrate prior knowledge with uncertain feedback information in a way that is quantitatively consistent with Bayesian inference ([Bayesian integration in sensorimotor learning](http://dx.doi.org/10.1038/nature02169), Koerding, Wolpert (2004) Nature) - that is weighting the two sources of information according to their reliability.  
In our task there were four types of visual feedback

 * **Full feedback**: precise feedback about the position of the (shifted) cursor - allows for precise corrections in order to hit the target without requiring knowledge about the prior-distribution over shifts.
 * **Partial horizontal feedback**: A "vertical bar" like stimulus that gives precise feedback about the horizontal dimension but no feedback about the vertical dimension.
 * **Partial vertical feedback**: A "horizontal bar" like stimulus that gives precise feedback about the vertical dimension but no feedback about the horizontal dimension.
 * **No feedback**: no visual feedback is provided an the reaching movement completely relies on the knowledge about previous shifts (the prior).

The two dimensional prior distribution over the shifts (the prior) allowed us to introduce non-trivial statistical structure between the two dimensions of the shift - structure that the participants could learn as higher-order invariants. In our experiment we tested two groups of participants, each with a different prior over the shifts (that stayed constant throughout the experiment)

* **Uncorrelated group**: no correlation between the two dimensions of the shift. In partial feedback trials participants must rely on their knowledge about previous trials for movement correction in the uninformative feedback dimension (e.g. for the vertical bar feedback, participants did not get any information about the vertical dimension of the shift and had to use their learned prior for this dimension).
* **Correlated group**: full correlation between the horizontal and vertical dimension of the shift. If participants had learned the correlation structure of the prior then receiving partial feedback about one dimension of the shift provides knowledge about both dimensions of the shift (since they are correlated), allowing participants to hit the target precisely.

The prediction is thus that participants of the correlated and uncorrelated group should behave differently in partial feedback trials. In particular, if the correlated group is able to learn the structure of the prior, they should be able to hit the target with more precision in the partial feedback trials compared to the uncorrelated group.  
We were able to confirm this prediction in the experiment. Additionally we found that learning of the mean of the prior over shifts was quite fast and robust across participants whereas learning of the correlation structure required a lot more trials and even after 4000 trials learning hat not yet flattened out.


## Modeling with a HBM
To model participants' behavior in the task we used a hierarchical Bayesian model (HBM) where we assumed a Gaussian prior distribution over the shifts with unknown parameters (the mean and covariance matrix). We placed a distribution over the parameters of the prior - the so-called hyper-prior - which was a normal inverse Wishart distribution (the conjugate prior for Gaussians with unknown mean and covariance). This allowed us to derive an online update rule for to infer the parameters of the hyper-prior. We trained the HBM on the same data that the participants were exposed to and found that by placing a strong prior-belief over uncorrelated covariance-matrices we could replicate the timescales of learning the correlation structure with the HBM. Similarly, the HBM could learn the correct mean of the prior and could be used to produce responses in each trial that are statistically similar to human behavior. Importantly, when the HBM was trained with uncorrelated shifts (and keeping all other parameters the same), we could also replicate human behavior in the uncorrlated group.
