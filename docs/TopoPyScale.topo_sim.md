<!-- markdownlint-disable -->

# <kbd>module</kbd> `TopoPyScale.topo_sim`
Methods to generate required simulation files and run simulations of various models using tscale forcing J. Fiddes, February 2022 



**TODO:**
 


---

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

## <kbd>function</kbd> `topo_map`

```python
topo_map(df_mean)
```

Function to map results to toposub clusters generating map results. 



**Args:**
 
 - <b>`df_mean`</b> (dataframe):  an array of values to map to dem same length as number of toposub clusters 



Here 's an approach for arbitrary reclassification of integer rasters that avoids using a million calls to np.where. Rasterio bits taken from @Aaron' s answer: https://gis.stackexchange.com/questions/163007/raster-reclassify-using-python-gdal-and-numpy 




---

_This file was automatically generated via [lazydocs](https://github.com/ml-tooling/lazydocs)._
