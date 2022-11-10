<!-- markdownlint-disable -->

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_plot#L0"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

# <kbd>module</kbd> `TopoPyScale.topo_plot`
Collectio of plotting functions for TopoPyScale S. Filhol, December 2021 


---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_plot/map__terrain#L12"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `map__terrain`

```python
map__terrain(ds_param, var='elevation', hillshade=True)
```

Function to plot terrain parameters 



**Args:**
  ds_param:  var:  hillshade: 



**Returns:**
 


---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_plot/map_unclustered#L49"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `map_unclustered`

```python
map_unclustered(
    ds_down,
    ds_param,
    time_step=1,
    var='t',
    cmap=<matplotlib.colors.LinearSegmentedColormap object at 0x7ffa9a410970>,
    hillshade=True,
    **kwargs
)
```

Function to plot unclustered downscaled points given that each point corresponds to a cluster label 



**Args:**
  ds_down:  ds_param:  time_step:  var:  cmap: 
 - <b>`**kwargs`</b>:  kwargs to pass to imshow() in dict format. 



**TODO:**
 
- if temperature, divergent colorscale around 0degC 
- see if we can remain within xarray dataset/dataarray to reshape and include x,y 




---

_This file was automatically generated via [lazydocs](https://github.com/ml-tooling/lazydocs)._
