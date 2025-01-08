# Data Gap Analysis for Weather and Climate-Related AI/ML Applications

In order to contribute to this document, please fork the repository, make your changes, and submit a pull request. You are invited to contact the faciltators for providing feedback, content or requesting further information.

- **Roope Tervo**  
  EUMETSAT  
  roope.tervo@eumetsat.int

- **Arianna Valmassoi**  
  DWD  
  arianna.valmassoi@dwd.de

- **Stephan Siemen**  
  ECMWF  
  stephan.siemen@ecmwf.int


## Summary
This Data Gap Analysis for Weather and Climate-Related AI/ML Applications is part of the EUMETNET Artificial Intelligence (E-AI) Working Group 1 ('Data Curation') activities. Its primary goal is to identify key data requirements, gaps, and obstacles hindering the effective use of weather and climate data for AI/ML-based applications. 

Key data gaps include missing datasets such as cloud fraction data from high-resolution LEO satellites for Northern Europe and comprehensive icing observations in gridded formats. Additionally, long training datasets for MTG FCI and LI data as well as European-wide weather radar products like echo tops and hail detection remain unavailable.

Obstacles to data usage include slow download speeds, exotic and inconsistent data formats and time steps, lacking or complex geo-referencing, licensing restrictions, and incomplete temporal/geospatial coverage. The lack of real-time equivalents to Climate Data Records (CDRs) further limits AI/ML training capabilities.

Future avenues of this work include expanding the data inventory, providing usage examples, and curating best practices to make weather and climate data more AI-ready. Contributions and feedback from the community are encouraged to further refine this living document and support advancements in AI/ML applications for weather and climate science.

## Introduction

This analyses is part of EUMETNET Artificial Intelligence (E-AI) working group 1 ('data curation') activities. The goal of this document is to provide an overview of the data requirements and most significant gaps and obstacles in data usage in the context of weather and climate-related AI/ML applications. 

The document is composed by European  hydro-meteorological services and related reserarch organisations. The analyses is based on the use cases and data sources provided for this and other E-AI working groups and edited by the working group faciliators. The document is meant to be a living document and updated regularly.

## Data Requirements of Identified Use Cases
This chapter handles key requirements for data based on the use case analyses.

### Key Use Cases

This chapter summaries [use cases](./use_cases/) provided by the WG members along with known use cases from other sources. The goal is to provide an overview of the characteristics of the use cases to identify commonalities and key challenges in data usage.

<!-- Applications summary (table below), possibly to be divided per category in the future:
  - Meteorological data (e.g., temperature, humidity, pressure).
  - Climate data (e.g., long-term trends, sea-level changes).
  - Environmental data (e.g., land cover, aerosols).
  - Socioeconomic data (for impact and adaptation modeling). -->

  | Name | Link | Temporal Resolution | Domain | Geospatial Resolution | Used Data | Data Format | Platform | Key Challenges |
  |------|------|---------------------|-------------|----------|------------|-------------|----------|----------------|
  | CloudCast | [Description](../gap_analysis/use_cases/cloudcast.md) | 15 minutes | Northern Europe | 4x4 km | Effective cloudiness, ie. cloud fraction | Zarr | - | Poor quality and missing data  |
  | Icing forecast | [Description](use_cases/icing.md) | 1h | - |  2.5x2.5km | NWP/MEPS | Grib2  | - | - |
  | Earthformer | [Description](use_cases/multi_source_to_precipitation.md) | 5 min | Austria | 1x1km/2x2km | radar / SEVIRI / lightning / analyses | H5 --> tif | EWC | slow download |
  | Tropical storm detection | [Description](use_cases/tropical_storm_detection.md) | 30 minutes | Global | 5km | Infrared satellite images | GeoTiff | EWC | 1) Handling native format is challenging. 2) License restrictions for usage |
  | Weather front forecasts | [Description](use_cases/weather_front_analysis.md) | 3 hours | Europe / Global |  ~ 0.4° | ICON | Grib --> NetCDF | - | - |
  |Clear sky probability | planned EWC R&D project | 30 minutes | Global| ~5km | GeoRing | NetCDF/Zarr | EWC | - | 
  |Widlfire detection | planned EWC R&D project | 10 minutes | Global | ~2km | GOES-16/18, MTG, Himawari, EPS-SG | - | EWC | - | 
  |Marine heat waves detection Machine Learning | planned EWC R&D project | - | Northern Atlantic | 0.25x0.25deg | AVHRR, ATSR, SLSTR, ERA5, CMEMS global ocean eddy, NAO, ENSO | - | EWC | - |
  | Deep Learning Strategies for IASI based retrievals | EWC R&D project | - | Global | - | IASI, SEVIRI, AVHRR CF | - | EWC | - | 
  | Machine Learning applications for Post-Processing of NWP model output | - | - | Italy |  28x28km | NWP, ERA5 |  - | EWC | - | 
  | ML-based cloud retrieval | EWC R&D project | - | - |  - | DISAMAR simulations, GOME-2, S4, S5, 3MI |  - | EWC | All necessary data not available yet | 
  | Early fog and thunderstorm detection | [Description](use_cases/CNMCA-SRNWP-EPS_specs.md) | 1 hour | - | 3x3km | COSMO, NWC SAF RDT, METAR |  CSV, NetCDF, GRIB | - | Inconsistent time steps, missing fog prediction data |

### Joined Characteristics

There are no enough use cases to draw trustwrothy synthesis, but preliminary folllowing things can be stated: 

- Preferred access mechanism is S3
- Preferred data format is controversial
- Temporal and geospatial resolution varies greatly depending on the use cases

## Current Data Inventory

This chapter list most typically used data sources for E-AI applications with necessary details to identify potential challenges with existing data or missing data. Readers are invited to add their data source to the tables.

Also [MLCast](https://docs.google.com/document/d/1iknFj36XdV19udaIsYJhVJLv2Hq-ARjO85jD0jfrYqw/edit?usp=sharing) and [ML LAM](https://docs.google.com/document/d/1KzMHjl08ESMSpEwJ1eopbWfBp_2MXL-XL63KljWQCZU/edit?usp=sharing) working group documents list typically used datasets. 

### Reanalyses

Reanalyses are a key dataset for early ML, since they provide a gridded physically consistent dataset that has no spatial (neither in the vertical nor in the horizontal) or temporal gap.

The available products can be divided between global and regional reanalyses, based on their spatial coverage.

#### Global Reanalyses
The current available global reanalyses are summarized below.

| Data Type | Realtime Service | Archive | License | Resolution | Format | Time Range | Time Step | Challenges |
|-----------|-----------------|---------|---------|------------|--------|------------|-----------|------------|
| ERA5 |  5-days delay | [C3S](link) | [Licence](https://apps.ecmwf.int/datasets/licences/copernicus/) | 30km (9km ERA-Land) | GRIB/NetCDF | 1940 onwards | 1 hour | Low resolution |
| JRA-55 |  no (1958 - 2024) | [JRA](https://jra.kishou.go.jp/JRA-55/index_en.html) |  [Licence](https://search.diasjp.net/en/dataset/JRA55) | 55km |  | 1958-01-01 - 2024-02-02  | 3/6 hour | Discontinued |
| JRA-3Q |  - |  [Licence](https://search.diasjp.net/en/dataset/JRA3Q) | [JRA-3Q](DOI:10.20783/DIAS.645) | 40km  | [Variables and format](https://jra.kishou.go.jp/JRA-3Q/document/JRA-3Q_LL125_format_en.pdf) | 1947-09-01 onwards | ? hour | Low resolution |
| MERRA-2 | 15th of the next month | [Access](https://gmao.gsfc.nasa.gov/reanalysis/MERRA-2/WMO_climate_reanalysis/) | [Licence](https://gmao.gsfc.nasa.gov/reanalysis/MERRA-2/citing_MERRA-2/)   | 0.5° × 0.625°  | [Variables and format](https://gmao.gsfc.nasa.gov/reanalysis/MERRA-2/citing_MERRA-2/) | 1980 onwards | 1/3 hour | Low resolution |
| ICON-DREAM |  ? | ? |  CC-BY4.0 | 13km  | ? | 2010 onwards | 1 hour | ? |

ICON-DREAM is included in the available reanalyses even if the data sharing and paper publication is still ongoing.

The planned global reanalyses are summarized below.

| Data Type |  Planned production start | License | Resolution | Format | Time Range | Time Step | Challenges |
|-----------|-----------------|---------|------------|--------|------------|-----------|------------|
| ERA6 |   Q2 2026 | [Licence](https://apps.ecmwf.int/datasets/licences/copernicus/) | 14km () |  | 1940 onwards | 1 hour | ? |
| MERRA-21C |  2027/2028 | - | -  | - | - | - | - |
| ICON-DREAM |  2026 | - | 13km  |  | 1980 onwards | 1 hour | ? |

While the planned ERA6 and MERRA-21C include an update of the whole system, the ICON-DREAM is only a back-extension and no major updates are planned.
MERRA-21C has no planned start, as the system is currently being tested, including the possibility of adding an ensemble to it.

A major challenge for the current global reanalyses is the impossibility to assess uncertainty as only ERA5 provides an ensemble, prior to ICON-DREAM.
Furthermore, the ERA5 ensemble is only meant to sample the observations uncertainties, as it perturbs the observational error.

ICON-DREAM provides a 20-ensemble members (ERA5/ERA6 10), which includes physical perturbations and parameter perturbations. However, the challenge lies in sharing this data volume.

#### European Regional Reanalyses

One of the main limitations for the regional reanalyses production is that they rely on the global reanalyses to provide the boundary conditions.
Therefore, the current system currently used in the numerical weather forecast needs to be adapted for a reduced/lack of ensemble.


| Data Type | Realtime Service | Archive | License | Resolution | Format | Time Range | Time Step | Challenges |
|-----------|-----------------|---------|---------|------------|--------|------------|-----------|------------|
| COSMO-REA6 |  no | [DWD](https://opendata.dwd.de/climate_environment/REA/COSMO_REA6/) | [Licence](https://data.opendatascience.eu/geonetwork/srv/api/records/4d6f6090-c242-454b-9224-1151f7ae2823) | 6km | [grib2 to netcdf](https://opendata.dwd.de/climate_environment/REA/COSMO_REA6/help_COSMO_REA6/Convert_REA6_data.pdf) | 1995-2019 | 1 hour/15 minutes | Not extended, .. |
| HARMONIE-UERRA | no | [CDS](https://cds.climate.copernicus.eu/datasets/reanalysis-uerra-europe-single-levels?tab=overview) | [CDS](https://cds.climate.copernicus.eu/datasets/reanalysis-uerra-europe-single-levels?tab=overview) | 9km | grib2 | 1961-2019 | 6 hours | ? |
| CERRA |  [Refer to here](https://climate.copernicus.eu/copernicus-regional-reanalysis-europe-cerra) | [Info](https://climate.copernicus.eu/copernicus-regional-reanalysis-europe-cerra) | [Info](https://climate.copernicus.eu/copernicus-regional-reanalysis-europe-cerra) | 5.5km |  | 1984 onwards | 1 hour? | ? |
| ICON-DREAM |  ? | - | CC-BY4.0 | 6.5km | grib2? | 2010 onwards | 1 hour | ? |

The ICON-DREAM reanalyses is the 2-way nest over Europe of the global reanalyses previously described.

The challenge with our regional reanalyses is that:
1. very few are continued, i.e. CERRA, ICON-DREAM
2. their uncertainty is hard to estimate, i.e. CERRA has ERA5 ensemble.
3. ICON-DREAM is looking for a sharing strategy.

One of the main scientific challenges for regional reanalyses is to provide a climate-consistent representation that is not influenced by the inclusion of observations throughout the period.
Therefore, the Japan Meteorological Agency has suggested a framework for regional reanalyses that split what was one product into two: sparse-input and full-input.
The sparse/full- input they refer to the observations, the first is with a very limited subset of available observation types for which there is a long record.
The full-input refers to using as many observations as the current operational system, but limiting the period to one that includes all observation types.

The planned regional reanalyses for Europe are summarized below.

| Data Type |  Planned production start | License | Resolution | Format | Time Range | Time Step | Challenges |
|-----------|-----------------|---------|------------|--------|------------|-----------|------------|
| ARRA |   Q4 2024 |  | 1.3km  |  | 1961-2020  | 1 hour? | Data sharing: ~13 PB |
| ICON-FORCE |  2026 | - | 2.1km  |  | 2016 onwards | 1 hour/sub-hourly | ? |
| ICON-FORCE-C |  2026 | - | 2.1km  |  | 2016 onwards | 1 hour/sub-hourly | ? |

The main challenge that regional reanalyses are facing is the high volume of data and the lack of a common sharing platform, as at the moment each producer has to create that as well.

#### Reanalysis challenges
The reanalysis production faces two main challenges: the observation processing and the sharing of the final product.

We go now more in detail about both.

##### Observations for producing the reanalysis

A major technical challenge for producing reanalysis is finding and/or getting access to observations for the past times that not only have a good quality, but also are readable by modern systems.

The centers producing the reanalysis in fact uses their own conventional observations (i.e. SYNOP, TEMP, SHIP, DRIBU,PILOT,AIREP), and those are locally stored.
Further issues are related to the format of the data: 
1. centers might not store them in a WMO-standard format, making data sharing very complex; 
2. changes in the WMO-formats in the decades, forward compatibility to modern formats is not always ensure and trivial. 

When thinking about multi-decades reanalysis, it is important to remember that the local availability depends also not only on the center's history itsefl, but also on the country history.
   
Regarding the satellites observations, centers like EUMETSAT, UCAR, etc, provide reprocessed observational datasets. 
These products have the benefits of having a modern format, but has in mind different end-users.
This makes very complicate to use such datasets out of the box, given how different in structure and information stored are with respect to the operational version that is sent for weather forecasting.
To use datasets such as [EUMETSAT ASCAT](https://dx.doi.org/10.15770/EUM_SEC_CLM_0041), the data assimilation code has to go under major re-write for the IO, quality checks, etc.
This however, would hinder the reanalysis advances due to the complexity in merging the faster paced R&D ongoing in the numerical weather prediction framework.

##### Sharing of the reanalysis products

The second challenge faced in the reanalysis, but not only there, is to find a plattform to share the large volume of data.
For the reanalysis, it is especially important that any user can easily access/download many model variables, as e.g. they can be used as initial/boundary conditions for other AI/classical-downscaling runs.

The latter is a limitation for the planning and/or creation of future regional reanalysis, as they can only be designed with what is easily available.


### Weather radar data
Weather radar data are available at least from following sources:

| Data Type | Realtime Service | Archive | License | Resolution | Format | Time Range | Time Step | Challenges |
|-----------|-----------------|---------|---------|------------|--------|------------|-----------|------------|
| OPERA composites containing rainfall accumulation, rain rate and reflectivity |  Via OPERA data distribution to NMHS | [EWC data buckets](https://confluence.ecmwf.int/display/EWCLOUDKB/EUMETSAT+-+Data+Access=) | EUMETNET License | 2x2km | HDF5 | 2012 onwards | 15 minutes | Low resolution |
| OPERA-SEVIRI fusion dataset (will be added soon)| - | [EWC data buckets](https://confluence.ecmwf.int/display/EWCLOUDKB/EUMETSAT+-+Data+Access=) | EUMETNET License | 2x2km | NetCDF | 2018-2023 | 5/15 minutes | No ready real-time data flow |
| OPERA volume data |  Via OPERA data distribution to NMHS | RODEO project plans to add to EWC | EUMETNET License | 2x2km | HDF5 | 2012 onwards | 15 minutes | Complex data model |
| FMI radar data   |  [FMI open data](https://en.ilmatieteenlaitos.fi/radar-data-on-aws-s3) | [FMI open data](https://en.ilmatieteenlaitos.fi/radar-data-on-aws-s3) | CC4By | 250x250m | GeoTiff / HDF5 | Single radar data from 2007 onwards (HDF5), composites from 2020 onwards (GeoTiff) | 5/15 minutes | Limited coverage |


### Weather and marine observations from single locations

Weather and marine bservations from single locations include synop stations, automatic weather stations (AWS), soundings, AMDARs, buouys, other type of observations providing data from single location or trajectory.

| Data Type | Realtime Service | Archive | License | Resolution | Format | Time Range | Challenges |
|-----------|-----------------|---------|---------|------------|--------|------------|------------|
| Synop & AWS    | EUMETNET Obsevation hub: [Description](https://observations.eumetnet.eu/) (json, last 24 hours) |    RODEO climatogloical data API     |     CC4BY    |    -     | json | 24h | Doesn't include all stations, bufr      |
|               | WIS2 global cache: [Description](https://registry.opendata.aws/wis2-global-cache/) (bufr/grib/netcdf, last 24 hours)  |    RODEO climatogloical data API     |     CC4BY    |    -     | bufr | 24h | Doesn't include all stations, bufr      |
| Sounding  |                 |         |         |            | - | - |           |
| AMDAR     |                 |         |         |            | - | - |           |
| Buoy      |                 |         |         |            | - | - |           |
| Ship      |                 |         |         |            | - | - |           |
| METAR     | [Aviation weather center API](https://aviationweather.gov/data/api/) | - | - | - | - | - | - |
| AIRMET       | [Aviation weather center API](https://aviationweather.gov/data/api/) | - | - | - | - | - | - |
| SIGMET       | [Aviation weather center API](https://aviationweather.gov/data/api/) | - | - | - | - | - | - |


### Gridded observations

Gridded observations, a.k.a. analyses are typically produced using more or less complex interpolation methods such as kriging or mesan. 

| Data Type | Realtime Service | Archive | License | Resolution | Format | Time Range | Challenges |
|-----------|-----------------|---------|---------|------------|--------|------------|------------|
| Gridded observations fro Finland | [FMI open data](https://en.ilmatieteenlaitos.fi/gridded-observations-on-aws-s3) | [FMI open data](https://en.ilmatieteenlaitos.fi/gridded-observations-on-aws-s3) | CC4By | 1x1km | NetCDF | 2022 onwards | Limited coverage 


### Satellite data

#### Geostationary (GEO) Satellites

| Satellite | Data Type               | Real-time Data Service                                                                                                  | Archive Data Service                                                                                                      | License               | Resolution | Format            | Time Range      | Coverage             | Challenges                                                                                                                                                                           |
|-----------|-------------------------|------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|-----------------------|------------|-------------------|-----------------|---------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GOES      | Imagery, radiometric data | [GOES 16-18: GOES AWS S3 Bucket](https://aws.amazon.com/goes/)                                                         | [GOES 13-15: NOAA CLASS](https://www.class.noaa.gov/) <br> [GOES PreGVAR and GOES GVAR in EWC: ECMWF Knowledge Base](https://confluence.ecmwf.int/display/EWC) | Free, open access    | 0.5-2 km   | Native / NetCDF   | 1978-present    | Western Hemisphere  | Limited geospatial coverage, exotic data formats, large data volumes, not all data are publicly available, varying data quality, not geo-referenced                                |
| Himawari  | Imagery, radiometric data | [Himawari AWS S3 Bucket](https://aws.amazon.com/himawari/)                                                             | [HimawariCloud (for NMHSs only)](https://www.data.jma.go.jp/mscweb/en/himawari89/himawari_cloud_service.html)            | Some free, some restricted | 0.5-2 km   | NetCDF / Native   | 2015-present    | Asia-Pacific region | Limited to Asia-Pacific region, large data volumes, exotic data format, not geo-referenced                                                                                        |
| Meteosat  | Imagery, radiometric data | [EUMETSAT Data Store / EUMETCast](https://www.eumetsat.int/data/eumetcast)                                             | [EUMETSAT Data Store](https://www.eumetsat.int/data/data-delivery/eumetsat-data-store)                                   | [EUMETSAT Data Policy](https://www.eumetsat.int/data-policy/eumetsat-data-policy.pdf) | 1-3 km   | NetCDF, Native    | 1977-present    | Europe, Africa, Indian Ocean | Limited to Europe, Africa, and the Indian Ocean region, large data volumes, exotic data format, not geo-referenced                                                             |

#### Low Earth Orbit (LEO) Satellites

| Satellite     | Data Type                  | Real-time Data Service                                                                                      | Archive Data Service                                                                                             | License               | Resolution | Format          | Time Range      | Coverage             | Challenges                                                                                       |
|---------------|----------------------------|------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|-----------------------|------------|-----------------|-----------------|---------------------|-------------------------------------------------------------------------------------------------|
| Landsat       | Imagery, spectral data     | [Landsat AWS S3 Bucket](https://registry.opendata.aws/landsat-8/)                                          | [Landsat AWS S3 Bucket](https://registry.opendata.aws/landsat-8/)                                            | Free, S3 Bucket with Requester Pays | 15-30 m  | GeoTIFF         | 1972-present    | Global              |                                                                                                 |
| Sentinel-1    | Synthetic Aperture Radar (SAR) |  [Copernicus Data Space Ecosystem](https://www.copernicus.eu/en/access-data/copernicus-services-data-hub)| [Copernicus Data Space Ecosystem](https://www.copernicus.eu/en/access-data/copernicus-services-data-hub) | Free, open access    | 5-20 m    | SAFE            | 2014-present    | Global              | Large data volumes, SAFE packages need to be uncompressed                                       |
| Sentinel-2    | Imagery, spectral data     |  [Copernicus Data Space Ecosystem](https://www.copernicus.eu/en/access-data/copernicus-services-data-hub) | [Copernicus Data Space Ecosystem](https://www.copernicus.eu/en/access-data/copernicus-services-data-hub) | Free, open access    | 10-60 m   | SAFE            | 2015-present    | Global              | Large data volumes, SAFE packages need to be uncompressed, cloud cover can affect data quality |
| MODIS         | Imagery, radiometric data  | [MODIS AWS S3 Bucket](https://registry.opendata.aws/modis/)                                               | [MODIS Data](https://modis.gsfc.nasa.gov/data/)                                                              | Free, open access    | 250 m - 1 km | GeoTIFF, others | 1999-present    | Global              | Moderate resolution, large data volumes                                                        |
| EUMETSAT EPS  | Imagery, radiometric data, spectral data | [EUMETSAT Data Store](https://www.eumetsat.int/data/data-delivery/eumetsat-data-store)                         | [EUMETSAT Data Store](https://www.eumetsat.int/data/data-delivery/eumetsat-data-store)                         | [EUMETSAT Data Policy](https://www.eumetsat.int/data-policy/eumetsat-data-policy.pdf)   | 250 m - 1 km | NetCDF, Native  | 2006-present    | Global              | Exotic data formats                                                                             |


#### SAF Data Overview

| SAF Name | Data Type | Real-time Data Service | Archive Data Service | License | Resolution | Format | Time Range | Time Step | Coverage | Challenges |
|----------|-----------|------------------------|----------------------|---------|------------|--------|------------|-----------|----------|------------|
| **[Land Surface Analysis (LSA SAF)](https://lsa-saf.eumetsat.int/en/)** | Land surface temperature, albedo, vegetation indices, surface radiation, evaporation and turbulent fluxes, wild fires | [EUMETCast](https://www.eumetsat.int/eumetcast) | [LSA SAF Data Access](https://lsa-saf.eumetsat.int/en/data/data-access/) | [EUMETSAT Data Policy](https://www.eumetsat.int/data-policy/eumetsat-data-policy.pdf) | 1-3 km | NetCDF, HDF5 | First from 2004 onwards | 15 min - 10 days | Europe / Global | - |
| **[Ocean and Sea Ice (OSI SAF)](https://osi-saf.eumetsat.int/)** | Sea surface temperature, sea ice concentration, wind vectors, radiation fluxes | [EUMETCast](https://www.eumetsat.int/eumetcast) | [OSI SAF Data Access](https://osi-saf.eumetsat.int/) | [EUMETSAT Data Policy](https://www.eumetsat.int/data-policy/eumetsat-data-policy.pdf) | 1km - 75km | NetCDF3, Bufr,  | First from 1978 onwards | 3 min - 1 day | Local / Global | - |
| **[Climate Monitoring (CM SAF)](https://www.cmsaf.eu/EN/Home/home_node.html)** | [See product catalogue](https://www.cmsaf.eu/EN/Products/AvailableProducts/Available_Products_node.html) | [EUMETCast](https://www.eumetsat.int/eumetcast) | [CM SAF](https://www.cmsaf.eu/EN/Products/Data_access/data_access_node.html/) / [EUMETSAT Data Store](https://data.eumetsat.int)| [EUMETSAT Data Policy](https://www.eumetsat.int/data-policy/eumetsat-data-policy.pdf) | 5.6 - 111 km | NetCDF | First from 1978 onwards | 15 min onwards | Local / Global | - |
|  **[Atmospheric Composition Monitoring (AC SAF)](https://acsaf.org/)** | [See product catalogue](https://acsaf.org/) | [EUMETCast](https://www.eumetsat.int/eumetcast) / [DLR FTP Server](https://acsaf.org/nrt_access.php) |[DLR FTP Server](https://acsaf.org/nrt_access.php) / [FMI Data Server](https://acsaf.org/nrt_access.php) | [AC SAF Data Policy](https://acsaf.org/data_policy.php) | ~ 30-500 km  | NetCDF, HDF5, Bufr | First from 2007 onwards | - | Global | - |
| **[Support to Operational Hydrology and Water Management (H SAF)](https://hsaf.meteoam.it/)** | Products related to soil moisture, precipitation and snow | [EUMETCast](https://www.eumetsat.int/eumetcast), ftp | Last 60 days via ftp, the rest via ordering | [EUMETSAT Data Policy](https://www.eumetsat.int/data-policy/eumetsat-data-policy.pdf) | 1-50km | NetCDF, HDF5, GRIB1, GRIB2, Bufr | First from 1992 onwards| 15 minutes to 1-2 days | Local / Global | - |
| **[Radio Occultation Meteorology (ROM SAF)](https://rom-saf.eumetsat.int/)** | Bending Angle Profiles, Refractivity Profiles, Dry Temperature Profiles, 1D-Var Retrievals (Temperature, Humidity, Pressure, and Surface Pressure), Tropopause Height Estimates, Gridded Monthly Mean Data ([more details](https://rom-saf.eumetsat.int/product_archive.php))  | [ROM SAF Product Archive](https://rom-saf.eumetsat.int/product_archive.php) / [EUMETCast](https://www.eumetsat.int/eumetcast) | [ROM SAF Product Archive](https://rom-saf.eumetsat.int/product_archive.php) | [EUMETSAT Data Policy](https://www.eumetsat.int/data-policy/eumetsat-data-policy.pdf) | Individual locations / ~110km | NetCDF3, Bufr | First from 2001 onwards | | Global | - |
| **[Nowcasting (NWC SAF)](https://www.nwcsaf.org/)** <br> (mainly software)| Cloud , precipitation, convection, winds, humidity, instability and conceptual products from GEO and LEO satellites | [EUMETCast](https://www.eumetsat.int/eumetcast) |  GEO reference data at [NWC SAF archive](https://www.nwcsaf.org/web/guest/nec/geo-geostationary-archive) | [EUMETSAT Data Policy](https://www.eumetsat.int/data-policy/eumetsat-data-policy.pdf) | 1km for LEO and 3km for GEO satellites | NetCDF, Bufr | - | 10/15 minutes for GEO, ~2 times a day for LEO | Europe+Africa / Global | - |


### NWP data

While reanalysis data sets have enabled a fast evolution in the development of AI-based forecasting models, latest (physics-based) forecasts at higher resolutions are a valuable data source to tune the modeling of current weather situations and help improve (AI-based) numerical forecasts. Fortunately, an increasingly number of open data sets are now avialble:

| Data Type | Realtime Service | Archive | License | Resolution | Format | Time Range | Challenges |
|-----------|-----------------|---------|---------|------------|--------|------------|------------|
| ECMWF - IFS global medium-range - physics based model + ensembles | [Forecasts](https://www.ecmwf.int/en/forecasts/access-forecasts/access-real-time-open-data) | [Archive](https://www.ecmwf.int/en/forecasts/access-forecasts/access-archive-datasets) | [CC-4.0-BY and the ECMWF ToU](https://apps.ecmwf.int/datasets/licences/general/) | (9km ->) | GRIB/NetCDF | 15 days |  |
| ECMWF - AIFS global medium-range - AI based model + enembles | [Forecasts](https://www.ecmwf.int/en/forecasts/dataset/aifs-machine-learning-data) - 1hr delay| [Archive](https://www.ecmwf.int/en/forecasts/access-forecasts/access-archive-datasets) | [CC-4.0-BY and the ECMWF ToU](https://apps.ecmwf.int/datasets/licences/general/) | (27km ->) | GRIB/NetCDF | 15 days |  |
|  | | |  |  |  | |  |

### Impact & IoT data

The use of AI opens up the possibility to intergrate a wider range of (observational) data on which models can be trained. This includes data on impacts of weather events and data measured by IoT and smart devices. 

There have been already a number of projects funded under the European Unions's Horizon 2020 and Europe programmes to collect and use IoT data for improved imapact assesments. While these projects show the great potential of these data sources, they also show the more complex handling of the data, not just because of the variance of formats and vocabularies, but also for legal and ethical considerations. Unfortunately the heterogenous and large variance nature of these data sets makes it hard to summarise them here.

Efforts are needed to harmonise the access of IoT data for our community, for example like the [TRIGGER](https://project-trigger.eu) project which uses ECMWF's polytope data access software to create a harmonise interface to a wide variance of IoT data from non-meteorological domains. 

*QUESTION: Would it be better to list projects here, rather than data sets?*


| Data Type | Realtime Service | Archive | License | Resolution | Format | Time Range | Challenges |
|-----------|-----------------|---------|---------|------------|--------|------------|------------|
| data type | Realtime service | Archive | License | Resolution | Format | Time Range | Challenges |


## Identification of Data Gaps and Obstacles in Usage

Based on the analyses, following data gaps and obstacles in usage have be identified. 

### Missing data

Following missing data were identified: 
- Fog prediction data is well-known challenge
- Cloud fraction data from LEO satellites providing high-enough resolution in Northern Europe are missing 
- Icing observations preferably in gridded format and for multiple levels for Norhern Europe are missing
- Long-enough training dataset for MTG FCI and LI-data 
- Missing weather radar products such as echo tops, VIL, and hail prodcuts covering the whole Europe

Moreover, imapct data such as flood, drought, and windstorm data were not yet analysed but it's clear that they are widely missing or only available as proprietary data.

 ### Obstacles in Usage

Following remarkable obastacles in usage were identified:

- Slow download and need to uncompress data after downloading (i.e. for satellite data)
- Exotic and varying data formats
- License restrictions i.e. for some satellite data
- Varying and inconcistent time steps and resolutions. All data is not geo-referenced
- Climate Data Records (CDRs) are great source for training but there's no always corresponding real-time data available
- Limited coverage of data sources / fragmented data sources
- Missing mechanism to share large data volumes (i.e. reanalyses)

## Future avenues

As noted, the current version is done in very limited time and collecting use cases and data sources is still ongoing. More data presumably provides more insight to the data gaps and obstacles in usage.

Moreover, the future avenues for this work may also include extension of the content, including:

- Usage examples (e.g. Jupyter notebooks) 
- List and analyses of tools to handle and convert data to AI-ready form
- Best practices ('do/donts') for the different data types and sources, collected both from data providers and consumers
- Quality analyses of the data sources

**We thank all contributors for their instrumental input and feedback!**

We are looking forward to see more contributions from both data providers and consumers. 
We are also very happy to see hear your feedback and ideas for the future avenues of this work.
