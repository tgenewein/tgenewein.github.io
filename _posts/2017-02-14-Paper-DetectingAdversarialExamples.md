---
layout: post
title:  "Paper accepted: On Detecting Adversarial Perturbations"
date:   2017-02-14 15:00:00
publication: true
pubtype: "paper"
publink: "https://arxiv.org/abs/1702.04267"
downloadlink: "https://arxiv.org/pdf/1702.04267.pdf"
pubtitle: "On Detecting Adversarial Perturbations"
citeas: "Metzen JH, Genewein T, Fischer V, Bischoff B (2017). On Detecting Adversarial Perturbations. International Conference on Learning Representation (ICLR) 2017."
excerpt: "Metzen JH, Genewein T, Fischer V, Bischoff B (2017). On Detecting Adversarial Perturbations."
tags: [publication, paper, deep learning, adversarial examples]
---

Our paper on detecting adversarial perturbations has been accepted for publication at this year's ICLR. In the paper we explore the possibility to train a reliable detector for discriminating whether an image is perturbed by adversarial noise or not. Since adversarial perturbations are characterized by being quasi-imperceptible to humans, it is not clear a priori whether a detector can be found to reliably distinguish between genuine inputs and adversarial examples. We found that a deep neural network can be successfully trained to detect adversarial perturbations in a classification task (CIFAR-10, Imagenet).  
In the paper, we explored different "depths of attachement" of the detector-network to the clasifier-network. Additionally, we looked into how well detector networks generalize across different adversarial attack methods. Finally, we tested whether an attacker with access to both, the classifier and the detector, could construct adversarial perturbations that fool both systems. We found this to be the case. We show that training with adversarial examples that are generated dynamically during training allows to harden against these attacks. While we cannot create a classifier/detector pair that successfully detects $100\%$ of adversarial examples, we can show that it is possible to train good adversarial detectors that generalize to some degree across attack methods. These results indicate that adversarial attacks might also be characterized by certain regularities or structure which clearly separates adversarial examples from genuine data. Understanding these regularities might provide some insights into the nature of adversarial examples.