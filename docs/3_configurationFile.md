# Project Configuration

## Project Organisation

To run a TopoPyScale project, you need to have the following file structure:

```
my_project/
    ├── inputs/
        ├── dem/ 
            ├── my_dem.tif
            └── pts_list.csv  (optional)
        └── climate/
            ├── PLEV*.nc
            └── SURF*.nc
    ├── outputs/
            ├── tmp/
    └── config.yml
```

## File `config.yml`

The configuration file contains all parameters needed to run a downscaling work. It includes general information about the job, as well as specific routine and values. Examples of `config.yml` file can be found in the repository[TopoPyScale_examples](https://github.com/ArcticSnow/TopoPyScale_examples).

The configuration consists of a YAML file, which is a common standard for storing configurations. Further help on YAML syntax can be found [here](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html), and the Python packages [pyyaml](https://pyyaml.org/wiki/PyYAMLDocumentation) and [Munch](https://pypi.org/project/munch/) allows to interact with such kind of file.

For TopoPyScale, the configuration file must contain at least the sections:

```yaml
project:
    name: Name of the project
    description: Describe the project
    authors:
        - Author 1 (can add contact and affiliation here)
        - Author 2
        - Author 3
    date: Date at which the project is ran. This is metadata
    directory: /path/to/project/

    # start and end date of the timeperiod of interest
    start: 2018-01-01   
    end: 2018-01-31
    split:
        IO: False       # Flag to split downscaling in time or not
        time: 2         # number of years to split timeline in
        space: None     # NOT IMPLEMENTED

    # This is for the option of fetching DEM with API (NOT YET SUPPORTED)
    extent:

    # Indicate the number of core to use
    CPU_cores: 4

    # indicate which climate data to use. Currently only era5 available (see climate section below)
    climate: era5

#.....................................................................................................
climate:
	# For now TopoPyScale only supports ERA5-reanalysis input climate data
    era5:
        path: inputs/climate/
        product: reanalysis
        timestep: 1H

        # Choose pressure levels relevant to your project and evailable in ERA5 Pressure Levels
        plevels: [700,750,775,800,825,850,875,900,925,950,975,1000]
        download_threads: 12    # Number of threads to request downloads with cdsapi
    precip_lapse_rate: True     # Apply precipitation lapse-rate correction (currently valid for Northern Hemisphere only)

#.....................................................................................................
dem:
    file: myDEM.tif                         # Name of the dem file. Must be a raster.
    epsg: 32632                             # projection EPSG code
    horizon_increments: 10                  # horizon increment angle in degrees

#.....................................................................................................
sampling:

	# choose downscaling using dem segmentation 'toposub' or a list of points 'points'. Possible values: toposub, points
    method: toposub

    # In case method == 'points', indicate a file with a list of points and the point coordinate projection EPSG code
    points:
        csv_file: pt_list.csv               # filename of list of points
        epsg: 4326                          # EPSG code of the points (x,y) coordinates in file

    # In case method == 'toposub'
    toposub:
        clustering_method: minibatchkmean   # clustering method available: kmean, minibatchkmean
        n_clusters: 50                      # number of cluster to segment the DEM
        random_seed: 2                      # random seed for the K-mean clustering 

#.....................................................................................................
toposcale:
    interpolation_method: idw               # interpolation methods available: linear or idw
    pt_sampling_method: nearest
    LW_terrain_contribution: True           # (bool)    Turn ON/OFF terrain contribution to longwave

#.....................................................................................................
outputs:
    variables: all                          # list or combination name
    file:
        clean_outputs: False                # (bool)    delete the entire outputs/ directory
        clean_FSM: True                     # (bool)    delete the entire sim/ directory
        df_centroids: df_centroids.pck      # (pickle)  dataframe containing the points of interest with their topographic features
        ds_param: ds_param.nc               # (netcdf)  topographic parameters (slope, aspect, etc.)
        ds_solar: ds_solar.nc               # (netcdf)  solar geometry
        da_horizon: da_horizon.nc           # (netcdf)  horizon angles
        landform: landform.tif              # (geotiff) rasters of of cluster labels, [TopoSub]
        downscaled_pt: down_pt_*.nc         # (netcdf)  Downscales 
```

The file `config.yml` is parsed by TopoPyScale at the time the class `topoclass('config.yml')` is created.

## File `csv` format for a list of points

The list of points is a comma-separated value file which must contain at least the fields `x,y`. All other columns will be loaded into a dataframe and can be used for further analysis (but won't be used by TopoPyScale).

An example of a list of points:
```csv
Name,stn_number,latitude,longitude,x,y
Finsevatne,SN25830,60.5938,7.527,419320.867306002,6718447.86246835
Fet-I-Eidfjord,SN49800,60.4085,7.2798,405243.856317655,6698143.36494597
Skurdevikåi,SN29900,60.3778,7.5693,421114.679132306,6694343.36865902
Midtstova,SN53530,60.6563,7.2755,405730.30171528,6725742.26010349
FV50-Vestredalen,SN53990,60.7418,7.5748,422296.164018722,6734871.61164008
Klevavatnet,SN53480,60.7192,7.2085,402259.379226592,6732844.21093029
```




