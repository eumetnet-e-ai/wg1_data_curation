# Data Gap Analysis for Weather and Climate-Related AI/ML Applications

## 1. Summary
- Keep short enough

## 2. Introduction

1 paragraph of background

### 2.1 Purpose and Scope
(1 paragraph)

- to find most important missing data
- to find technical and content-related obstacles in using the data
- possibly to be extended to data inventory in the future (more about future avenues in Chapter xx)

### 2.3 Methodology
(1 or 2 paragaphs)

- WG composition and meetings 
- Use case data collection
- Dataset data collection (other documents, do we do anything else?)
- Writing of this report


## 3. Data Requirements of Identified Use Cases
This chapter handles key requirements for data based on the use case analyses.

### 3.1 Key Use Cases
- List of use cases identified / analysed in this work 
- Applications summary (table below), possibly to be divided per category in the future:
  - Meteorological data (e.g., temperature, humidity, pressure).
  - Climate data (e.g., long-term trends, sea-level changes).
  - Environmental data (e.g., land cover, aerosols).
  - Socioeconomic data (for impact and adaptation modeling).


  | Name | Link | Temporal Resolution | Domain | Geospatial Resolution | Used Data | Data Format | Key Challenges |
  |------|------|---------------------|-------------|----------|------------|-------------|----------------|
  | CloudCast | [Description](../gap_analysis/use_cases/cloudcast.md) | 15 minutes | Northern Europe | 4x4 km | Effective cloudiness, ie. cloud fraction | Zarr | Poor quality and missing data  |
  | Icing forecast | [Description](use_cases/icing.md) | 1h | - |  2.5x2.5km | NWP/MEPS | Grib2  | - |
  | Earthformer | [Description](use_cases/multi_source_to_precipitation.md) | 5 min | Austria | 1x1km/2x2km | radar / SEVIRI / lightning / analyses | H5 --> tif | slow download |
  | Tropical storm detection | [Description](use_cases/tropical_storm_detection.md) | 30 minutes | Global | 5km | Infrared satellite images | GeoTiff | 1) Handling native format is challenging. 2) License restrictions for usage |
  | Weather front forecasts | [Description](use_cases/weather_front_analysis.md) | 3 hours | Europe / Global |  ~ 0.4° | ICON | Grib --> NetCDF |  - |

### 3.3 Joined Characteristics

There are no enough use cases to draw trustwrothy synthesis, but preliminary folllowing things can be stated: 

- Preferred access mechanism is S3
- Preferred data format is controversial
- Spatial resolution should be as high as possible but it naturally depends on use cases. Currently available data for ML/AI training is sufficient for localised use cases such as nowcasting.

### 3.4 Summary of obstacles

There are no enough use cases to draw trustwrothy synthesis. 

## 4. Current Data Inventory

This chapter list most typically used data sources for E-AI applications with necessary details to identify potential challenges with existing data or missing data. Readers are invited to add their data source to the tables.

Also MLCast and MLLAM working group documents list typically used datasets. 

Repeat following for:
- Reanalysis 
- NWP data
- Satellite data
- Impact data

NOTE: add also key future datasets such as ERA6 and EPS-SG

### 4.1 Reanalyses

To be written


### 4.1 Weather and marine observations from single locations

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


### 4.1 Satellite data

xxx

| Data Type | Realtime Service | Archive | License | Challenges |
|-----------|-----------------|---------|---------|-----------|


## 5. Identification of Data Gaps

List missing data or significant content-related shortcomings for existing data. For each: 

- **Data Description**:
  - Description of data content (variables / parameters / etc.)
- **Resolution**:
  - Lack of resolution for use case xx
- **Coverage**:
  - Lack of coverage for use case xx
- **Obstacles in Usage**:
  - Whatever comes out from the analyses, some guesses: 
    - Data services not available or not usabe
    - Data too complex to use in given time (why?)
    - Licensing
    - ... 

## 6. Conclusion

1-2 paragraphs to summary (or we keep only executive summary in the top?)

## 7. Futureu avenues

- This version was done very quickly, continue gathering data for this and update
- Add:
    - Usage examples
    - Tools to handle and convert data to AI-ready form
    - Future directions: do/donts feedback from the ML applications to the different data providers (best practices)
    - Quality analyses ?
    - what else?


    