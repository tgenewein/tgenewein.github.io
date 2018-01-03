---
layout: post
title:  "Talk @ Amlab Amsterdam: Information-optimal coupling of perception and action through lossy compression"
date:   2017-06-01 15:00:00
publication: true
pubtype: "talk"
#publink: ""
downloadlink: "/files/publications/talks/2017_06_Amlab_Perception_Action_Coupling.pdf"
pubtitle: "Information-optimal coupling of perception and action through lossy compression"
citeas: "Genewein T (2017) Information-optimal coupling of perception and action through lossy compression"
excerpt: "Talk at Amlab (Max Welling) / UvA-Bosch Delta Lab (Zeynep Akata) on Information-optimal coupling of perception and action through lossy compression."
tags: [publication, talk, abstractions, bounded rationality, decision-making, rate distortion, perception-action, likelihood synthetization]
---
As part of the collaboration between Bosch Center for AI and Max Welling's Amlab, or more precisely [UvA-Bosch Delta Lab](https://ivi.fnwi.uva.nl/uvaboschdeltalab/) headed by Zeynep Akata, I visited UvA for a couple of days and also gave a talk (see abstract below). I was very impressed with the lab and had quite a few very interesting discussions that need to be followed up on. I find it remarkable how world-class labs have this very particular feel to them - it's very hard to nail down which factors precisely are different compared to many other labs. Yet, the atmosphere instantly reminded me a lot of the MPI Tuebingen. It guess it's mostly about the people and the discussion culture - everybody is really clever and has very convincing arguments why their approach/idea is really good, at the same time everybody is very open to hear about and critically reflect on other's ideas. It was a great visit - the campus is really nice as well and Amsterdam is certainly worth spending some time.

Here's the abstract of my talk, find out more about the topics on the [Research](/research/) pages or alternatively [this paper](/Paper-AbstractionsHierarchiesOptimalityPrinciple/)):


Perception is processing of sensory information into useful representations (percepts or features) for acting. It is common practice in many application-domains, such as robotics or autonomous driving, to treat perception (e.g. computer vision) and action (e.g. planning or control) as more or less separate problems. In such cases, the perceptual representation is typically manually designed, e.g. a semantic segmentation of the input image. While such a representation might be sufficient for certain tasks, it is rarely optimal, which can lead to poor robustness and even render the learning problem for the action stage of the system more difficult than necessary (since the action stage needs to learn to ignore irrelevant information captured by the perceptual representation). This talk presents an optimality principle for coupling a perceptual stage that feeds into an action stage. The resulting objective function can be derived from well-known optimality principles (Bayesian inference, free-energy minimization and rate-distortion theory). As a result, the perceptual stage is formalized as a lossy compressor. The analytical solution to the optimality principle exhibits interesting theoretical properties - in particular the corresponding perceptual representations can be shown to (1) capture a lot of (task-) relevant information with (2) little redundancy, while (3) being robust to (task-) irrelevant variation. Another result is that the implicit objective of the perceptual stage is to enable the downstream action stage to operate most efficiently (i.e. with maximal free energy).