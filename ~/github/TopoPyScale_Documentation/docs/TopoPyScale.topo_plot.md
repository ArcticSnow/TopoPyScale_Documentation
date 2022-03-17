<!-- markdownlint-disable -->

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_plot#L0"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

# <kbd>module</kbd> `TopoPyScale.topo_plot`
Collectio of plotting functions for TopoPyScale S. Filhol, December 2021 


---

<a href="https://github.com/ArcticSnow/TopoPyScale/TopoPyScale/topo_plot/plot_unclustered_map#L10"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `plot_unclustered_map`

```python
plot_unclustered_map(
    ds_down,
    ds_param,
    time_step=1,
    var='t',
    cmap=<matplotlib.colors.LinearSegmentedColormap object at 0x7ff2d07c7a30>
)
```

Function to plot unclustered downscaled points given that each point corresponds to a cluster label 



**Args:**
  ds_down:  ds_param:  time_step:  var:  cmap: 



**TODO:**
 
- if temperature, divergent colorscale around 0degC 
- see if we can remain within xarray dataset/dataarray to reshape and include x,y 




---

_This file was automatically generated via [lazydocs](https://github.com/ml-tooling/lazydocs)._
