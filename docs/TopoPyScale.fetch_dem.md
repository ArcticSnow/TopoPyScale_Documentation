<!-- markdownlint-disable -->

<a href="../docs/TopoPyScale/fetch_dem#L0"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

# <kbd>module</kbd> `TopoPyScale.fetch_dem`
Methods to fetch DEM from various public repository 



**TODO:**
 
- [ ] SRTM 
- [ ] ArcticDEM 
- [ ] ASTER dem 
- [ ] Norwegian DEM 


---

<a href="../docs/TopoPyScale/fetch_dem/fetch_dem#L15"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

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
