---
layout: post
title: "Brief overview of PSF Photometry: Google Summer of Code project for Astropy/Photutils"
excerpt: "I have no idols. I admire work, dedication and competence. (Ayrton Senna)" 
modified: 2016-09-09
tags: [gsoc, astropy, openastronomy]
comments: true
image:
  feature: gsoc_post.jpg
  credit: Hubble Space Telescope
---

<p style='text-align: justify;'>
Hi all!
</p>

<p style='text-align: justify;'>
First things first; the following links point out to the pull requests that I worked on
during the course of my GSoC project:
</p>

<ul>
<li> <a href="https://github.com/astropy/photutils/pull/367">#367: Create PSF subpackage</a></li>
<li> <a href="https://github.com/astropy/photutils/pull/369">#369: Add an implementation of daophot GROUP functionality</a></li>

<li> <a href="https://github.com/astropy/photutils/pull/376">#376: Add a way to get params uncertainties in psf_photometry</a></li>

<li> <a href="https://github.com/astropy/photutils/pull/379">#379: findstars oop interface</a></li>

<li> <a href="https://github.com/astropy/photutils/pull/385">#385: PSF Photometry in Crowded Fields</a></li>

<li> <a href="https://github.com/astropy/photutils/pull/404">#404: [DOC]: Narrative docs for PSF Photometry</a></li>

<li> <a href="https://github.com/astropy/photutils-datasets/pull/5">#5: Notebook for psf-photometry in crowded fields</a></li>

</ul>

<p style='text-align: justify;'>
My project was entitled "Implement Point Spread Function (PSF) photometry for
fitting several overlapping objects at once". The basic question is, given an
astronomical image, "How to estimate the flux and the positions of each star
when there exist overlap between them?".
</p>

<p style='text-align: justify;'>
To make our lives easier, we broke this question in smaller ones, for instance,
"Which stars are overlapping?". To answer this question,
we implemented (<a href="https://github.com/astropy/photutils/pull/369">#369</a>
) the GROUP algorithm proposed by Stetson (1987) which is used
in the IRAF/DAOPHOT software.
</p>

<p style='text-align: justify;'>
It is assumed that the point spread function (which is the optical system's
impulsive response) has a known model with unknown parameters (and we would
like to estimate them). Mathematically, assume that
<img src="../images/final/Theta.png" width="14"> is the parameter space (i.e. the space
of possible values that the parameters can assume).
</p>

<p style='text-align: justify;'>
Usually, the parameters are the center position and the flux of the star.
In this case, <img src="../images/final/Theta.png" width="14"> is reduced to
<img src="../images/final/param_space.png" width="128">. As the parameters are
positive real-valued numbers and if we would like to fit only one star at at time,
then the optmization algorithm will search for solutions over the <img src="../images/final/R_three.png" width="22"> space.
</p>

<p style='text-align: justify;'>
If <img src="../images/final/model.png" width="14"> is the PSF model (for example a
<a href="http://photutils.readthedocs.io/en/latest/api/photutils.psf.IntegratedGaussianPRF.html">Gaussian model</a>), <img src="../images/final/theta_in_Theta.png" width="42">, then
the model for a group of <img src="../images/final/n.png" width="10"> stars is given as
</p>

<center>
<img src="../images/final/sum_model.png" width="200">
</center>

<p style='text-align: justify;'>
Note that, the space of possible solutions is not the positive part of the 3D space anymore, 
it is the positive part of the 3nD space =o
</p>

<p style='text-align: justify;'>
Fortunately, Scipy scientists already implemented awesome optimization algorithms
and some of then are encapsulated in <a href="http://docs.astropy.org/en/stable/_modules/astropy/modeling/fitting.html"> astropy.modeling </a> :)

<p style='text-align: justify;'>
After finding the groups of stars, the algorithm proceeds to fit the stars in
each group simultaneously. Right after fitting a given group, that group is subtracted
from the original image (forming a "residual image").
</p>

<p style='text-align: justify;'>
All these steps are enclosed in <a href="https://github.com/astropy/photutils/pull/385">DAOPhotPSFPhotometry</a> class, which is the main contribution of my project GSoC project.
</p>

<p style='text-align: justify;'>
In addition, please, see this notebook <a href="https://github.com/astropy/photutils-datasets/pull/5">here</a> for examples on how to use DAOPhotPSFPhotometry. 
</p>
