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
  | Earthformer | [Description](use_cases/multi_source_to_precipitation.md) | 5 min | Austria | 1x1km/2x2km | radar / SEVIRI / lightning / analyses | H5/tif | slow download |
  | Tropical storm detection | [Description](use_cases/tropical_storm_detection.md) | 30 minutes | Global | 5km | Infrared satellite images | GeoTiff | 1) Handling native format is challenging. 2) License restrictions for usage |

### 3.3 Joined Characteristics
- Preferred access mechanism: S3
- Preferred data format: controversial
- Spatial resolution: as high as possible
- Temporal resolution: ?
- Coverage (global, regional, local): mostly limited areas

### 3.4 Summary of obstacles
- If we have enough content, we can add summary table of problems 

## 4. Current Data Inventory

Repeat following for:
- Reanalysis 
- NWP data
- Ground-based observations
- Satellite data
- Impact data

NOTE: add also key future datasets such as ERA6 and EPS-SG

### 4.1 Reanalyses
Reanalyses are a key dataset for early ML, since they provide a gridded physically consistent dataset that has no spatial (neither in the vertical nor in the horizontal) or temporal gap.
#### 4.1.1. ERA5 
1-2 sentence definition of data

- **Available data sources**
    - List / table of available data sourcees with a link
- **Data services**
    - How available (data API / S3 / ftp / not available / etc.)
    - Restrictions in availability (only in HPC / EWC / etc, only for certain users...)
- **License**:
    - Restrictions in availability (only in HPC / EWC / etc, only for certain users...)
- **Obstacles in Usage**:
  -  Whatever comes up in the use case analyses

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


    
