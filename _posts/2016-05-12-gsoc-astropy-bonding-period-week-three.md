---
layout: post
title: "Community Bonding Period: Week Three"
excerpt: "Week two of the community bonding period comes to its end!"
modified: 2016-05-12
tags: [gsoc, astropy, openastronomy]
comments: true
image:
  feature: gsoc_post.jpg
  credit: Hubble Space Telescope
---

Second week of the community bonding period is over!

During that week, I primarily took a detailed reading of the classic Stetson's 1987 paper, which meticulously describes the algorithms implemented in the DAOPHOT software to perform point spread function photometry on crowded fields.

As stated in the previous post, psf photometry of overlapping sources is feasible with DAOPHOT through the loop FIND-GROUP-NSTAR-SUBTRACT-FIND-GROUP... until no more sources are found.

Right now, **photutils** already has FIND and SUBTRACT routines implemented. 
So, I started by sketch an interface of the GROUP routine, which looks like this

```python
def daogroup(starlist, crit_separation=None):
    """
    This is an implementation that follows the DAOGROUP algorithm presented
    by Stetson (1987).

    GROUP divides an entire starlist into sets of distinct, self-contained
    groups of mutually overlapping stars.

    GROUP accepts as input a list of stars and their approximate
    brightenesses relative to a model stellar intensity profile for the frame
    and determines which stars are close enough to be capable of
    adversely influencing each others' profile fits.

    Parameters
    ----------
    starlist : `~astropy.Table` or array-like
        List of stars positions.
        If `~astropy.Table`, columns should be named 'x_0' and 'y_0'.
        Additionally, 'flux_0' may also be provided. 
        If array-like, it should be either (x_0, y_0) or (x_0, y_0, flux_0).
        If 'starlist' only contains x_0 and y_0, 'crit_separation' must be
        provided.
    crit_separation : float (optional)
        Distance, in units of pixels, such that any two stars separated by
        less than this distance will be placed in the same group.
        If None, 'flux_0' must be provided in 'starlist'.
    
    Returns
    -------
    group_starlist : list of `~astropy.Table`
        Each `~astropy.Table` in the list corresponds to a group of mutually
        overlapping starts.

    Notes
    -----
    Assuming the psf fwhm to be known, 'crit_separation' may be set to
    k*fwhm, for some positive real k.

    See
    ---
    `~daofind`
    """

    The GROUP algorithm, as described by Stetson, is as follows.

    Take the first star on `starlist`, then the rest of the list is searched for stars lying within one critical separation of the star in question. If any stars are found to lie within one critical separation, they are assigned to its group. Otherwise, the star in question is isolated and may be fitted by a single model.
    When the end of the star list has been reached, the stars remaining unassigned are searched for any lying within the critical separation of the second star in the group; if such are found, they are assigned to that group.
    This process is iterated until no star remains unassigned.

    Some comments on complexity:
        - For a given star, find all stars lying within one critical
        separation takes at most O(n).
        - For a given group, insert stars takes at most O(n).
```

For the third week I expect to refine this description a bit and start a similarsketch for the NSTAR routine. Just to give a glimpse, NSTAR basically accepts as input the list of groups returned by GROUP and, for every group, it creates a compound PSF model which will be fittted to all stars within a given group.

*Now, to work*! :)
