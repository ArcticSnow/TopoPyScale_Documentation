<!-- markdownlint-disable -->

# <kbd>module</kbd> `TopoPyScale.topo_export`
Functions to export topo_scale output to formats compatible with existing models (e.g. CROCUS, Cryogrid, Snowmodel, ...) 

S. Filhol, December 2021 

TODO; 
- export compressed netcdf ERROR!! syntax is not correct 
- SPHY forcing (grids) 


---

## <kbd>function</kbd> `compute_scaling_and_offset`

```python
compute_scaling_and_offset(da, n=16)
```

Compute offset and scale factor for int conversion 



**Args:**
 
 - <b>`da`</b> (dataarray):  of a given variable 
 - <b>`n`</b> (int):  number of digits to account for 


---

## <kbd>function</kbd> `to_cryogrid`

```python
to_cryogrid(
    ds,
    df_pts,
    fname_format='Cryogrid_pt_*.nc',
    path='outputs/',
    label_map=False,
    da_label=None,
    climate_dataset_name='ERA5',
    project_author='S. Filhol'
)
```

Function to export TopoPyScale downscaled dataset in a netcdf format compatible for Cryogrid-community model 



**Args:**
 
 - <b>`ds`</b> (dataset):  downscaled values from topo_scale 
 - <b>`df_pts`</b> (dataframe):  with metadata of all point of downscaling 
 - <b>`fname_format`</b> (str):  file name for output 
 - <b>`path`</b> (str):  path where to export files 
 - <b>`label_map`</b> (bool):  export cluster_label map 
 - <b>`da_label`</b> (dataarray): (optional) dataarray containing label value for each pixel of the DEM 


---

## <kbd>function</kbd> `to_fsm`

```python
to_fsm(ds, df_pts, fname_format='FSM_pt_*.tx')
```

Function to export data for FSM. 



**Args:**
 
 - <b>`ds`</b> (dataset):  downscaled_pts, 
 - <b>`df_pts`</b> (dataframe):  toposub.df_centroids, 
 - <b>`fname_format`</b> (str pattern):  output format of filename 

format is a text file with the following columns year month  day   hour  SW      LW      Sf         Rf     Ta  RH   Ua    Ps (yyyy) (mm) (dd) (hh)  (W/m2) (W/m2) (kg/m2/s) (kg/m2/s) (K) (RH 0-100) (m/s) (Pa) 

See README.md file from FSM source code for further details 



**TODO:**
 
- Check unit DONE jf 
- Check format is compatible with compiled model DONE jf 


---

## <kbd>function</kbd> `to_micromet_single_station`

```python
to_micromet_single_station(
    ds,
    df_pts,
    fname_format='Snowmodel_pt_*.csv',
    na_values=-9999,
    headers=False
)
```

Function to export TopoScale output in the format for Listn's Snowmodel (using Micromet). One CSV file per point_id 



**Args:**
 
 - <b>`ds`</b> (dataset):  TopoPyScale xarray dataset, downscaled product 
 - <b>`df_pts`</b> (dataframe):  with point list info (x,y,elevation,slope,aspect,svf,...) 
 - <b>`fname_format`</b> (str):  filename format. point_id is inserted where * is 
 - <b>`na_values`</b> (int):  na_value default 
 - <b>`headers`</b> (bool):  add headers to file 



Example of the compatible format for micromet (headers should be removed to run the model: 

year   mo   dy    hr     stn_id  easting  northing  elevation   Tair     RH     speed    dir     precip (yyyy) (mm) (dd) (hh.hh) (number)   (m)       (m)      (m)        (C)    (%)     (m/s)   (deg)    (mm/dt) 

2002   10    1   12.00    101   426340.0  4411238.0  3598.0     0.92    57.77     4.80   238.29 -9999.00 2002   10    2   12.00    101   426340.0  4411238.0  3598.0    -3.02    78.77 -9999.00 -9999.00 -9999.00 2002   10    8   12.00    101   426340.0  4411238.0  3598.0    -5.02    88.77 -9999.00 -9999.00 -9999.00 


---

## <kbd>function</kbd> `to_crocus`

```python
to_crocus(
    ds,
    df_pts,
    fname_format='CROCUS_pt_*.nc',
    scale_precip=1,
    climate_dataset_name='ERA5',
    project_author='S. Filhol'
)
```

Functiont to export toposcale output to CROCUS netcdf format. Generates one file per point_id 



**Args:**
 
 - <b>`ds`</b> (dataset):  Toposcale downscaled dataset. 
 - <b>`df_pts`</b> (dataframe):  with point list info (x,y,elevation,slope,aspect,svf,...) 
 - <b>`fname_format`</b> (str):  filename format. point_id is inserted where * is 
 - <b>`scale_precip`</b> (float):  scaling factor to apply on precipitation. Default is 1 




---

_This file was automatically generated via [lazydocs](https://github.com/ml-tooling/lazydocs)._
