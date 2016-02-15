---
layout: post
title:  "Why we need to stop using rainbow colormaps: an interactive example"
date:   2016-02-15 11:00:00
publication: false
excerpt: "Rainbow colormaps distort visualizations of raw data - better alternatives can easily be found and should be used. See here why."
tags: [visualization, jupyter, binder, python, matplotlib, jet]
---

This article contains an accompanying Jupyter notebook, launch it from your browser with this button:  
[![Binder](http://mybinder.org/badge.svg)](http://mybinder.org/repo/tgenewein/StopUsingRainbowColormaps)

---

In the early nineties some software company decided to make a rainbow colormap the default-colormap. Soon others would follow and today data-visualizations are flooded with rainbow colormaps. You can find them in many scientific publications in all kinds of fields of research, but they also appear as default options in commercial software across all kinds of domains. 

People in the late nineties already pointed out that rainbow colormaps are a particularly bad way of visualizing data - despite the shiny and fancy looks. There's a whole bunch of problems associated with rainbow colormaps and the Internet is full of articles, blog-posts and scientific papers, pointing out the flaws and providing better alternatives. For instance, one study found that (future) medical doctors preferred rainbow colormaps for detecting anomalies in some processed imaging data (for detecting coronary artery disease), mostly because they were so used to this particular colormap which has become the de-facto standard in the medical literature. However, the same study found that participants' detection accuracy was increased with a different colormap, even though participants were not particularly used to that colormap (see accompanying Jupyter notebook for a reference to the study).

Meanwhile there are open letters asking scientific communities to abandon the rainbow and journals to start banning its use as it is considered poor visual communication, particularly since better methods a readily available. And indeed, almost all software packages for visualization and scientific computing provide a whole range of colormaps, a lot of which are much more suitable than rainbow colormaps. Despite that, the scientific literature is still flooded with images in rainbow colors. This has to stop.

See the accompanying Jupyter notebook for an interactive example that clearly illustrates the problems with rainbow colormaps (and perceptually non-uniform colormaps). You can also find more information and further reading in the notebook.

The notebook can be run directly in the browser using [binder](http://mybinder.org/), even though its use is still experimental with occasional performance problems (lately a guy published a notebook to play around with the data underlying the recently detected gravitational waves, which is amazing but blew the resources of binder for some time - luckily they have scaled up since then).

Launch the notebook in you browser with the button below:  
[![Binder](http://mybinder.org/badge.svg)](http://mybinder.org/repo/tgenewein/StopUsingRainbowColormaps)

Alternatively find the notebook for viewing or downloading in [my Github repository](https://github.com/tgenewein/StopUsingRainbowColormaps).


An article on how to use binder with a customized docker image (including a Julia environment) will follow soon (link here as soon as article is online). 