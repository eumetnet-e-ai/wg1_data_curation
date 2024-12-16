## Use case template

In the context of SRNWP-EPS_2 Project of the EUMETNET consortium, the objective of this wor is to use Machine Learning, particularly a decision tree and XGBoost model with Numerical Weather Prediction (NWP) data to enhance early detection of extreme weather events like thunderstorms and fog. (ref: https://www.eumetnet.eu/activities/forecasting-programme/current-activities-fc/eps-ii)

### Contact
Marco Di Giacomo
Email: marco.digiacomo@geo-k.co
Tel: +39 06 72597711

### Used training data




| Topic | Content |
|-------|---------|
| **Data source** | [COSMO-IT model](https://www.meteoam.it/it/operational-configuration) |
| **Data content** | CAPE, CIN, CPTP, EHI, JEFF, K, KO, LPI, QG, rh, SWEAT, T2m, thick_pres, TP, TT, UH, wind_shear3km, hsurf (for thundestorm detection task) tqv, 10u, 10v, 2d, 2t, pmsl, relhum_2m, sp, tp (for fog detection task)|
| **Geospatial resolution**| 2.2x2.2km|
| **Temporal resolution**| 1 hour |
| **Data format**| Grib |
| **Preferred data format** | Grib or NetCDF/CSV |
| **Preferred data access mechanism** | Provided by Italian Air Force Met Service (CNMCA)|
| **Data preprocessing** | Extraction of single day file, temporal and spatial aggregation with other type of data|
| **Reason for usage** | Input data for the AI model. This dataset provides information about the atmospheric initial conditions, e.g., atmospheric instability which trigger weather phenomena, e.g., thunderstorms and fog |
| **Challenges** | Due to the hourly basis of the dataset, when adopting a considerable time window to build the training dataset, the aggregation with the other data is too resources-demanding, despite the great GPU capabilities.|

| Topic | Content |
|-------|---------|
| **Data source** | [Rapidly Developing Thunderstorms (RDT)](https://navigator.eumetsat.int/product/EO:EUM:DAT:0023/print) |
| **Data content**  | RDT data is collected in IR domain. This product provides short-range forecasting and nowcasting users with a large range of parameters about convection events and their predicted development. |
| **Geospatial resolution**| 3x3km|
| **Temporal resolution**| 15 minutes |
| **Data format**| NetCDF |
| **Preferred data format** | NetCDF or CSV or Grib |
| **Preferred data access mechanism** | NWC/GEO 2021.1 |
| **Data preprocessing** | The data need a temporal and spatial aggregation with the others parameters in input to the model|
| **Reason for usage** | Target data for the AI model. The dataset consists of satellite observations that provide information on the presence or absence of thunderstorms.|
| **Challenges** | Problem with a missing variable on a specific time frame; It would be great to access past data to generate larger dataset and solve missing values/variables problems  |

| Topic | Content |
|-------|---------|
| **Data source** | [METAR](https://navigator.eumetsat.int/product/EO:EUM:DAT:0023/print) |
| **Data content**  | METAR dataset consists of reports describing the weather conditions observed by weather stations, consisting of ground-based observations. There are 114 weather stations across Italy that provide several obsrvations inculing visibility and convective events phenomena with hourly temporal frequency.|
| **Geospatial resolution**| exact locations |
| **Temporal resolution**| 1 hour |
| **Data format**| CSV |
| **Preferred data format** | CSV |
| **Preferred data access mechanism** | Downloaded from EPIMETEO repository ownd by Provided by Italian Air Force Met Service (CNMCA) |
| **Data preprocessing** | Spatial interpolation on COSOMO-IT grid. Temporal and spatial aggregation with the other dataset involved in the AI framework |
| **Reason for usage** | Validation daset to assess model accuracy (for thunderstorm detection task). Target data for the AI model (fog detection task) |
| **Challenges** |  Not all the stations acquire data continuously, and, when they do, the recorded values may include NaN (missing) values.|


### Missing data


| Topic | Content |
|-------|---------|
| **Explanation** | FOG information data | 
| **Data content**  |We need some spatialized data about visibility variations to enable the creation of a dataset for fog prediction over the whole are of interest.|
| **Geospatial resolution**| 3x3km or finer resolution |
| **Temporal resolution**| not less of 1 hour |
| **Preferred data format** | CSV/Grib/NetCDF|
| **Preferred data access mechanism** | Open access, API, Download .zip files |
### Used interference data
--
