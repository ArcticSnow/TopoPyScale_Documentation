# Installation

## Release Installation
To install the latest release, in a virtual environment simply use `pip`

```bash
pip install topopyscale
```

## Development version Installation
To install the version in development:
- [x] tested on Linux Ubuntu
- [ ] tested on MacOS

```bash
conda install mamba -n base -c conda-forge
mamba create -n downscaling ipython numpy pandas xarray matplotlib netcdf4 ipykernel scikit-learn rasterio gdal pyproj munch
conda activate downscaling
pip install cdsapi
pip install h5netcdf
pip install topocalc
pip install pvlib
pip install elevation
pip install lazydocs

cd github  # navigate to where you want to clone TopoPyScale
git clone git@github.com:ArcticSnow/TopoPyScale.git
pip install -e TopoPyScale    #install a development version, remove the -e for normal install

#----------------------------------------------------------
#            OPTIONAL: if using jupyter lab
# add this new Python kernel to your jupyter lab PATH
python -m ipykernel install --user --name downscaling
```

## Setting up `cdsapi`

Then you need to setup your `cdsapi` with the Copernicus API key system. Follow [this tutorial](https://cds.climate.copernicus.eu/api-how-to#install-the-cds-api-key) after creating an account with [Copernicus](https://cds.climate.copernicus.eu/). On Linux, create a file `nano ~/.cdsapirc` with inside:

```
url: https://cds.climate.copernicus.eu/api/v2
key: {uid}:{api-key}
```