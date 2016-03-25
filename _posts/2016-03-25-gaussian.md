---
layout: post
title: Is any data sample Gaussian distributed?
excerpt: "Why you can't, sometimes, assume Gaussianity of your data..."
modified: 2016-04-06
tags: [intro, beginner, jekyll, tutorial]
comments: true
image:
  feature: gsoc_post.jpg
  credit: Hubble Space Telescope
---
This post is the first of a series of in which I will give some practical examples in which statistics (i. e., any function of the data) will perform poor if the data sample is assumed to be Gaussian distributed.

People usually tend to assume (a little is actually verified) that their data samples are Gaussian distributed. The Central Limit Theorem proves that, in fact, this is true provided *some* conditions.

With the Gaussian assumption comes several goodies, e.g., the density is smooth everywhere, the likelihood is easy to write analytically and to compute, the maximum likelihood estimator coincides with the classical least squares estimator, which one can use to fit any model to the data, and so on... (Perhaps the least squares is the most used objective function ever).
