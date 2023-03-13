# FAQ

TopoPyScale is a library building in top of a number of advanced Python libraries such as `xarray`, `pandas` *et al.*, and data type such as Digital Elevation models, and climate datasets. In case you never came across these libraries, we advice you first get familiarized with their respective concepts. 

You may also have a look at the github issues which are [open](https://github.com/ArcticSnow/TopoPyScale/issues?q=is%3Aopen+is%3Aissue) or [closed](https://github.com/ArcticSnow/TopoPyScale/issues?q=is%3Aissue+is%3Aclosed).

## I get an `Error` message, why is the example not working?

If reading the error message does not give you clear pointers, please ask yourself the following questions:
- Is TopoPyScale installed in a Python 3.9 (or more recent) virtual environment?
- Have it dependencies been installed via `conda` as recommended in the [installation instructions](./01_install.md)?
- Did you follow the file structure recommended? It is good practice that the project directory is seperated from the package directory.
- Have you checked once more the config file? Are the dates right? Is the project path correct?

## How do I cite TopoPyScale?

1. To cite the software itself, a manuscript is in review in JOSS. 
2. To cite the method on which TopoPyScale relies on, we invite you to look at:
	- Fiddes, J. and Gruber, S.: TopoSCALE v.1.0: downscaling gridded climate data in complex terrain, Geosci. Model Dev., 7, 387–405, https://doi.org/10.5194/gmd-7-387-2014, 2014.
	- Fiddes, J. and Gruber, S.: TopoSUB: a tool for efficient large area numerical modelling in complex topography at sub-grid scales, Geosci. Model Dev., 5, 1245–1257, https://doi.org/10.5194/gmd-5-1245-2012, 2012.
