<!-- markdownlint-disable -->

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_obs#L0"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

# <kbd>module</kbd> `TopoPyScale.topo_obs`
Tools to download and compare Downsclaed timeseries to observation All observation in folder inputs/obs/ S. Filhol December 2021 


---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_obs/get_metno_obs#L12"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `get_metno_obs`

```python
get_metno_obs(
    sources,
    voi,
    start_date,
    end_date,
    client_id='97a0e2bc-a262-48fe-9dea-5e9c894e9328'
)
```

Function to download observation data from MetNo FROST API (Norwegian Meteorological institute) 

Args  sources (list): station code, e.g. 'SN25830'  voi (list): variables to download  start_date (str): starting date  end_date (str): ending date  client_id (str): FROST_API_CLIENTID 

Return:   dataframe: all data combined together 

List of variable: https://frost.met.no/element table Find out about stations: https://seklima.met.no/  WARNING: Download max one year at the time to not reach max limit of data to download. 



**TODO:**
 
- convert df to xarray dataset with stn_id, time as coordinates 


---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_obs/combine_metno_obs_to_xarray#L71"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `combine_metno_obs_to_xarray`

```python
combine_metno_obs_to_xarray(fnames='metno*.pckl', path='inputs/obs/')
```

Function to convert metno format to usable dataset 



**Args:**
 
 - <b>`fnames`</b> (str pattern):  pattern of the file to load 
 - <b>`path`</b> (str):  path of the file to load 



**Returns:**
 
 - <b>`dataset`</b>:  dataset will all data organized in timeseries and station number 




---

_This file was automatically generated via [lazydocs](https://github.com/ml-tooling/lazydocs)._
