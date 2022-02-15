# Project Configuration

## Project Organisation

To run a TopoPyScale project, you need to have this

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

The configuration consists of YAML file, which is a common standard for storing configurations. Further help on YAML syntax can be found [here](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html), and the Python packages [pyyaml](https://pyyaml.org/wiki/PyYAMLDocumentation) and [Munch](https://pypi.org/project/munch/) allows to interact with such kind of file.

For TopoPyScale, the configuration file must contain at least the sections:

```yaml
project:
    name: Name of the project
    description: Describe the project
    authors:
        - Author 1 (can add contact and affiliation here)
        - Author 2
        - Author 3
    date: Date at which the project is ran
    directory: /path/to/project/

    # start and end date of the timeperiod of interest
    start: 2018-01-01   
    end: 2018-01-31

    # possibility to provide an extent in the format [latN, latS, lonW, lonE]. If empty then it uses extent of the DEM provided below
    extent: 
    CPU_cores: 4

    # indicate which climate data to use. Currently only era5 available (see climate section below)
    climate: era5

climate:
	# For now TopoPyScale only supports ERA5-reanalysis input climate data
    era5:
        path: inputs/climate/
        product: reanalysis
        timestep: 1H
        plevels: [700,750,775,800,825,850,875,900,925,950,975,1000]
        download_threads: 12

dem:
    file: myDEM.tif
    # projection EPSG code
    epsg: 32632
    # horizon increment angle in degrees
    horizon_increments: 10

sampling:
	# choose downscaling using toposub or a list of points. Possible values: toposub, points
    method: toposub
    points:
        csv_file: pt_list.csv
        epsg: 4326

    toposub:
    	# clustering method available: kmean, minibatchkmean
        clustering_method: minibatchkmean
        n_clusters: 50
        random_seed: 2

toposcale:
	# interpolation methods available: linear or idw
    interpolation_method: idw
    pt_sampling_method: nearest
    # Turn ON/OFF terrain contribution to longwave
    LW_terrain_contribution: True
```

The file `config.yml` is parsed by TopoPyScale at the time the class `topoclass('config.yml')` is created. As many config files can be created and used to 

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




