---
layout: post
title: Google Summer of Code 2016
excerpt: "This year I'm applying to the Google Summer of code under the Astropy community"
modified: 2016-04-06
tags: [intro, beginner, jekyll, tutorial]
comments: true
image:
  feature: gsoc_post.jpg
  credit: Hubble Space Telescope
---
<p style='text-align: justify;'>
This year I'm applying to the Google Summer of Code under the Astropy community. I'm in the process of preparing my proposal, and potential mentors are actually taking a look at it.
</p>

<p style='text-align: justify;'>
Primarily, my proposal concerns the problem of fitting point spread functions (PSF) to crowded fields (i. e., a image with a high density of sources so that many of them overlap with each other).
</p>

<p style='text-align: justify;'>
Honestly, I feel very confortable on working on this, since I have a prior experience with a very similar problem. In fact, at NIST (Marcelo's research group) I mainly worked writing MATLAB code for PSF fitting of single molecules.
</p>

<p style='text-align: justify;'>
As an example, see the figure below. It shows a lot of nanoemitters and their center positions (red marks) which were estimated using the maximum likelihood estimator (Poisson data + Poisson background).
</p>
<img src="..\images\emccd.png" style="width:256px;height:256px;">

<p style='text-align: justify;'>
Once one has fitted the PSF models to the nanoemitters data, all the remains is extract useful information from the sources (e. g., flux).
</p>

<p style='text-align: justify;'>
However, imagine that the sources are so closed that their flux "overlap", i. e., one does not have a disjoint set of sources anymore. How many sources are in a given subregion? "N"? What is the probability that one has that many sources? How to extract flux from each source? What are the widths of each source? What are their central positions?
</p>

<p style='text-align: justify;'>
I'd love to look for answers of these questions during GSoC 2016 :). As always, I will do my best to get it! Hope everything goes alright.
</p>

