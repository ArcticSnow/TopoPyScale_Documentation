<!-- markdownlint-disable -->

# <kbd>module</kbd> `TopoPyScale.topo_plot`
Collectio of plotting functions for TopoPyScale S. Filhol, December 2021 


---

## <kbd>function</kbd> `plot_unclustered_map`

```python
plot_unclustered_map(
    ds_down,
    ds_param,
    time_step=1,
    var='t',
    cmap=<matplotlib.colors.LinearSegmentedColormap object at 0x7f8bbf9539d0>
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
