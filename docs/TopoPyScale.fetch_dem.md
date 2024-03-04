<!-- markdownlint-disable -->

# <kbd>module</kbd> `TopoPyScale.fetch_dem`
Methods to fetch DEM from various public repository 



**TODO:**
 
- [ ] SRTM 
- [ ] ArcticDEM 
- [ ] ASTER dem 
- [ ] Norwegian DEM 
- [x] Copernicus DEM 


---

## <kbd>function</kbd> `fetch_copernicus_dem`

```python
fetch_copernicus_dem(
    directory='.',
    extent=[23, 24, 44, 45],
    product='COP-DEM_GLO-90-DTED/2023_1'
)
```

Routine to downlaod Copernicus DEM product for a given extent 



**Args:**
 
 - <b>`directory`</b> (str, optional):  _description_. Defaults to '.'. 
 - <b>`extent`</b> (list, optional):  extent in [east, west, south, north]. Defaults to [23,24,44,45]. 
 - <b>`product`</b> (str, optional):  name of product to download. Default is 'COP-DEM_GLO-90-DTED/2023_1' 


---

## <kbd>function</kbd> `fetch_dem`

```python
fetch_dem(dem_dir, extent, dem_epsg, dem_file, dem_resol=None)
```

Function to fetch DEM data from SRTM and potentially other sources 



**Args:**
 
 - <b>`dem_dir`</b> (str):  path to dem folder 
 - <b>`extent`</b> (dict):  list of spatial extent in lat-lon [latN, latS, lonW, lonE] 
 - <b>`epsg`</b> (int):  epsg projection code 
 - <b>`dem_file`</b> (str):  filename of the downloaded DEM. must be myfile.tif 


---

## <kbd>class</kbd> `copernicus_dem`

---> Class to download Publicly available Copernicus DEM products 



**Args:**
 
 - <b>`directory`</b> (str):  directory where to store downloads 

### <kbd>method</kbd> `__init__`

```python
__init__(directory='.', product=None)
```








---

### <kbd>method</kbd> `download_tiles_in_extent`

```python
download_tiles_in_extent(extent=[22, 28, 44, 45])
```

Function to download tiles falling into the extent requested 



**Args:**
 
 - <b>`extent`</b> (list, int):  [east, west, south, north] longitudes and latitudes of the extent of interest. Defaults to [22,28,44,45]. 



**Returns:**
 
 - <b>`dataframe`</b>:  dataframes of the tile properties (url, lat, lon, etc.) 

---

### <kbd>method</kbd> `extract_all_tar`

```python
extract_all_tar(dem_extension='dt2')
```





---

### <kbd>method</kbd> `fetch_copernicus_dem_product_list`

```python
fetch_copernicus_dem_product_list()
```





---

### <kbd>method</kbd> `request_tile_list`

```python
request_tile_list(fname_tile=None)
```

Function to  



**Args:**
 
 - <b>`product`</b> (_type_):  _description_ 
 - <b>`fname_tile`</b> (str, optional):  _description_. Defaults to 'tiles.csv'. 




---

_This file was automatically generated via [lazydocs](https://github.com/ml-tooling/lazydocs)._
