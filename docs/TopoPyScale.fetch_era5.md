<!-- markdownlint-disable -->

# <kbd>module</kbd> `TopoPyScale.fetch_era5`
Retrieve ecmwf data with cdsapi. 


- J. Fiddes, Origin implementation 
- S. Filhol adapted in 2021 


---

## <kbd>function</kbd> `retrieve_era5`

```python
retrieve_era5(
    product,
    startDate,
    endDate,
    eraDir,
    latN,
    latS,
    lonE,
    lonW,
    step,
    num_threads=10,
    surf_plev='surf',
    plevels=None,
    realtime=False
)
```

Sets up era5 surface retrieval. * Creates list of year/month pairs to iterate through.  * MARS retrievals are most efficient when subset by time.  * Identifies preexisting downloads if restarted.  * Calls api using parallel function. 



**Args:**
 
 - <b>`product`</b>:  "reanalysis" (HRES) or "ensemble_members" (EDA) startDate: endDate: 
 - <b>`eraDir`</b>:  directory to write output 
 - <b>`latN`</b>:  north latitude of bbox 
 - <b>`latS`</b>:  south latitude of bbox 
 - <b>`lonE`</b>:  easterly lon of bbox 
 - <b>`lonW`</b>:  westerly lon of bbox 
 - <b>`step`</b>:  timestep to use: 1, 3, 6 
 - <b>`num_threads`</b>:  number of threads to use for downloading data 
 - <b>`surf_plev`</b>:  download surface single level or pressure level product: 'surf' or 'plev' 



**Returns:**
 Monthly era surface files stored in disk.                 


---

## <kbd>function</kbd> `era5_request_surf`

```python
era5_request_surf(dataset, year, month, bbox, target, product, time)
```

CDS surface api call 



**Args:**
 
 - <b>`dataset`</b> (str):  copernicus dataset (era5) 
 - <b>`year`</b> (str or list):  year of interest 
 - <b>`month`</b> (str or list):  month of interest 
 - <b>`bbox`</b> (list):  bonding box in lat-lon 
 - <b>`target`</b> (str):  filename 
 - <b>`product`</b> (str):  type of model run. defaul: reanalysis 
 - <b>`time`</b> (str or list):  hours for which to download data  



**Returns:**
 Store to disk dataset as indicated 


---

## <kbd>function</kbd> `era5_request_plev`

```python
era5_request_plev(dataset, year, month, bbox, target, product, time, plevels)
```

CDS plevel api call 



**Args:**
 
 - <b>`dataset`</b> (str):  copernicus dataset (era5) 
 - <b>`year`</b> (str or list):  year of interest 
 - <b>`month`</b> (str or list):  month of interest 
 - <b>`bbox`</b> (list):  bonding box in lat-lon 
 - <b>`target`</b> (str):  filename 
 - <b>`product`</b> (str):  type of model run. defaul: reanalysis 
 - <b>`time`</b> (str or list):  hours to query 
 - <b>`plevels`</b> (str or list):  pressure levels to query 



**Returns:**
 Store to disk dataset as indicated 


---

## <kbd>function</kbd> `era5_realtime_surf`

```python
era5_realtime_surf(eraDir, dataset, bbox, product)
```






---

## <kbd>function</kbd> `era5_realtime_plev`

```python
era5_realtime_plev(eraDir, dataset, bbox, product, plevels)
```






---

## <kbd>function</kbd> `return_last_fullday`

```python
return_last_fullday()
```








---

_This file was automatically generated via [lazydocs](https://github.com/ml-tooling/lazydocs)._
