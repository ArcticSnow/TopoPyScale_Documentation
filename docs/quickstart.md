# Quick Start

## Basic usage

1. Setup your Python environment
2. Create your project directory
3. Configure the file `config.yml` to fit your problem (see [`config.yml`](https://github.com/ArcticSnow/TopoPyScale/blob/main/TopoPyScale/config.yml) for an example)
4. Run TopoPyScale

```python
import pandas as pd
from TopoPyScale import topoclass as tc
from matplotlib import pyplot as plt

# ========= STEP 1 ==========
# Load Configuration
config_file = './config.yml'
mp = tc.Topoclass(config_file)
# Compute parameters of the DEM (slope, aspect, sky view factor)
mp.compute_dem_param()

# ========== STEP 2 ===========
# Extract DEM parameters for points of interest (centroids or physical points)

# ----- Option 1:
# Compute clustering of the input DEM and extract cluster centroids
mp.extract_dem_cluster_param()
# plot clusters
mp.toposub.plot_clusters_map()
# plot sky view factor
mp.toposub.plot_clusters_map(var='svf', cmap=plt.cm.viridis)

# ------ Option 2:
# inidicate in the config file the .csv file containing a list of point coordinates (!!! must same coordinate system as DEM !!!)
mp.extract_pts_param(method='linear',index_col=0)

# ========= STEP 3 ==========
# compute solar geometry and horizon angles
mp.compute_solar_geometry()
mp.compute_horizon()

# ========= STEP 4 ==========
# Perform the downscaling
mp.downscale_climate()

# ========= STEP 5 ==========
# explore the downscaled dataset. For instance the temperature difference between each point and the first one
(mp.downscaled_pts.t-mp.downscaled_pts.t.isel(point_id=0)).plot()
plt.show()

# ========= STEP 6 ==========
# Export output to desired format
mp.to_netcdf()
```

TopoClass will create a file structure in the project folder (see below). TopoPyScale assumes you have a DEM in GeoTiFF, and a set of climate data in netcdf (following ERA5 variable conventions). 
TopoPyScale can easier segment the DEM using clustering (e.g. K-mean), or a list of predefined point coordinates in `pts_list.csv` can be provided. Make sure all parameters in `config.yml` are correct.
```
my_project/
    ├── inputs/
        ├── dem/ 
            ├── my_dem.tif
            └── pts_list.csv  (optional)
        └── climate/
            ├── PLEV*.nc
            └── SURF*.nc
    ├── outputs/
            ├── tmp/
    └── config.yml
```