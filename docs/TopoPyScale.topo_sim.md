<!-- markdownlint-disable -->

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_sim.py#L0"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

# <kbd>module</kbd> `TopoPyScale.topo_sim`
Methods to generate required simulation files and run simulations of various models using tscale forcing J. Fiddes, February 2022 



**TODO:**
 


---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_sim.py#L22"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `fsm_nlst`

```python
fsm_nlst(nconfig, metfile, nave)
```

Function to generate namelist parameter file that is required to run the FSM model. https://github.com/RichardEssery/FSM 



**Args:**
 
 - <b>`nconfig`</b> (int):  which FSm configuration to run (integer 1-31) 
 - <b>`metfile`</b> (str):  path to input tscale file (relative as Fortran fails with long strings (max 21 chars?)) 
 - <b>`nave`</b> (int):  number of forcing steps to average output over eg if forcing is hourly and output required is daily then nave = 24 



**Returns:**
 NULL (writes out namelist text file which configures a single FSM run) 



**Notes:**

> constraint is that Fortran fails with long strings (max?) definition: https://github.com/RichardEssery/FSM/blob/master/nlst_CdP_0506.txt 
>
>
>Example nlst: &config / &drive met_file = 'data/met_CdP_0506.txt' zT = 1.5 zvar = .FALSE. / &params / &initial Tsoil = 282.98 284.17 284.70 284.70 / &outputs out_file = 'out_CdP_0506.txt' / 


---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_sim.py#L84"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `txt2ds`

```python
txt2ds(fname)
```

Function to read a single FSM text file output as a xarray dataset 

**Args:**
 
 - <b>`fname`</b> (str):  filename 



**Returns:**
 xarray dataset of dimension (time, point_id) 


---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_sim.py#L113"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `to_dataset`

```python
to_dataset(fname_pattern='sim_FSM_pt*.txt', fsm_path='./fsm_sims/')
```

Function to read FSM outputs of one simulation into a single dataset. 

**Args:**
  fname_pattern:  fsm_path: 



**Returns:**
 


---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_sim.py#L141"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `read_pt_fsm`

```python
read_pt_fsm(fname)
```

Function to load FSM simulation output into a pandas dataframe 

**Args:**
 
 - <b>`fname`</b> (str):  path to simulation file to open 



**Returns:**
 pandas dataframe 


---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_sim.py#L160"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `fsm_sim`

```python
fsm_sim(nlstfile, fsm_exec)
```

Function to simulate the FSM model https://github.com/RichardEssery/FSM 



**Args:**
 
 - <b>`nlstfile`</b> (int):  which FSm configuration to run (integer 1-31) 
 - <b>`fsm_exec`</b> (str):  path to input tscale file (relative as Fortran fails with long strings (max 21 chars?)) 



**Returns:**
 NULL (FSM simulation file written to disk) 


---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_sim.py#L180"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `agg_by_var_fsm`

```python
agg_by_var_fsm(ncol=None, var='gst', fsm_path='./fsm_sims')
```

Function to make single variable multi cluster files as preprocessing step before spatialisation. This is much more efficient than looping over individual simulation files per cluster. For V variables , C clusters and T timesteps this turns C individual files of dimensions V x T into V individual files of dimensions C x T. 

Currently written for FSM files but could be generalised to other models. 



**Args:**
 
 - <b>`ncol`</b> (int):  column number of variable to extract 

**Returns:**
 NULL ( file written to disk) 

ncol: 4 = rof 5 = hs 6 = swe 7 = gst 


---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_sim.py#L253"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `agg_by_var_fsm_ensemble`

```python
agg_by_var_fsm_ensemble(ncol=None, var='gst', W=1)
```

Function to make single variable multi cluster files as preprocessing step before spatialisation. This is much more efficient than looping over individual simulation files per cluster. For V variables , C clusters and T timesteps this turns C individual files of dimensions V x T into V individual files of dimensions C x T. 

Currently written for FSM files but could be generalised to other models. 



**Args:**
 
 - <b>`ncol`</b> (int):  column number of variable to extract W (): 

**Returns:**
 NULL ( file written to disk) 

ncol: 4 = rof 5 = hs 6 = swe 7 = gst 


---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_sim.py#L337"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `timeseries_means_period`

```python
timeseries_means_period(df, start_date, end_date)
```

Function to extract results vectors from simulation results. This can be entire time period some subset or sing day. 



**Args:**
 
 - <b>`df`</b> (dataframe):  results df 
 - <b>`start_date`</b> (str):  start date of average (can be used to extract single day) '2020-01-01' 
 - <b>`end_date`</b> (str):  end date of average (can be used to extract single day) '2020-01-03' 



**Returns:**
 
 - <b>`dataframe`</b>:  averaged dataframe 


---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_sim.py#L369"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `topo_map`

```python
topo_map(df_mean, mydtype, outname='outputmap.tif')
```

Function to map results to toposub clusters generating map results. 



**Args:**
 
 - <b>`df_mean`</b> (dataframe):  an array of values to map to dem same length as number of toposub clusters 
 - <b>`mydtype`</b>:  HS (maybeGST) needs "float32" other vars can use "int16" to save space 

Here 's an approach for arbitrary reclassification of integer rasters that avoids using a million calls to np.where. Rasterio bits taken from @Aaron' s answer: https://gis.stackexchange.com/questions/163007/raster-reclassify-using-python-gdal-and-numpy 


---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_sim.py#L413"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `topo_map_headless`

```python
topo_map_headless(df_mean, mydtype, outname='outputmap.tif')
```

Headless server version of Function to map results to toposub clusters generating map results. 



**Args:**
 
 - <b>`df_mean`</b> (dataframe):  an array of values to map to dem same length as number of toposub clusters 
 - <b>`mydtype`</b>:  HS (maybeGST) needs "float32" other vars can use "int16" to save space 

Here 's an approach for arbitrary reclassification of integer rasters that avoids using a million calls to np.where. Rasterio bits taken from @Aaron' s answer: https://gis.stackexchange.com/questions/163007/raster-reclassify-using-python-gdal-and-numpy 


---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_sim.py#L453"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `topo_map_forcing`

```python
topo_map_forcing(ds_var, n_decimals=2, dtype='float32', new_res=None)
```

Function to map forcing to toposub clusters generating gridded forcings 



**Args:**
 
 - <b>`ds_var`</b>:  single variable of ds eg. mp.downscaled_pts.t 
 - <b>`n_decimals`</b> (int):  number of decimal to round vairable. default 2 
 - <b>`dtype`</b> (str):  dtype to export raster. default 'float32' 
 - <b>`new_res`</b> (float):  optional parameter to resample output to (in units of projection 

Return: 
 - <b>`grid_stack`</b>:  stack of grids with dimension Time x Y x X 

Here 's an approach for arbitrary reclassification of integer rasters that avoids using a million calls to np.where. Rasterio bits taken from @Aaron' s answer: https://gis.stackexchange.com/questions/163007/raster-reclassify-using-python-gdal-and-numpy 


---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_sim.py#L549"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `write_ncdf`

```python
write_ncdf(wdir, grid_stack, var, units, longname, mytime, lats, lons, mydtype)
```






---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_sim.py#L595"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `agg_stats`

```python
agg_stats(df)
```






---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_sim.py#L620"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `climatology`

```python
climatology(ncol, fsm_path)
```






---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_sim.py#L633"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `climatology_plot`

```python
climatology_plot(
    mytitle,
    HSdf_daily_median,
    HSdf_daily_quantiles,
    HSdf_realtime=None,
    plot_show=False
)
```








---

_This file was automatically generated via [lazydocs](https://github.com/ml-tooling/lazydocs)._
