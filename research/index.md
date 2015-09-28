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

I am interested in building intelligent machines. Biological brains do very well at leveraging the rich structure of natural environments to extract re-usable knowledge. This knowledge helps to speed up learning of similar tasks and allows for performing well with less computation. Producing re-usable, transferrable knowledge while learning a specific task is a big unsolved challenge for artificial systems. It is perhaps the main challenge that prevents todays robots from "leaving the lab" - specific tasks can be learnt very well, but even slight task variations often require complete re-learning. Humans and animals are extraordinarily good at structure learning despite having limited computational resources. I believe that it is exactly these limits in computational capacity that drive structure learning, because re-usable knowledge reduces computational demands.  
My research is focused on understanding how structure learning can be framed as a consequence of having limited computational capacity. I investigate links between a thermodynamic framework for bounded rational decision-making and rate distortion theory (the information-theoretic framework for lossy compression). Building upon these links, I am working on a theoretical framework for information-optimal hierarchical models for bounded rational inference and decision-making.  
Additionally, I use virtual reality experiments to shed some light on how the human brain performs structure learning and structure selection.

Find out more about the topics involved (including interactive demos) on the research topics pages (coming soon):


 * Bounded rationality, lossy compression and abstractions
   * What is [bounded rationality]({{ site.url }}/research/boundedrationality/)?
   * Information theory (lossy compression) and bounded rational decision-making
   * Hierarchies of abstraction emerge as a consequence of bounded rationality
 * Information processing hierarchies
   * Sensing for acting (likelihood function synthetization)
   * Distributed information processing through hierarchies
     * What is the benefit of hierarchical models?
     * An objective for information-optimal hierarchical models

 * Virtual reality experiments
   * Structure learning
   * Bayesian model selection 


**--- dummy content below ---**


## Mathjax equations
Just testing equations $$\beta = 5$$.

$$ \alpha_i = \Delta F $$



## Testing a Thebe widget
<pre data-code-language="julia" data-executable='true'>
using Gadfly

plot(x=rand(10), y=rand(10), Geom.point, Geom.smooth)
</pre>

<pre data-code-language="julia" data-executable='true'>
Pkg.add("PyPlot")
using PyPlot  #this is Julia's wrapper around matplotlib (from Python) it behaves very similar to MATLAB

# compute the "speed of divergence" for point c and perturbation z
# the return value is small for perturbations that diverge fast, and large for non-divergent sequences
function julia(z, c; maxiter=200)
    #iterate through the complex quadratic polynomial
    for n = 1:maxiter
        z = z^2 + c         
        #check if sequence has "diverged"
        if abs2(z) > 4
            return n
        end
    end
    return maxiter #sequence has not diverged (yet)
end

#this call produces the Julia set for c=-0.06+0.67im
c = complex(-0.06, 0.67)  #try changing this!

jset = [ julia(complex(r,i), c) for i=1:-.002:-1, r=-1.5:.002:1.5 ]; 

#this time with a different colormap
imshow(jset, cmap="afmhot", extent=[-1.5,1.5,-1,1])
xlabel("Re(z0)")
ylabel("Im(z0)")
title("Julia set (c=$c, complex quadr. pol.)")
</pre>
