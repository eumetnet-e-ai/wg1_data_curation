
## Weather front forecasts (gridded)

Fronts are often connected to relevant weather and at many weather services hand drawn using model and other synoptic data.
This task is labour intensive and could be supported by providing AI produced front analysis.
DWD trained an AI front prediction system (U-Net) using a large set of hand drawn, machine readable front analysis as training label data.
The model output is a pixel map. Each pixel is given a probability to be classified either as cold-, warm-, occluded or no front.


[https://ascmo.copernicus.org/articles/5/147/2019/]
[https://wcd.copernicus.org/articles/3/113/2022/]


### Contact
felix.fundel@dwd.de

### Used label data

| Topic | Content |
|-------|---------|
| **Data source** | DWD (on demand) |
| **Data content** <br> (parameters / products / levels / etc.) | Lines with position of warm-fronts, cold-fronts and occlusions |
| **Geospatial resolution**| Vector |
| **Temporal resolution**| Analysis at 00 and 12 UTC (starting March 2021)|
| **Data format**| GML |
| **Data preprocessing** | Data is gridded for training purposes|



### Used training data

| Topic | Content |
|-------|---------|
| **Data source** | ICON 0h forecasts of 00UTC and 12UTC runs [https://opendata.dwd.de/weather/nwp/icon/] |
| **Data content** <br> (parameters / products / levels / etc.) | T2M, RH2M, U10M, V10M, MSLP, land-sea mask |
| **Data format**| Grib |
| **Geospatial resolution**| regridded to ~ 0.4° |
| **Temporal resolution**| 12 hrly |
| **Preferred data access mechanism** |  |
| **Data preprocessing** | Regridded original grib to ~0.4° and converted to netCDF |



### Used inference data

| Topic | Content |
|-------|---------|
| **Data source** | ICON & ICON-EPS forecasts  [https://opendata.dwd.de/weather/nwp/] |
| **Data content** <br> (parameters / products / levels / etc.) | T2M, RH2M, U10M, V10M, MSLP, land-sea mask |
| **Data format**| Grib |
| **Geospatial resolution**| regridded to ~ 0.4° |
| **Temporal resolution**| 3 hrly |
| **Preferred data access mechanism** |  |
| **Data preprocessing** | Regridded original grib to ~0.4° and converted to netCDF |


