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
Bounded rationality in two sentences (utility, in general not feasible to search through set of all actions, solution: satisficing)

Hierarchical models play a central role for information-efficient inference and decision-making. In my research I am investigating the theoretical foundations of information-optimal hierarchies for bounded rational inference and decision-making. Re-usable knowledge is abstract knowledge.

Bounded rationality, information theory of decision-making, foundations of computation, hierarchies of abstraction
Related topics are structure learning, lossy compression, Bayesian probability theory and computational neuroscience.


 * What is bounded rationality?
   * Information theory and bounded rational decision-making
   * Hierarchies of abstraction emerge as a consequence of bounded rationality
 * Sensing for acting (likelihood function synthetization) (coming soon)
 * Distributed information processing through hierarchies
   * What is the benefit of hierarchical models?
   * An objective for information-optimal hierarchical models (coming soon)

 * Virtual reality experiments
   * Structure learning
   * Bayesian model selection 

## More details
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

## Links to more special topics
**Topics**  

* [Bounded rationality]({{ site.url }}/research/boundedrationality/)
* Rate distortion decision-making
* Hierarchies of abstraction
* Sensorimotor experiments in virtual reality
