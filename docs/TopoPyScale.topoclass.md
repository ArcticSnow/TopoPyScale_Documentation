<!-- markdownlint-disable -->

# <kbd>module</kbd> `TopoPyScale.topoclass`
Toposcale class definition 

S. Filhol, September 2021 

project/  config.ini 
    -> input/ 
        -> dem/ 
        -> climate/ 
    -> output/ 



---

## <kbd>class</kbd> `Topoclass`
A python class to bring the typical use-case of toposcale in a user friendly object 

### <kbd>method</kbd> `__init__`

```python
__init__(config_file)
```








---

### <kbd>method</kbd> `compute_dem_param`

```python
compute_dem_param()
```





---

### <kbd>method</kbd> `compute_horizon`

```python
compute_horizon()
```

Function to compute horizon angle and sample values for list of points :return: 

---

### <kbd>method</kbd> `compute_solar_geometry`

```python
compute_solar_geometry()
```





---

### <kbd>method</kbd> `downscale_climate`

```python
downscale_climate()
```





---

### <kbd>method</kbd> `extract_dem_cluster_param`

```python
extract_dem_cluster_param()
```

Function to segment a DEM in clusters and retain only the centroids of each cluster. :return: 

---

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

### <kbd>method</kbd> `extract_topo_param`

```python
extract_topo_param()
```

Function to select which  

---

### <kbd>method</kbd> `get_era5`

```python
get_era5()
```

Funtion to call fetching of ERA5 data 

**TODO:**
 
- merge monthly data into one file (cdo?)- this creates massive slow down! 

---

### <kbd>method</kbd> `to_crocus`

```python
to_crocus(fname_format='./outputs/CROCUS_pt_*.nc', scale_precip=1)
```

function to export toposcale output to crocus format .nc. This functions saves one file per point_id 



**Args:**
 
 - <b>`fout_format`</b> (str):  filename format. point_id is inserted where * is 
 - <b>`scale_precip`</b> (float):  scaling factor to apply on precipitation. Default is 1 

---

### <kbd>method</kbd> `to_cryogrid`

```python
to_cryogrid(fname_format='Cryogrid_pt_*.nc')
```

wrapper function to export toposcale output to cryosgrid format from TopoClass 



**Args:**
 
 - <b>`fname_format`</b> (str):  filename format. point_id is inserted where * is 

---

### <kbd>method</kbd> `to_fsm`

```python
to_fsm(fname_format='./outputs/FSM_pt_*.txt')
```

function to export toposcale output to FSM format 

---

### <kbd>method</kbd> `to_netcdf`

```python
to_netcdf(file_out='./outputs/output.nc')
```

function to export toposcale output to one single generic netcdf format, compressed 



**Args:**
 
 - <b>`file_out`</b> (str):  name of export file 

---

### <kbd>method</kbd> `to_snowmodel`

```python
to_snowmodel(fname_format='./outputs/Snowmodel_stn_*.csv')
```

function to export toposcale output to snowmodel format .ascii, for single station standard 

 fout_format: str, filename format. point_id is inserted where * is 




---

_This file was automatically generated via [lazydocs](https://github.com/ml-tooling/lazydocs)._
