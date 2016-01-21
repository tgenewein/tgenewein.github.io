---
layout: researchpage
title: Research
share: false
excerpt: "Overview of my research-topics"
# date: 2015-09-09 13:53:00
permalink: /research/
---

<section id="table-of-contents" class="toc">
  <header>
    <h3><i class="fa fa-fw fa-flask"></i> Research topics</h3>
  </header>
  <div id="drawer" markdown="0">
    <ul>
      {% for page in site.pages %}
        {% if page.researchtopicpage == true %}
          {% if page.shorttitle %}
            <li><a href="{{ site.url }}{{ page.url }}"><i class="fa fa-fw fa-caret-right"></i> {{ page.shorttitle }}</a></li>
          {% else %}
            <li><a href="{{ site.url }}{{ page.url }}"><i class="fa fa-fw fa-caret-right"></i> {{ page.title }}</a></li>
          {% endif %}
        {% endif %}
      {% endfor %}
    </ul>
  </div>
</section><!-- /#table-of-contents -->

I am interested in understanding intelligence and I am interested in building intelligent machines. Biological brains do very well at leveraging the rich structure of natural environments to extract re-usable knowledge and apply it to similar but not identical situations. This re-usable knowledge helps to speed up learning of similar tasks and allows for performing well with less computation. Producing re-usable, transferable knowledge while learning a specific task is a big unsolved challenge for artificial systems. It is perhaps the main challenge that prevents todays robots from "leaving the lab" - specific tasks can be learned very well, but even slight task variations often require complete re-learning. Humans and animals are extraordinarily good at structure learning despite having limited computational resources. I believe that it is exactly these limits in computational capacity that drive structure learning, because re-usable knowledge reduces computational demands.  

My research is focused on understanding how structure learning can be framed as a consequence of having limited computational capacity. I investigate links between a thermodynamic framework for bounded rational decision-making and rate distortion theory (the information-theoretic framework for lossy compression). Building upon these links, I am working on a theoretical framework for information-optimal hierarchical models for bounded rational inference and decision-making.  

Additionally, I use virtual reality experiments to shed some light on how the human brain performs structure learning and structure selection. 

Find out more about the topics involved in the research articles below or in the side-bar menu of the page.

---

**Bounded rationality, abstractions and hierarchical decision-making**:  
(the last two articles build upon the first two articles, make sure to read these first)

* [Bounded rational decision-making]({{ site.url }}/research/boundedrationality/)
  *  the problem with utility maximization
  *  trading-off utility against cost of computation
* [Information-theoretic bounded rationality]({{site.url}}/research/naturalabstractions/)
  *  lossy compression and decision-making
  *  emergence of natural abstractions
* [Sensing for acting]({{ site.url }}/research/sensingforacting/)
  *  a bounded-rational perception-action system
  *  perception is different from plain inference
  *  likelihood function synthetization
* [Distributed information processing through hierarchies]({{ site.url }}/research/distributedinformationprocessing)
  *  splitting up computational load onto several processing elements
  *  hierarchical decision-making

---

**Virtual reality experiments**:

* [Structure learning]({{ site.url }}/research/structurelearningexperiments/)
  *  extracting high-level statistical invariants
  *  sensorimotor task in virtual reality
* [Bayesian model selection]({{ site.url }}/research/modelselectionexperiments/)
  *  integrating out the parameters
  *  preference of simpler hypotheses - Bayesian Occam's razor

