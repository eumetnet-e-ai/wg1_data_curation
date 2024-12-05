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
  | CloudCast | [Description](../gap_analysis/use_cases/cloudcast.md) | 15 minutes | Northern Europe | 4x4 km | Effective cloudiness, ie. cloud fraction | Zarr | EWC | Poor quality and missing data  |
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

### 4.1 Reanalyses
<<<<<<< HEAD

To be written
=======
Reanalyses are a key dataset for early ML, since they provide a gridded physically consistent dataset that has no spatial (neither in the vertical nor in the horizontal) or temporal gap.
#### 4.1.1. ERA5 
1-2 sentence definition of data
>>>>>>> 16b1c88 (Update e_ai_data_gap_analyses.md)


<<<<<<< HEAD
### Weather radar data
Weather radar data are available at least from following sources:
=======
#### 4.1.x. ICON-DREAM - "future"
ICON-DREAM (ICON-Dual resolution Reanalysis for Emulators, Applications and Monitoring) utilize the global ICON NWP framework from DWD, that has an additional two-way coupled nest over Europe. This  reanalysis has resolution of 13km globally and 6.5 km over Europe and 120 vertical levels. Its operational data assimilation cycle comprises an EnVar at 3-hourly intervals complemented by a snow analysis every 3 hours, and T2M, SST and soil moisture analysis every 24 hours (at 00 UTC). The background error covariances are provided by a 20 member ensemble at 40km global and 20km over Europe with a LETKF-based data assimilation scheme.
The reanalysis currently covers the period from 2010 to today with a continuous extension to the current time. Plans include the back-extension starting in 1979.

- **Available data sources**
    - 111 hourly variables for the deterministic and all ensembles, including their European nests. Data sharing procedure: work in progress given the high volume (0.4 PB/year).
- **Data services**
    - How available: some variables will be on a publicly accessible ftp server.
    - Restrictions in availability: for now, only on HPC.
- **License**:
    - Restrictions in availability (only in HPC / EWC / etc, only for certain users...)
- **Obstacles in Usage**:
  -  Whatever comes up in the use case analyses

## 5. Identification of Data Gaps
>>>>>>> 16b1c88 (Update e_ai_data_gap_analyses.md)

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

To be added 

| Data Type | Realtime Service | Archive | License | Resolution | Format | Time Range | Challenges |
|-----------|-----------------|---------|---------|------------|--------|------------|------------|
| data type | Realtime service | Archive | License | Resolution | Format | Time Range | Challenges |

### Impact data

To be added 

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


    
