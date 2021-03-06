# harold [![GitHub license](https://img.shields.io/github/license/mashape/apistatus.svg?style=plastic)](https://github.com/ilayn/harold/blob/master/LICENSE)
A systems and controls toolbox for Python3. MIT licensed. See `LICENSE.md` file for details.

## Brief Intro

This is harold, a Python3 toolbox. I'm currently implementing a subset of the features of the control toolboxes that are found on matlab, mathematica, sage, octave, scilab and whoknowswhatelsekidsareusingthesedays. Though the main purpose of this attempt was to scratch my own itches and teach myself Python with a running project example, it grew out of its flower pot and I squeezed enough adrenalin to let it go run in the wild (a running flower?!). 

There is already a pseudo-matured control toolbox which is led by Richard Murray et al. ([click for the Github page](https://github.com/python-control/python-control) ) and it can perform already most of the essential tasks. Hence, if you want to have something that resembles the basics of matlab control toolbox give it a try. The reason why I didn't fork that and started from scratch is a-few-fold:

  1. I couldn't install [Slycot](https://github.com/jgoppert/Slycot) (actually drove me nuts) on Windows. Besides, if this is going to be a true open-source project, it is my belief that the nuts and bolts should be accessible. Fortran code is both only readable to some  members of an esoteric cult and has strange license issues, see [SLICOT homepage](http://slicot.org/). Even worse matlab has its own code given in the unexplicable and encrypted `.p` file format. 
  2. python-control emulates the matlab syntax and usage (for a good reason considering the matlab users) which is something I really wish to leave behind completely. Just to name a few, argument hopping thanks to `nargin,nargout` stuff, inconsistent (sometimes just stupid) error handling, weird amalgam of structs and cells usage... 
  3. I wish to implement (or at least try) the production-quality code in pure python so that the SLICOT routines buried under layers of Klingon language is avoided for the interested experts who would like to replace a function with their own. 
  4. I am too opinionated about the way control toolboxes are setup. 


By the way, if you are interested in robust control you would probably appreciate the  [Skogestad-Python](https://github.com/alchemyst/Skogestad-Python) project. 

## Features

All the functions are written with MIMO intentions at the outset which is inevitable if we are serious about avoiding SLICOT. 

  - The function names are verbose and (hopefully) understandable. 
  - Programmatically, only two classes exist `Transfer` and `State` and the rest is number crunching.
  - Interactive plots suitable for Ipython (if I can fix that nasty last problem) hence way better Bode, Nyquist plots and root loci (in case people are still using). 
  - Numerical polynomial operations (as opposed to symbolic) such as Least Common Multiples, Greatest Common Divisors etc. which is tested via pathological examples found in academic papers and to some extent practically on strange transfer matrices.
  - Matrix-pencil based subroutines, Hessenberg forms and transmission zero computations (this one I've tested as much as I can). Agrees with matlab, if not better resolution, and typically much faster for reasons I don't know yet.
  - Better control of internal tolerances that affects minimal realizations, rank tolerances and so on. 
  - When a model is discretized, it remembers the method used (or set later) and also continous/discrete, discrete/discrete type of interconnections recognize the slowest sampling time system and resamples remaining ones. 
  - Helper functions that makes it easy to slice, concatenate, manipulate system data thanks to Python/Numpy flexibility. 
  - The only dependencies are `numpy`,`scipy`,`scipy.signal.deconvolve`,
  `tabulate.tabulate`,`copy.deepcopy`,`itertools.zip_longest`,`collections`


## Current Status

- Burning issues are the documentation and enabling the `nosetest` framework.

Until I learn how to use Python project structure, nosetesting and other Git related issues, this will be the baseline page. When I manage to figure those out. It will appear on PyPI. There is a rough TODO list given at the top of `harold.py` file for the interested.


### Contact

If something caught your eye or you have a burning question, send one to `harold.of.python@gmail.com`
