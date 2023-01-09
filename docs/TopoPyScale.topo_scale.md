<!-- markdownlint-disable -->

<a href="../docs/TopoPyScale/topo_scale#L0"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

# <kbd>module</kbd> `TopoPyScale.topo_scale`
Toposcale functionalities 

S. Filhol, Oct 2021 

======= Organization of input data to Toposcale ====== dem_description (nb_points)  X  Y,  elev,  slope,  aspect,  svf,  x_ERA,  y_ERA,  elev_ERA, 

horizon_angles (nb_points * bins) solar_geom (nb_points * time * 2) surface_climate_data (spatial + time + var) plevels_climate_data (spatial + time + var + plevel) 



======= Dataset naming convention:  ========= ds_surf => dataset direct from ERA5 single level surface ds_plev => dataset direct from ERA5 pressure levels 

ds_surf_pt => 3*3 grid ERA5 single surface level around a given point (lat,lon) ds_plev_pt => 3*3 grid ERA5 pressure level around a given point (lat,lon) 

plev_interp => horizontal interpolation of the 3*3 grid at the point (lat,lon) for the pressure levels surf_interp => horizontal interpolation of the 3*3 grid at the point (lat,lon) for the single surface level 

top => closest pressure level above the point (lat,lon,elev) for each timesep bot => closest pressure level below the point (lat,lon,elev) for each timesep 

down_pt => downscaled data time series (t, u, v, q, LW, SW, tp) 



**TODO:**
 
- check that transformation from r,t to q for plevels is working fine 
- add metadata to all newly created variables in datasets ds_psurf, ds_plevel, down_pt 
- upscale method for all points in df_centroids: 
    - method (1) simply using a for loop over each row 
    - method (2) concatenate 3*3 grid along an additional dimension to process all points in one go. 

**Global Variables**
---------------
- **g**
- **R**

---

<a href="../docs/TopoPyScale/topo_scale/clear_files#L63"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `clear_files`

```python
clear_files(path)
```






---

<a href="../docs/TopoPyScale/topo_scale/downscale_climate#L71"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `downscale_climate`

```python
downscale_climate(
    project_directory,
    df_centroids,
    horizon_da,
    ds_solar,
    target_EPSG,
    start_date,
    end_date,
    interp_method='idw',
    lw_terrain_flag=True,
    tstep='1H',
    precip_lapse_rate_flag=True,
    file_pattern='down_pt*.nc'
)
```

Function to perform downscaling of climate variables (t,q,u,v,tp,SW,LW) based on Toposcale logic 



**Args:**
 
 - <b>`project_directory`</b>:  path to project root directory 
 - <b>`df_centroids`</b> (dataframe):  containing a list of point for which to downscale (includes all terrain data) 
 - <b>`horizon_da`</b> (dataarray):  horizon angles for a list of azimuth 
 - <b>`target_EPSG`</b> (int):  EPSG code of the DEM 
 - <b>`interp_method`</b> (str):  interpolation method for horizontal interp. 'idw' or 'linear' 
 - <b>`lw_terrain_flag`</b> (bool):  flag to compute contribution of surrounding terrain to LW or ignore 
 - <b>`tstep`</b> (str):  timestep of the input data, default = 1H 
 - <b>`file_pattern`</b> (str):  filename pattern for storing downscaled points, default = 'down_pt_*.nc' 



**Returns:**
 
 - <b>`dataset`</b>:  downscaled data organized with time, point_id, lat, long 


---

<a href="../docs/TopoPyScale/topo_scale/read_downscaled#L376"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `read_downscaled`

```python
read_downscaled(path='outputs/down_pt*.nc')
```

Function to read downscaled points saved into netcdf files into one single dataset using Dask 



**Args:**
 
 - <b>`path`</b> (str):  path and pattern to use into xr.open_mfdataset 



**Returns:**
 
 - <b>`dataset`</b>:  merged dataset readily to use and loaded in chuncks via Dask 




---

_This file was automatically generated via [lazydocs](https://github.com/ml-tooling/lazydocs)._
