<!-- markdownlint-disable -->

<a href="../docs/TopoPyScale/topoclass#L0"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

# <kbd>module</kbd> `TopoPyScale.topoclass`
Toposcale class definition 

S. Filhol, September 2021 

project/  config.ini 
    -> input/ 
        -> dem/ 
        -> climate/ 
    -> output/ 



---

<a href="../docs/TopoPyScale/topoclass/Topoclass#L40"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>class</kbd> `Topoclass`
A python class to bring the typical use-case of toposcale in a user friendly object 

<a href="../docs/TopoPyScale/topoclass/__init__#L45"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `__init__`

```python
__init__(config_file)
```








---

<a href="../docs/TopoPyScale/topoclass/compute_dem_param#L201"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `compute_dem_param`

```python
compute_dem_param()
```





---

<a href="../docs/TopoPyScale/topoclass/compute_horizon#L341"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `compute_horizon`

```python
compute_horizon()
```

Function to compute horizon angle and sample values for list of points 

---

<a href="../docs/TopoPyScale/topoclass/compute_solar_geometry#L306"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `compute_solar_geometry`

```python
compute_solar_geometry()
```





---

<a href="../docs/TopoPyScale/topoclass/downscale_climate#L366"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `downscale_climate`

```python
downscale_climate()
```





---

<a href="../docs/TopoPyScale/topoclass/extract_pts_param#L210"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `extract_pts_param`

```python
extract_pts_param(method='nearest', **kwargs)
```

Function to use a list point as input rather than cluster centroids from DEM segmentation (topo_sub.py/self.clustering_dem()). 



**Args:**
  df (dataFrame): 
 - <b>`method`</b> (str):  method of sampling 
 - <b>`**kwargs`</b>:  pd.read_csv() parameters 

**Returns:**
 

---

<a href="../docs/TopoPyScale/topoclass/extract_topo_cluster_param#L224"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `extract_topo_cluster_param`

```python
extract_topo_cluster_param()
```

Function to segment a DEM in clusters and retain only the centroids of each cluster. 

:return: 



**TODO:**
 
- try to migrate most code of this functino to topo_sub.py as a function itself segment_topo() 

---

<a href="../docs/TopoPyScale/topoclass/extract_topo_param#L259"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `extract_topo_param`

```python
extract_topo_param()
```

Function to select which  

---

<a href="../docs/TopoPyScale/topoclass/get_WMO_observations#L466"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `get_WMO_observations`

```python
get_WMO_observations()
```

Function to download and parse in-situ data from WMO database 

---

<a href="../docs/TopoPyScale/topoclass/get_era5#L431"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `get_era5`

```python
get_era5()
```

Funtion to call fetching of ERA5 data 

**TODO:**
 
- merge monthly data into one file (cdo?)- this creates massive slow down! 

---

<a href="../docs/TopoPyScale/topoclass/load_project#L144"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `load_project`

```python
load_project()
```

Function to load pre-existing TopoPyScale project saved in files 

---

<a href="../docs/TopoPyScale/topoclass/to_crocus#L517"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `to_crocus`

```python
to_crocus(fname_format='CROCUS_pt_*.nc', scale_precip=1)
```

function to export toposcale output to crocus format .nc. This functions saves one file per point_id 



**Args:**
 
 - <b>`fout_format`</b> (str):  filename format. point_id is inserted where * is 
 - <b>`scale_precip`</b> (float):  scaling factor to apply on precipitation. Default is 1 

---

<a href="../docs/TopoPyScale/topoclass/to_cryogrid#L486"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `to_cryogrid`

```python
to_cryogrid(fname_format='Cryogrid_pt_*.nc', precip_partition='continuous')
```

wrapper function to export toposcale output to cryosgrid format from TopoClass 



**Args:**
 
 - <b>`fname_format`</b> (str):  filename format. point_id is inserted where * is 

---

<a href="../docs/TopoPyScale/topoclass/to_fsm#L511"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `to_fsm`

```python
to_fsm(fname_format='FSM_pt_*.txt')
```

function to export toposcale output to FSM format 

---

<a href="../docs/TopoPyScale/topoclass/to_geotop#L562"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `to_geotop`

```python
to_geotop(fname_format='meteo_*.txt')
```

function to export toposcale output to FSM format 

---

<a href="../docs/TopoPyScale/topoclass/to_musa#L568"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `to_musa`

```python
to_musa(fname_met='musa_met.nc', fname_labels='musa_labels.nc')
```

function to export TopoPyScale output in a format compatible with MuSa MuSa: https://github.com/ealonsogzl/MuSA 



**Args:**
 
 - <b>`fname`</b>:  filename of the netcdf  

---

<a href="../docs/TopoPyScale/topoclass/to_netcdf#L544"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `to_netcdf`

```python
to_netcdf(file_out='output.nc', variables=None)
```

function to export toposcale output to one single generic netcdf format, compressed 



**Args:**
 
 - <b>`file_out`</b> (str):  name of export file 
 - <b>`variables`</b> (list str):  list of variable to export. Default exports all variables 

---

<a href="../docs/TopoPyScale/topoclass/to_snowmodel#L532"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `to_snowmodel`

```python
to_snowmodel(fname_format='Snowmodel_stn_*.csv')
```

function to export toposcale output to snowmodel format .ascii, for single station standard 

 fout_format: str, filename format. point_id is inserted where * is 

---

<a href="../docs/TopoPyScale/topoclass/to_snowpack#L556"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `to_snowpack`

```python
to_snowpack(fname_format='smet_pt_*.smet')
```

function to export toposcale output to FSM format 


---

<a href="../docs/TopoPyScale/topoclass/Plotting#L590"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>class</kbd> `Plotting`
Sub-Class with plotting functions for topoclass object 




---

<a href="../docs/TopoPyScale/topoclass/horizon#L640"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `horizon`

```python
horizon()
```





---

<a href="../docs/TopoPyScale/topoclass/map_center_clusters#L622"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `map_center_clusters`

```python
map_center_clusters(
    background_var='elevation',
    cmap=<matplotlib.colors.ListedColormap object at 0x7f9a6248d670>,
    hillshade=True,
    **kwargs
)
```





---

<a href="../docs/TopoPyScale/topoclass/map_clusters#L629"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `map_clusters`

```python
map_clusters(**kwargs)
```





---

<a href="../docs/TopoPyScale/topoclass/map_terrain#L615"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `map_terrain`

```python
map_terrain(var='elevation', hillshade=True, **kwargs)
```





---

<a href="../docs/TopoPyScale/topoclass/map_variable#L598"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `map_variable`

```python
map_variable(
    var='t',
    time_step=1,
    time=None,
    cmap=<matplotlib.colors.LinearSegmentedColormap object at 0x7f9a6249c9d0>,
    hillshade=True,
    **kwargs
)
```





---

<a href="../docs/TopoPyScale/topoclass/solar_geom#L637"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `solar_geom`

```python
solar_geom()
```





---

<a href="../docs/TopoPyScale/topoclass/timeseries#L634"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `timeseries`

```python
timeseries()
```








---

_This file was automatically generated via [lazydocs](https://github.com/ml-tooling/lazydocs)._
