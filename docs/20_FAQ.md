# FAQ

`TopoPyScale` is a library building on top of a number of advanced Python libraries such as `xarray`, `pandas` *et al.*, and data type such as Digital Elevation models, and climate datasets. In case you never came across these libraries or types of data, we advice you to first get familiarized with their respective concepts. 

You may also have a look at the github issues currently [open](https://github.com/ArcticSnow/TopoPyScale/issues?q=is%3Aopen+is%3Aissue) or [closed](https://github.com/ArcticSnow/TopoPyScale/issues?q=is%3Aissue+is%3Aclosed).

## I get an `Error` message, why is the example not working?

If reading the error message does not give you clear pointers to solving the problem, please first review your setup with the following questions:

- Is `TopoPyScale` installed in a Python 3.9 (or more recent) virtual environment?
- Have its dependencies been installed via `conda` as recommended in the [installation instructions](./01_install.md)?
- Is the file structure following the documenation recommendation (i.e. one dedicated folder for a downscaling project)? It is good practice that the project directory is seperated from the package directory.
- Have you checked once more the config file? Might be worth one more look ;) 
	- Are the dates right? 
	- Is the project path correct?
	- is the config file containing all fields according to the example in the [documentation](https://topopyscale.readthedocs.io/en/latest/3_configurationFile/)? If you observe a field is missing, please let us know about it.
	- is the DEM  file correct?
	- are the projection EPSG codes correct?
	- lastly, check indents are fine as YAML is indent sensitive! 

## I have improvements suggestions, how can I bring it up?
Please, meet us on Github on the source code repository. A number of improvements and new features have been [identified](https://github.com/ArcticSnow/TopoPyScale/issues?q=is%3Aopen+is%3Aissue+label%3Aenhancement+). If your suggestion is not yet within this list, you may either interact via specific [Issues](https://github.com/ArcticSnow/TopoPyScale/issues), or through the [Discussion](https://github.com/ArcticSnow/TopoPyScale/discussions) page. Note: you'll need a Github account.

## How to load an exhisiting project whithout having to process the downscaling again?

Given you have all outputs file availble in `/outputs`, then you may load all necessary file of a downscaling project as follow:

```python
from TopoPyScale import topoclass as tc

config_file = './config.yml'
mp = tc.Topoclass(config_file)
mp.load_project()
```

## How to cite `TopoPyScale`?

1. To cite the software itself, a manuscript is in review in [JOSS](https://joss.theoj.org/papers/91621581b2d0c097495fdd1e58179e87). 
2. To cite the method on which `TopoPyScale` relies on, we invite you to look at:
	- Fiddes, J. and Gruber, S.: TopoSCALE v.1.0: downscaling gridded climate data in complex terrain, Geosci. Model Dev., 7, 387–405, https://doi.org/10.5194/gmd-7-387-2014, 2014.
	- Fiddes, J. and Gruber, S.: TopoSUB: a tool for efficient large area numerical modelling in complex topography at sub-grid scales, Geosci. Model Dev., 5, 1245–1257, https://doi.org/10.5194/gmd-5-1245-2012, 2012.
