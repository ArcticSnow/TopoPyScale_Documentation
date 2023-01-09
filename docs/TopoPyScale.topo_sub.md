<!-- markdownlint-disable -->

<a href="../docs/TopoPyScale/topo_sub#L0"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

# <kbd>module</kbd> `TopoPyScale.topo_sub`
Clustering routines for TopoSUB 

S. Filhol, Oct 2021 



**TODO:**
 
- explore other clustering methods available in scikit-learn: https://scikit-learn.org/stable/modules/clustering.html 
- look into DBSCAN and its relative 


---

<a href="../docs/TopoPyScale/topo_sub/ds_to_indexed_dataframe#L23"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `ds_to_indexed_dataframe`

```python
ds_to_indexed_dataframe(ds)
```

Function to convert an Xarray dataset with multi-dimensions to indexed dataframe (and not a multilevel indexed dataframe). WARNING: this only works if the variable of the dataset have all the same dimensions! 

By default the ds.to_dataframe() returns a multi-index dataframe. Here the coordinates are transfered as columns in the dataframe 



**Args:**
 
 - <b>`ds`</b> (dataset):  xarray dataset with all variable of same number of dimensions 



**Returns:**
 pandas dataframe:  


---

<a href="../docs/TopoPyScale/topo_sub/scale_df#L40"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `scale_df`

```python
scale_df(df_param, scaler=StandardScaler())
```

Function to scale features of a pandas dataframe 



**Args:**
 
 - <b>`df_param`</b> (dataframe):  features to scale 
 - <b>`scaler`</b> (scaler object):  Default is StandardScaler() 



**Returns:**
 
 - <b>`dataframe`</b>:  scaled data 


---

<a href="../docs/TopoPyScale/topo_sub/inverse_scale_df#L56"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `inverse_scale_df`

```python
inverse_scale_df(df_scaled, scaler)
```

Function to inverse feature scaling of a pandas dataframe 



**Args:**
 
 - <b>`df_scaled`</b> (dataframe):  scaled data to transform back to original (inverse transfrom) 
 - <b>`scaler`</b> (scaler object):  original scikit learn scaler 



**Returns:**
 
 - <b>`dataframe`</b>:  data in original format 


---

<a href="../docs/TopoPyScale/topo_sub/kmeans_clustering#L72"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `kmeans_clustering`

```python
kmeans_clustering(df_param, n_clusters=100, seed=None, **kwargs)
```

Function to perform K-mean clustering 



**Args:**
 
 - <b>`df_param`</b> (dataframe):  features 
 - <b>`n_clusters`</b> (int):  number of clusters 
 - <b>`seed`</b> (int):  None or int for random seed generator 

**kwargs:**
 



**Returns:**
 
 - <b>`dataframe`</b>:  df_centers 
 - <b>`kmean object`</b>:  kmeans 
 - <b>`dataframe`</b>:  df_param 


---

<a href="../docs/TopoPyScale/topo_sub/minibatch_kmeans_clustering#L99"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `minibatch_kmeans_clustering`

```python
minibatch_kmeans_clustering(
    df_param,
    n_clusters=100,
    n_cores=4,
    seed=None,
    **kwargs
)
```

Function to perform mini-batch K-mean clustering 



**Args:**
 
 - <b>`df_param`</b> (dataframe):  features 
 - <b>`n_clusters`</b> (int):   number of clusters 
 - <b>`n_cores`</b> (int):  number of processor core 

**kwargs:**
 



**Returns:**
 
 - <b>`dataframe`</b>:  centroids 
 - <b>`kmean object`</b>:  kmean model 
 - <b>`dataframe`</b>:  labels of input data 


---

<a href="../docs/TopoPyScale/topo_sub/plot_center_clusters#L127"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `plot_center_clusters`

```python
plot_center_clusters(
    dem_file,
    ds_param,
    df_centers,
    var='elevation',
    cmap=<matplotlib.colors.ListedColormap object at 0x7f9a6248d670>,
    figsize=(14, 10)
)
```

Function to plot the location of the cluster centroids over the DEM 



**Args:**
 
 - <b>`dem_file`</b> (str):  path to dem raster file 
 - <b>`ds_param`</b> (dataset):  topo_param parameters ['elev', 'slope', 'aspect_cos', 'aspect_sin', 'svf'] 
 - <b>`df_centers`</b> (dataframe):  containing cluster centroid parameters ['x', 'y', 'elev', 'slope', 'aspect_cos', 'aspect_sin', 'svf'] 
 - <b>`var`</b> (str):  variable to plot as background 
 - <b>`cmap`</b> (pyplot cmap):  pyplot colormap to represent the variable. 


---

<a href="../docs/TopoPyScale/topo_sub/plot_pca_clusters#L156"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `plot_pca_clusters`

```python
plot_pca_clusters(
    dem_file,
    df_param,
    df_centroids,
    scaler,
    n_components,
    subsample=3
)
```






---

<a href="../docs/TopoPyScale/topo_sub/write_landform#L183"><img align="right" style="float:right;" src="https://img.shields.io/badge/-source-cccccc?style=flat-square"></a>

## <kbd>function</kbd> `write_landform`

```python
write_landform(dem_file, df_param, project_directory='./')
```

Function to write a landform file which maps cluster ids to dem pixels 



**Args:**
 
 - <b>`dem_file`</b> (str):  path to dem raster file 
 - <b>`ds_param`</b> (dataset):  topo_param parameters ['elev', 'slope', 'aspect_cos', 'aspect_sin', 'svf'] 




---

_This file was automatically generated via [lazydocs](https://github.com/ml-tooling/lazydocs)._
