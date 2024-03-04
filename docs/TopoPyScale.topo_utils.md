<!-- markdownlint-disable -->

# <kbd>module</kbd> `TopoPyScale.topo_utils`





---

## <kbd>function</kbd> `ds_to_indexed_dataframe`

```python
ds_to_indexed_dataframe(ds)
```

Function to convert an Xarray dataset with multi-dimensions to indexed dataframe (and not a multilevel indexed dataframe). WARNING: this only works if the variable of the dataset have all the same dimensions! 

By default the ds.to_dataframe() returns a multi-index dataframe. Here the coordinates are transfered as columns in the dataframe 



**Args:**
 
 - <b>`ds`</b> (dataset):  xarray dataset with all variable of same number of dimensions 



**Returns:**
 pandas dataframe: 


---

## <kbd>function</kbd> `multicore_pooling`

```python
multicore_pooling(fun, fun_param, n_cores)
```

Function to perform multiprocessing on n_cores 

**Args:**
 
 - <b>`fun`</b> (obj):  function to distribute 
 - <b>`fun_param zip(list)`</b>:  zip list of function arguments 
 - <b>`n_core`</b> (int):  number of cores 


---

## <kbd>function</kbd> `multithread_pooling`

```python
multithread_pooling(fun, fun_param, n_threads)
```

Function to perform multiprocessing on n_threads 

**Args:**
 
 - <b>`fun`</b> (obj):  function to distribute 
 - <b>`fun_param zip(list)`</b>:  zip list of functino arguments 
 - <b>`n_core`</b> (int):  number of threads 


---

## <kbd>function</kbd> `get_versionning`

```python
get_versionning()
```






---

## <kbd>function</kbd> `FsmMetParser`

```python
FsmMetParser(file, freq='1h', resample=False)
```

Parses FSM forcing files from toposcale sims 


---

## <kbd>function</kbd> `FsmSnowParser`

```python
FsmSnowParser(file, freq='1H', resample=False)
```

parses FSM output fuiles 


---

## <kbd>function</kbd> `FsmPlot_ensemble`

```python
FsmPlot_ensemble(wdir, simvar, sampleN)
```

Function to plot ensemble results for a given variable and point. 



**Args:**
 
 - <b>`wdir`</b>:  full path to sim directory 
 - <b>`simvar`</b>:  variable to plot (str) 
 - <b>`sampleN`</b>:  sample number to plot 

**Returns:**
 
 - <b>`sampleN`</b>:  sample number 



**Example:**
 FsmPlot_ensemble('/home/joel/sim/topoPyscale_davos/', "HS", 0) 


---

## <kbd>function</kbd> `SmetParser`

```python
SmetParser(file, doresample=True, freq='1H', NA_val=-999)
```

val_file = full path to a smet resample = "TRUE" or "FALSE" freq = '1D' '1H' etc 


---

## <kbd>function</kbd> `getCoordinatePixel`

```python
getCoordinatePixel(map_path, x_coord, y_coord, epsg_in, epsg_out)
```

Function to find which sample a point exists in. Can accept any combination of projections of the map and points. 



**Args:**
 
 - <b>`map_path`</b>:  full path to map 
 - <b>`x_coord`</b>:  x coord of point 
 - <b>`y_coord`</b>:  y coord of point 
 - <b>`epsg_in`</b>:  input proj epsg code (lonlat: 4326) 
 - <b>`epsg_out`</b>:  ouput proj epsg code 



**Returns:**
 
 - <b>`sampleN`</b>:  sample number 



**Example:**
 # get epsg of map from TopoPyScale import topo_da as da epsg_out, bbxox = da.projFromLandform(map_path) 

getCoordinatePixel("/home/joel/sim/topoPyscale_davos/landform.tif", 9.80933, 46.82945, 4326, 32632) 


---

## <kbd>function</kbd> `val_plots`

```python
val_plots()
```








---

_This file was automatically generated via [lazydocs](https://github.com/ml-tooling/lazydocs)._
