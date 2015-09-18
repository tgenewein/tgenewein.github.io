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

**TODO: all of this is just dummy-text, final page TBD**

## Research interest
I am interested in building intelligent machines. One of the most important steps towards that goal is to understand how large-scale computational problems can be tackled with limited resources.
Hierarchical models play a central role in information-efficient inference and decision-making. In my research I am investigating the theoretical foundations of information-optimal hierarchies for bounded rational inference and decision-making.  
Additionally, I try to understand how the human brain can do so extraordinarily well with very little computational resources through virtual reality experiments with human participants.

Bounded rationality, information theory of decision-making, foundations of computation, hierarchies of abstraction

## More details
Just testing equations $$\beta = 5$$.

$$ \alpha_i = \Delta F $$

## Links to more special topics
**Topics**  

* [Bounded rationality]({{ site.url }}/research/boundedrationality/)
* Rate distortion decision-making
* Hierarchies of abstraction
* Sensorimotor experiments in virtual reality
