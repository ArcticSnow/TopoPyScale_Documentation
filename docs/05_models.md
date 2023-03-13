# Output Formats

TopoPyScale include a number of functions to export the downscaled timeseries to be compatible with some established energy and mass balance land-surface models for snow and permafrost physics, or hydrology. All these functions are available into the file `topo_export.py` and are integrated to the class `topoclass`.

## netcdf files
It is possible to export netcdf files for a list of given variables. Otherwise, by default all downscaled timeseries are available in `outputs/`

## FSM
TopoPyScale includes tools to interact and work with [FSM](https://github.com/RichardEssery/FSM). Those are available in the file `topo_sim.py`.

## Cryogrid
[Cryogrid](https://github.com/CryoGrid/CryoGrid) is a model used for simulating the thermal regime of the ground, particularly applied to permafrost and hydrological application.

## Snowmodel
Snowmodel is a snow model focused on wind redistribution. 

## CROCUS
[CROCUS](https://gmd.copernicus.org/articles/5/773/2012/gmd-5-773-2012.pdf) is a 1D physical model developed by Meteo France to simulate the evolution of snowpack state variables and snow metamorphic path.

## SNOWPACK
[SNOWPACK](https://www.slf.ch/en/services-and-products/snowpack.html) is a physical model developped at SLF, Switzerland to simulate the evolution a snowpack state variables and snow metamorphic path.

## GEOTOP
Geotop is a hydrological model