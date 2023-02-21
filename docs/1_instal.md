# Installation

## Python Environment Preparation
`TopoPyScale` is tested for Python 3.8. You may create a new virtual environment using conda prior to installation.

```bash
conda create -n downscaling python=3.8 ipython
conda activate downscaling

# Recomended way to install dependencies:
conda install -c conda-forge xarray matplotlib scikit-learn pandas numpy netcdf4 h5netcdf rasterio pyproj dask
```

## Latest Release Installation

```bash
pip install topopyscale
```

TopoPyScale has been tested on the OS:
- [x] Linux Ubuntu
- [ ] MacOS
- [ ] Windows

## Setting up `cdsapi`

Then you need to setup your `cdsapi` with the Copernicus API key system. Follow [this tutorial](https://cds.climate.copernicus.eu/api-how-to#install-the-cds-api-key) after creating an account with [Copernicus](https://cds.climate.copernicus.eu/). On Linux, create a file `nano ~/.cdsapirc` with inside:

```
url: https://cds.climate.copernicus.eu/api/v2
key: {uid}:{api-key}
```

## Development version Installation

```bash

cd github  # navigate to where you want to clone TopoPyScale
git clone git@github.com:ArcticSnow/TopoPyScale.git
pip install -e TopoPyScale    #install a development version, remove the -e for normal install

#----------------------------------------------------------
#            OPTIONAL: if using jupyter lab
# add this new Python kernel to your jupyter lab PATH
python -m ipykernel install --user --name downscaling

# OPTIONAL: To be able to compile the documentation locally
pip install lazydocs
git clone git@github.com:ArcticSnow/TopoPyScale_Documentation.git
```


