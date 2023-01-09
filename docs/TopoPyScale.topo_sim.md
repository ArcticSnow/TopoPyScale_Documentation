<!-- markdownlint-disable -->

<a href="../docs/TopoPyScale/topo_sim#L0"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

# <kbd>module</kbd> `TopoPyScale.topo_sim`
Methods to generate required simulation files and run simulations of various models using tscale forcing J. Fiddes, February 2022 



**TODO:**
 


---

<a href="../docs/TopoPyScale/topo_sim/fsm_nlst#L19"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

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

<a href="../docs/TopoPyScale/topo_sim/fsm_sim#L81"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

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

<a href="../docs/TopoPyScale/topo_sim/agg_by_var_fsm#L98"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `agg_by_var_fsm`

```python
agg_by_var_fsm(ncol)
```

Function to make single variable multi cluster files as preprocessing step before spatialisation. This is much more efficient than looping over individual simulation files per cluster. For V variables , C clusters and T timesteps this turns C individual files of dimensions V x T into V individual files of dimensions C x T. 

Currently written for FSM files but could be generalised to other models. 



**Args:**
 
 - <b>`ncol`</b> (int):  column number of variable to extract 

**Returns:**
 NULL ( file written to disk) 

ncol: 4 = rof 5 = hs 6 = swe 7 = gst 


---

<a href="../docs/TopoPyScale/topo_sim/agg_by_var_fsm_ensemble#L162"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `agg_by_var_fsm_ensemble`

```python
agg_by_var_fsm_ensemble(ncol, W)
```

Function to make single variable multi cluster files as preprocessing step before spatialisation. This is much more efficient than looping over individual simulation files per cluster. For V variables , C clusters and T timesteps this turns C individual files of dimensions V x T into V individual files of dimensions C x T. 

Currently written for FSM files but could be generalised to other models. 



**Args:**
 
 - <b>`ncol`</b> (int):  column number of variable to extract 

**Returns:**
 NULL ( file written to disk) 

ncol: 4 = rof 5 = hs 6 = swe 7 = gst 


---

<a href="../docs/TopoPyScale/topo_sim/timeseries_means_period#L240"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

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

<a href="../docs/TopoPyScale/topo_sim/topo_map#L271"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `topo_map`

```python
topo_map(df_mean, outname='outputmap.tif')
```

Function to map results to toposub clusters generating map results. 



**Args:**
 
 - <b>`df_mean`</b> (dataframe):  an array of values to map to dem same length as number of toposub clusters 

Here 's an approach for arbitrary reclassification of integer rasters that avoids using a million calls to np.where. Rasterio bits taken from @Aaron' s answer: https://gis.stackexchange.com/questions/163007/raster-reclassify-using-python-gdal-and-numpy 


---

<a href="../docs/TopoPyScale/topo_sim/topo_map_forcing#L314"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `topo_map_forcing`

```python
topo_map_forcing(ds_var, round_dp, mydtype, new_res=None)
```

Function to map forcing to toposub clusters generating gridded forcings 



**Args:**
 
 - <b>`ds_var`</b>:  single variable of ds eg. mp.downscaled_pts.t 
 - <b>`new_res`</b>:  optional parameter to resample output to (in units of projection 

Return: 
 - <b>`grid_stack`</b>:  stack of grids with dimension Time x Y x X 

Here 's an approach for arbitrary reclassification of integer rasters that avoids using a million calls to np.where. Rasterio bits taken from @Aaron' s answer: https://gis.stackexchange.com/questions/163007/raster-reclassify-using-python-gdal-and-numpy 


---

<a href="../docs/TopoPyScale/topo_sim/write_ncdf#L408"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `write_ncdf`

```python
write_ncdf(wdir, grid_stack, var, units, longname, mytime, lats, lons, mydtype)
```








---

_This file was automatically generated via [lazydocs](https://github.com/ml-tooling/lazydocs)._
