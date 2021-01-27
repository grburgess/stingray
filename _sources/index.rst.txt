*****************************************
Stingray: Next-Generation Spectral Timing
*****************************************

Stingray is a community-developed astrophysical spectral-timing software package written in Python.

.. image:: images/stingray_logo.png
   :width: 700
   :scale: 40%
   :alt: Stingray logo, outline of a stingray on top of a graph of the power spectrum of an X-ray binary
   :align: center

There are a number of official software packages for X-ray spectral fitting (XSPEC, ISIS, Sherpa, ...).
Such a widely used and standard software package does not exist for X-ray timing, so until now it has mainly been the domain of custom, proprietary software.
Stingray originated during the 2016 workshop `The X-ray Spectral-Timing Revolution <http://www.lorentzcenter.nl/lc/web/2016/720/info.php3?wsid=720&venue=Oort/>`_: a group of X-ray astronomers and developers decided to agree on a common platform to develop a new software package.
The goals were to merge existing efforts towards a timing package in Python, following the best guidelines for modern open-source programming, thereby providing the basis for developing spectral-timing analysis tools.
This software provides an easily accessible scripting interface (possibly a GUI) and an API for power users.
Stingray's ultimate goal is to provide the community with a package that eases the learning curve for advanced spectral-timing techniques, with a correct statistical framework.

Further spectral-timing functionality, in particularly command line scripts based on the API defined within Stingray, is available in the package `HENDRICS <https://github.com/StingraySoftware/HENDRICS>`_.
A Graphical User Interface is under development as part of the project `DAVE <https://github.com/StingraySoftware/dave>`_.

Contents
========

.. toctree::
   :maxdepth: 2

   scope
   basics
   install
   core
   modeling
   simulator
   pulsar
   api
   history
   help
   contributing
   citing
   acknowledgements

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
