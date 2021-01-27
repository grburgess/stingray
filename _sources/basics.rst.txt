####################################################
The basics about Stingray and astrophysics clarified
####################################################

1. What does Stingray do?
=========================

Stingray is a community-developed spectral-timing software package in Python for astrophysical data. It provides a basis for advanced spectral-timing analysis with a correct statistical framework while also being open-source.

Stingray provides functionalities such as:

- Constructing light curves from event data and performing various operations on light curves (e.g. add, subtract, join, truncate)
- Good Time Interval operations
- Creating periodograms(power spectra) and cross spectra

*more on this can be found in intro.txt*

2. So well what does all of this mean?
======================================
I know, I know all these words are too long and daunting to look at but making them seem easy is the whole reason why this document exists. So let's start from the basics:

Spectral Timing and why is it needed?
-------------------------------------
Let's back off a little and first understand what time-series and time-series analysis are:

| - Time Series: It is a sequence of observations recorded at a succession of time intervals. In general, time series are characterized by the interdependence of its values. The value of the series at some time t is generally not independent of its value at, say, t−1. [#f1]_
| There is no minimum or maximum amount of time that must be included, allowing the data to be gathered in a way that provides the information being sought by the analyst examining the activity. [#f2]_

| - Time Series Analysis: It is a statistical technique that deals with gaining insights from periodic or stochastic time-series data.

Now since that's cleared let's understand what spectral-timing analysis is:

| - Spectral-Timing Analysis: Many time series show periodic behaviour. This periodic behaviour can be very complex. Spectral analysis is a technique that allows us to discover underlying periodicities by decomposing the complex signal into simpler parts. To perform spectral analysis, we first must transform data from the time domain to the frequency domain. [#f1]_
| Hence spectral analysis can be defined as decomposing a stationary time series *{xT}* into a combination of sinusoids, with a random (and uncorrelated) coefficient essentially analysis in the frequency domain. The covariance of this time series *{xT}* can be represented by a function known as the spectral density.

Good Time Intervals
--------------------
| When observing a stellar object with a satellite, data is accumulated by observing the source with short exposures over time or collecting single photons and measuring their arrival time.
| While recording observations, we might have obstructions from the Earth in the form of increased particle background or any other effect that hinders our ability to observe the source properly.
| There will be times during the observation when everything is working perfectly. Good time intervals (GTIs) are the time intervals where instruments are working well and the source is perfectly visible.

Light Curves
-------------
| Light curves are graphs that show the brightness of an object over a period of time. Images show from the part of an object from where light is emitted. Another piece of information we have about light is the time when it reaches the detector. Astronomers use this "timing" information to create light curves and perform timing analysis. [#f3]_
| They are simply graphs of brightness (Y-axis) vs. time (X-axis). Brightness increases as you go up the graph and time advances as you move to the right.

| For eg., if we have the following data: [#f3]_

.. CSV-table::
   :header: "Date", "Brightness (magnitude)"
   :widths: 60, 40

   "April 21", "9.2"
   "April 27", "9.3"
   "May 3", "9.7"
   "May 9", "9.9"
   "May 15", "9.6"
   "May 21", "9.8"
   "May 27", "9.9"
   "June 2", "9.7"
   "June 8", "9.1"
   "June 14", "8.8"
   "June 20", "8.7"
   "June 26", "8.3"
   "July 2", "8.6"
   "July 8", "9.1"
   "July 14", "9.1"
   "July 20", "9.2"
   "July 26", "9.5"
   "August 1", "9.9"
   "August 7", "9.7"
   "August 13", "9.7"

| then we might make a light curve, and it would look like this: [#f3]_

.. image:: https://imagine.gsfc.nasa.gov/Images/science/lightcurve_example.gif
    :align: center
    :alt: Lightcurve Image

| We can generate similar light curves for studying any part of the light spectrum eg. X-Rays. The study of the light curve, together with other observations, can yield considerable information about the physical process that produces it. The record of changes in brightness that a light curve provides can help astronomers understand processes at work within the object they are studying and identify specific categories (or classes) of stellar events. [#f3]_

Periodograms, Power spectra and Cross spectra
---------------------------------------------
Let's first understand the concept of spectral density which we have mentioned.

| - Spectral Density/Power Spectra: The power spectrum of a time series {xT} describes the distribution of power into the frequency components composing that signal. Any signal that can be represented as a variable that varies in time has a corresponding frequency spectrum. When these signals are viewed in the form of a frequency spectrum, certain aspects of the received signals or the underlying processes producing them are revealed.

| - Power Spectral Density Function: A Power spectral density function (PSD) shows the strength of the energy variations as a function of frequency. In other words, it shows at which frequencies are variations strong, weak. The unit of PSD is energy (variance) per frequency(width) and one can obtain energy within a specific frequency range by integrating PSD within that frequency range.

| - Periodogram: A periodogram is a brute-force estimate of the spectral density of a signal. The naked eye can be fooled by repeated patterns in light curves, things that seem periodic might not be. In order to look for periodic signals, there are several mathematical tools. A periodogram is one of them. A periodogram calculates the significance of different frequencies in time-series data to identify any intrinsic periodic signals. [#f4]_

| The statistical significance of each frequency is computed based upon a series of algebraic operations that depend on the particular algorithm used and periodic signal shape assumed. Any time series can be expressed as a combination of cosine (or sine) waves with differing periods (how long it takes to complete a full cycle) and amplitudes (maximum/minimum value during the cycle). This fact can be utilized to examine the important periodic (cyclical) behaviour in a time series. A periodogram is used to identify the dominant periods (or frequencies) of a time series.

| A periodogram is similar to the Fourier Transform but is optimized for unevenly time-sampled data, and for different shapes in periodic signals. Unevenly sampled data is particularly common in astronomy, where your target might rise and set over several nights, or you have to stop observing with your spacecraft to download the data.
| To understand how to calculate a periodogram check this out: https://online.stat.psu.edu/stat510/lesson/6/6.1#paragraph--356

| - Cross Spectra: Cross spectral analysis allows one to determine the relationship between two time series as a function of frequency. Normally, we wish to compare two time-series along their statistically significant peaks to see if these signals are related to one another at the same frequency and if so, what is the phase relationship between them. Even if two signals look identical we wish to check their periodicity and understand how they are related.
| For further reference check this out: https://atmos.washington.edu/~dennis/552_Notes_6c.pdf


3. So, how does Stingray make this easier?
==========================================
| Stingray has various methods and classes such as:

- lightcurve: Used to generate light curves. It creates a lightcurve object from timestamps and photon count per timestamp. It has various methods such as _add_, _sub_, _neg_, _join_, __truncate__, __split__ to perform operations on the light curve.

- Crossspectrum: Creates a cross spectra from two light curves. It also has another class *AveragedCrosspectrum* which is used to analyze long light curves by segmenting and performing FFT on each segment and averaging the resulting cross spectra.

- Powerspectrum: Creates a power spectra/periodogram from a binned light curve with or without normalization. It also has another class *AveragedPowerspectrum* which is used to analyze long light curves by segmenting and performing FFT on each segment and averaging the resulting power spectra.

| and many more

| Stingray also provides a CLI *HENDRICS* and GUI *dave* interface for providing an abstract analysis interface.


4. Further Readings
===================
| If all of this intrigues you as much as it did me, you can go through the references mentioned below and the notebooks(https://github.com/StingraySoftware/notebooks) for Stingray or even fork the repository and mess around with the code yourself(**Highly Recommended ;)**)


|

References
==========

.. [#f1] http://web.stanford.edu/class/earthsys214/notes/series.html
.. [#f2] https://www.investopedia.com/terms/t/timeseries.asp
.. [#f3] https://imagine.gsfc.nasa.gov/science/toolbox/timing1.html
.. [#f4] http://coolwiki.ipac.caltech.edu/index.php/What_is_a_periodogram
