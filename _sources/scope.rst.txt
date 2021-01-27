************
Capabilities
************

Currently Implemented Methods
=============================

Currently implemented functionality in this library comprises:

* loading event lists from fits files of a few missions (RXTE/PCA, NuSTAR/FPM, XMM-Newton/EPIC)
* constructing light curves from event data, various operations on light curves (e.g. add, subtract, join, truncate)
* Good Time Interval operations
* power spectra in Leahy, rms normalization, absolute rms and no normalization
* averaged power spectra
* dynamical power spectra
* maximum likelihood fitting of periodograms/parametric models
* (averaged) cross spectra
* coherence, time lags
* cross correlation functions
* r.m.s. spectra and lags (time vs energy, time vs frequency); UNDER DEVELOPMENT
* covariance spectra; UNDER DEVELOPMENT
* bispectra; UNDER DEVELOPMENT
* (Bayesian) quasi-periodic oscillation searches
* simulating a light curve with a given power spectrum
* simulating a light curve from another light curve and a 1-d (time) or 2-d (time-energy) impulse response
* simulating an event list from a given light curve _and_ with a given energy spectrum
* pulsar searches with Epoch Folding, :math:`Z^2_n` test

Future Additions
================

We welcome feature requests: if you need a particular tool that's currently not available or have a new method you think might be usefully implemented in Stingray, please :doc:`get in touch <help>`!

Other future additions we are currently implementing are:

* bicoherence
* phase-resolved spectroscopy of quasi-periodic oscillations
* Fourier-frequency-resolved spectroscopy
* power colours
* full HEASARC-compatible mission support
* pulsar searches with $H$-test
* binary pulsar searches
