# Examples

We present here a set of examples given you have a working python environment for `TopoPyScale`. For any of the example hereafter, create a folder in which a given example will be contained. In this folder you will need at the minium, the configuration file (*e.g.*`config.yml`), the Python processing pipeline or JuPyteR notebook. 

**WARNING 1:** the examples require to download the climate data from ERA5 data portal [CDS Copernicus](https://cds.climate.copernicus.eu/). Depending on the amount of data request and the servers' load, it may take up to few days to acquire the complete dataset. To perform the examples, the `cdsapi` credentials must be set as indicated in the [install](./1_instal.md) section. 

**WARNING 2:** as TopoPyscale can have a large amount of verbose, we recommand running `TopoPyScale` in a simple IPython console.

## Getting the Example Material

To run the examples you will need to download the project materials (about 32MB) containing the Digital Elevation models for each example as well as the configuration files. Those are available on Github as a [specific repository](https://github.com/ArcticSnow/TopoPyScale_examples) and is likely to evolve in the future alongside to the main [TopoPyScale](https://github.com/ArcticSnow/TopoPyScale) repository.

**Option 1:**
```bash
git clone https://github.com/ArcticSnow/TopoPyScale_examples
```

**Option 2**
```bash
wget https://github.com/ArcticSnow/TopoPyScale_examples/archive/refs/tags/v0.1.1.zip
unzip v0.1.1.zip
cd TopoPyScale_examples-0.1.1/
```

Access to the examples from the terminal:
```
# For Finse example (ex1)
cd ex1_norway_finse/

# For Retezat Mountain example (ex2)
cd ex2_romania_retezat/

# For Davos example (ex3)
cd ex3_switzerland_davos/
```

## Finse, Norway

### Site Description
Finse is located at 1200m above sea level in Southern Norway. The site is is equipped of a large set of instruments for weather, snow, carbon fluxes and others. A full description of instrumentation available on (UiO website)[https://www.mn.uio.no/geo/english/research/groups/latice/infrastructure/].This example can be run for specific point (weather station) or in spatialized way (TopoSUB). 


### How to run the example

1. Open an iPython console for the VE in which `TopoPyScale` is installed
2. run the following commands in the console. This will initialize a `topoclass` object and download (if necessary) the climate data. **WARNING** this may take many hours during which the console must be active. You may use `screen` for run the console in the background.
```python
from TopoPyScale import topoclass as tc

config_file = './config_spatial.yml'
mp = tc.Topoclass(config_file)
```
3. Derive all topographical morphometrics
```python
mp.compute_dem_param()
mp.extract_topo_param()
mp.compute_solar_geometry()
mp.compute_horizon()
```
4. Execute the downscaling and store to file in a format compatible with [`Cryogrid-Community`](https://github.com/CryoGrid/CryoGridCommunity_source) model.
```python
mp.downscale_climate()
mp.to_cryogrid()
```
5. Plot the results
```python
mp.plot.map_variable(time_step=1, var='t')

import matplotlib.pyplot as plt
plt.show()
```

This example stores the downscaled climate in timeseries. There is one timeseries per cluster label. The function `plot.map_variable()` maps the cluster timeseries to the pixels part of each cluster. All results are stored in the folder `./outputs`.

This example can be run to downscale climate to a single point (*e.g.* a weather station).

```python
config_file = './config_point.yml'
mq = tc.Topoclass(config_file)
mq.compute_dem_param()
mq.extract_topo_param()
mq.compute_solar_geometry()
mq.compute_horizon()
mq.downscale_climate()
mq.to_cryogrid()
```

To do so, we use a `.csv` file located in the folder `./inputs/dem/`. 
```csv
Name,stn_number,latitude,longitude,x,y
Finsevatne,SN25830,60.5938,7.527,419320.867306002,6718447.86246835
Fet-I-Eidfjord,SN49800,60.4085,7.2798,405243.856317655,6698143.36494597
```
This file requires the field `x` and `y`. The EPSG projection code of the `x` and `y` coordinates must be indicated in the file config_point.yml

## Retezat Range, Romania

This example perform climate downscaling using the TopoSUB routine for spatial downscaling. Retezat is a mountain range in the Romanian Sourthern Carpathians.

```python
from TopoPyScale import topoclass as tc

config_file = './config.yml'

# create a topopyscale python object
mp = tc.Topoclass(config_file)

# Downscaling preparation routines
mp.compute_dem_param()
mp.extract_topo_param()
mp.compute_solar_geometry()
mp.compute_horizon()

# Downscaling routine
mp.downscale_climate()

# Export in Cryogrid format
mp.to_cryogrid()
```

## Davos, Switzerland

This example demonstrate `TopoPyScale` for the area of Davos. It downscales climate, and perform simulation with the snow model FSM. 

### Site Description
Davos is located in South-Eastern Switzerland. 

### How to run the example

In an IPython console run the following.
```python
import pandas as pd
from TopoPyScale import topoclass as tc
from matplotlib import pyplot as plt
from TopoPyScale import topo_sim as sim



# download era5 (should read the ini to supply parameters. Area from a DEM or polygon?
# sparse points method?
#era5.retrieve_era5(product="reanalysis", startDate="2020-01-01", endDate="2020-01-31", eraDir="/home/joel/sim/topoPyscale_paiku/inputs/climate/",latN=29.375, latS=28.125, lonW=85.125, lonE=86.375, step=1, num_threads=10, surf_plev='surf', plevels=None)
#plev=[600, 650, 700, 750, 775, 800, 825, 850, 875, 900, 925, 950, 975, 1000 ]
#era5.retrieve_era5(product="reanalysis", startDate="2020-01-01", endDate="2020-01-31", eraDir="/home/joel/sim/topoPyscale_paiku/inputs/climate/",latN=29.375, latS=28.125, lonW=85.125, lonE=86.375, step=1, num_threads=10, surf_plev='plev', plevels=plev)


# ========= STEP 1 ==========
# Load Configuration
config_file = './config.ini'
mp = tc.Topoclass(config_file)

# Compute parameters of the DEM (slope, aspect, sky view factor)
mp.compute_dem_param()

# ========== STEP 2 ===========
# Extract DEM parameters for points of interest (centroids or physical points)

# ----- Option 1:
# Compute clustering of the input DEM and extract cluster centroids
mp.extract_topo_param()
# plot clusters
mp.toposub.plot_clusters_map()
mp.toposub.write_landform()
# plot sky view factor
# mp.toposub.plot_clusters_map(var='svf', cmap=plt.cm.viridis)

# ------ Option 2:
# inidicate in the config file the .csv file containing a list of point coordinates (!!! must same coordinate system as DEM !!!)
# mp.extract_pts_param(method='linear',index_col=0)

# ========= STEP 3 ==========
# compute solar geometry and horizon angles
mp.compute_solar_geometry()
mp.compute_horizon()

# ========= STEP 4 ==========
# Perform the downscaling
mp.downscale_climate()

# ========= STEP 5 ==========
# explore the downscaled dataset. For instance the temperature difference between each point and the first one
#(mp.downscaled_pts.t-mp.downscaled_pts.t.isel(point_id=0)).plot()
#plt.show()

# ========= STEP 6 ==========
# Export output to desired format
# mp.to_netcdf()
mp.to_fsm()

# ========= STEP 7 ===========
# Simulate FSM
for i in range(mp.config.n_clusters):
    nsim = "{:0>2}".format(i)
    sim.fsm_nlst(31, "./outputs/FSM_pt_"+ nsim +".txt", 24)
    sim.fsm_sim("./fsm_sims/nlst_FSM_pt_"+ nsim +".txt", "./FSM")

# extract GST results(7)
df = sim.agg_by_var_fsm(7)

# extraxt timeseries average
df_mean = sim.timeseries_means_period(df, mp.config.start_date, mp.config.end_date)

# map to domain grid
sim.topo_map(df_mean)

```
