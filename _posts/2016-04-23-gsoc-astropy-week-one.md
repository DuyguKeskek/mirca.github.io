---
layout: post
title: Google Summer of Code 2016: Challenge Accepted!!!
excerpt: "I'm very glad to say that I have been selected by the Astropy project..."
modified: 2016-04-23
tags: [intro, beginner, jekyll, tutorial]
comments: true
image:
  feature: gsoc_post.jpg
  credit: Hubble Space Telescope
---
<p style='text-align: justify;'>
I'm very glad to say that I have been selected by the Astropy project to participate in the Google Summer of Code 2016!!
</p>

<p style='text-align: justify;'>
Frankly, this acceptance felt kind of a result of small steps that I have been taken in the past years... Many thanks goes surely to Marcelo Davanco, Moritz Gunther, and to the astropy development community ;-)
</p>

<p style='text-align: justify;'>
Well, during the GSoC (and after, for sure) I'm going to work for an Astropy affiliated package called <b>photutils</b>, which, among several other things, provides a set of tools for performing general photometry of astronomical sources.
</p>

<p style='text-align: justify;'>
Fundamentally, my task will be to develop code for Point Spread Function (PSF) photometry of overlapped sources. There are several scenarios for which one would choose PSF photometry instead of Aperture photometry. Basically, Aperture photometry assumes that the background varies in a linear fashion in the aperture’s vicinity. However, in a dense star cluster the background is usually nonlinear. Therefore, one may use PSF photometry in order to meaningfully measure the brightnesses of the sources. In PSF photometry, a single model is fitted to each object allowing one to determine, with subpixel precision, their position, amplitude, and width.
</p>

<p style='text-align: justify;'>
In summary, my primary task is to work on developing an algorithm to localize, fit, and perform photometry of several overlapping objects (e.g. a dense star cluster, globular clusters, etc) simultaneously.
</p>

<p style='text-align: justify;'>
<i>Now... to work! :)</i>
</p>
