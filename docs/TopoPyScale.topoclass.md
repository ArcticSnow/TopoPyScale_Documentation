<!-- markdownlint-disable -->

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass#L0"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

# <kbd>module</kbd> `TopoPyScale.topoclass`
Toposcale class definition 

S. Filhol, September 2021 

project/  config.ini 
    -> input/ 
        -> dem/ 
        -> climate/ 
    -> output/ 



---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/Topoclass#L32"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>class</kbd> `Topoclass`
A python class to bring the typical use-case of toposcale in a user friendly object 

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/__init__#L37"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `__init__`

```python
__init__(config_file)
```








---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/compute_dem_param#L190"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `compute_dem_param`

```python
compute_dem_param()
```





---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/compute_horizon#L258"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `compute_horizon`

```python
compute_horizon()
```

Function to compute horizon angle and sample values for list of points :return: 

---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/compute_solar_geometry#L250"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `compute_solar_geometry`

```python
compute_solar_geometry()
```





---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/downscale_climate#L272"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `downscale_climate`

```python
downscale_climate()
```





---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/extract_dem_cluster_param#L208"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `extract_dem_cluster_param`

```python
extract_dem_cluster_param()
```

Function to segment a DEM in clusters and retain only the centroids of each cluster. :return: 

---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/extract_pts_param#L194"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

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

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/extract_topo_param#L234"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `extract_topo_param`

```python
extract_topo_param()
```

Function to select which  

---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/get_WMO_observations#L324"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `get_WMO_observations`

```python
get_WMO_observations()
```

Function to download and parse in-situ data from WMO database 

---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/get_era5#L289"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `get_era5`

```python
get_era5()
```

Funtion to call fetching of ERA5 data 

**TODO:**
 
- merge monthly data into one file (cdo?)- this creates massive slow down! 

---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/to_crocus#L378"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `to_crocus`

```python
to_crocus(fname_format='./outputs/CROCUS_pt_*.nc', scale_precip=1)
```

function to export toposcale output to crocus format .nc. This functions saves one file per point_id 



**Args:**
 
 - <b>`fout_format`</b> (str):  filename format. point_id is inserted where * is 
 - <b>`scale_precip`</b> (float):  scaling factor to apply on precipitation. Default is 1 

---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/to_cryogrid#L346"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `to_cryogrid`

```python
to_cryogrid(fname_format='Cryogrid_pt_*.nc', precip_partition='continuous')
```

wrapper function to export toposcale output to cryosgrid format from TopoClass 



**Args:**
 
 - <b>`fname_format`</b> (str):  filename format. point_id is inserted where * is 

---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/to_fsm#L371"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `to_fsm`

```python
to_fsm(fname_format='./outputs/FSM_pt_*.txt')
```

function to export toposcale output to FSM format 

---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/to_geotop#L426"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `to_geotop`

```python
to_geotop(fname_format='./outputs/meteo_*.txt')
```

function to export toposcale output to FSM format 

---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/to_musa#L433"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `to_musa`

```python
to_musa(fname_met='musa_met.nc', fname_labels='musa_labels.nc')
```

function to export TopoPyScale output in a format compatible with MuSa MuSa: https://github.com/ealonsogzl/MuSA 



**Args:**
 
 - <b>`fname`</b>:  filename of the netcdf  

---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/to_netcdf#L402"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `to_netcdf`

```python
to_netcdf(file_out='./outputs/output.nc')
```

function to export toposcale output to one single generic netcdf format, compressed 



**Args:**
 
 - <b>`file_out`</b> (str):  name of export file 

---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/to_snowmodel#L394"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `to_snowmodel`

```python
to_snowmodel(fname_format='./outputs/Snowmodel_stn_*.csv')
```

function to export toposcale output to snowmodel format .ascii, for single station standard 

 fout_format: str, filename format. point_id is inserted where * is 

---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topoclass/to_snowpack#L420"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

### <kbd>method</kbd> `to_snowpack`

```python
to_snowpack(fname_format='./outputs/smet_pt_*.smet')
```

function to export toposcale output to FSM format 




---

_This file was automatically generated via [lazydocs](https://github.com/ml-tooling/lazydocs)._
