# Installation

## Python Environment Preparation
`TopoPyScale` is tested for Python 3.9. You may create a new virtual environment using conda prior to installation.

**Option 1 (recommended):**
```bash
wget https://raw.githubusercontent.com/ArcticSnow/TopoPyScale/main/environment.yml
conda env create -f environment.yml
rm environment.yml
```
We recommend this option as it will install an environment with librarie versions compatible with the latest release.

**Option 2:**
```bash
conda create -n downscaling python=3.9 ipython
conda activate downscaling

# Recomended way to install dependencies:
conda install -c conda-forge xarray matplotlib scikit-learn pandas numpy netcdf4 h5netcdf rasterio pyproj dask
```
WARNING: in case dependencies have been updated, there might be incompatibilities. 

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

Go to [Development page](./08_Development.md)


