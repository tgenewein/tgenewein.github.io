---
layout: post
title:  "Embedding Juyter code in a website with Thebe"
date:   2016-01-30 15:00:00
publication: false
excerpt: "This blog post shows how to embed an interactive code-widget in a website that connects to a Jupyter kernel on another server using Thebe."
tags: [Jupyter, Thebe, IPython, Julia, reproducible code, reproducible science, interactive code]
---

Essentially, Thebe is a minimal frontend that replaces a Juyter notebook and connects to a Jupyter kernel.

Syntax-highlighting, connecting to a local kernel, connecting to a remote kernel (tmpnb.org)

Ideally, get the Julia-set example going - you might have to use Gadfly to do so... (and use a slider as well if you can?)

Future posts - setting up your own notebook server on AWS/Google using docker images.

Future future, using docker images to publish reproducible code (publish a docker image along your code)

Future future future - connecting it all: running the published docker image on your own server and connect to it from an embedded Thebe widget.

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
