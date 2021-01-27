*******
History
*******

.. include:: ../CHANGELOG.rst

Performance improvements
========================

Version 0.2 introduced a few performance improvements when ``Lightcurve`` objects are created.
Once the user defines either the counts per bin or the count rates, the other quantity will be evaluated _lazily_, the first time it is requested.
Also, we introduce a new ``low_memory`` option in ``Lightcurve``: if selected, and users define e.g. ``counts``, ``countrate`` will be calculated _every_time it is requested, and will not be stored in order to free up RAM.

Previous projects merged to Stingray
====================================

* Daniela Huppenkothen's original Stingray
* Matteo Bachetti's `MaLTPyNT <https://github.com/matteobachetti/MaLTPyNT>`_
* Abigail Stevens' RXTE power spectra code and phase-resolved spectroscopy code
* Simone Migliari's and Paul Balm's X-ray data exploration GUI commissioned by ESA
