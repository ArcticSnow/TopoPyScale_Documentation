<!-- markdownlint-disable -->

# <kbd>module</kbd> `TopoPyScale.fetch_dem`
Methods to fetch DEM from various public repository 



**TODO:**
 
- [ ] SRTM 
- [ ] ArcticDEM 
- [ ] ASTER dem 
- [ ] Norwegian DEM 


---

## <kbd>function</kbd> `fetch_dem`

```python
fetch_dem(dem_dir, extent, dem_epsg, dem_file)
```

Function to fetch DEM data from SRTM and potentially other sources 



**Args:**
 
 - <b>`dem_dir`</b> (str):  path to dem folder 
 - <b>`extent`</b> (list):  list of spatial extent in lat-lon [latN, latS, lonW, lonE] 
 - <b>`epsg`</b> (int):  epsg projection code 
 - <b>`dem_file`</b> (str):  filename of the downloaded DEM. must be myfile.tif 




---

_This file was automatically generated via [lazydocs](https://github.com/ml-tooling/lazydocs)._
