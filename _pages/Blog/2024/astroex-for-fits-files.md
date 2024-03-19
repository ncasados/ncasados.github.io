---
title: "Elixir and Astronomy Could Be Friends"
date: "2024-03-14 23:00:00"
thumbnail: "/assets/img/thumbnail/pillars_of_creation.webp"
---

Astropy exists for being able to utilize FITS files however I think it would be really cool to have it in Elixir.

# FITS files and where to get them
---
I happen to be a bit of an astronomy nerd.

Now in my astronomical pursuits, I have been looking to be able to use Elixir for reading FITS files--a specific file standard endorsed by NASA and the International Astronomical Union.

These files are cool because they can contain information such as spectra about star systems, planets, galaxies, etc. So if one was curious as to the presence of hydrogen in the atmosphere of some planet, they could pull down the FITS data for that planet at a repository like the [Mikulski Archive for Space Telescopes (MAST)](https://mast.stsci.edu/portal/Mashup/Clients/Mast/Portal.html).

With your FITS file in hand, you'll start having a fit trying to utilize it for anything. Now what one could do is get ahold of the Astropy library, some Jupyter Notebook, and some of your boy DESI ASTRO's videos on YouTube.

But I'm built different. I really like Elixir. Unfortunately, there are no Elixir libraries for reading FITS files--[so I decided to make one that doesn't work yet](https://github.com/marth141/astroex). However, [FITS files have a primer provided by NASA](https://fits.gsfc.nasa.gov/fits_primer.html) on how to at least get started doing something with them.

The big thing that I learned is that FITS files can be broken apart, byte by byte, into 80 byte chunks. When you do this, you'll start to get information that almost looks like something useable.

Although this is great, I've recently heard from some of the good folks on the Elixir slack that you can simply invoke Python from Elixir and doing some more digging into that, it seems that one simply could do that.

So perhaps pursuing building some "AstroPy, but in Elixir so obviously it'll be AstroEx" is probably something that doesn't need to be done.

However, where I'm at with my little library--perhaps one day it could get there. Admittedly with how little progress I've made on though, perhaps someone would beat me to that.
