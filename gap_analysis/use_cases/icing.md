## Icing forecast in gridded format

Icing is a critical parameter of interest for various applications, including aviation, wind energy, and other industries. Efforts to forecast icing conditions have primarily relied on point observations. However, the lack of reliable observational data, especially covering large areas and across multiple atmospheric levels presents a significant challenge to improving the accuracy and reliability of these forecasts.

FMI has developed XGBoost model for forecasting the icing conditions on roads, but for in-cloud icing forecasts are based on NWP output and an icing model. 

This description is about ML model we would like to develop, if we had suitable observations.  

### Contact
leila.hieta@fmi.fi

### Used training data

| Topic | Content |
|-------|---------|
| **Data source** | [MEPS LAM model](https://metcoop.smhi.se/dokuwiki/nwp/metcoop/meps/start) |
| **Data content** <br> (parameters / products / levels / etc.) | Several model parameters relative for icing from surface and hybrid levels |
| **Geospatial resolution**| 2.5x2.5km |
| **Temporal resolution**| 1h |
| **Data format**| grib2 |
| **Preferred data format** |  |
| **Preferred data access mechanism** |  |
| **Data preprocessing** | |
| **Reason for usage** | High resolution, limited area model for Scandinavia |
| **Challenges** | |

### Missing data

Please describe which data are you missing / which data you believe would make usage better. 

| Topic | Content |
|-------|---------|
| **Explanation** | To forecast icing with ML, we would needs to have qood quality observations preferably in gridded format for Snacinavia. MTG ASII-ICE product sounds interesting | 
| **Data content** <br> (parameters / products / levels / etc.) | Icing observations preferably in gridded format and for multiple levels |
| **Geospatial resolution**|  preferably 2.5x2.5km  |
| **Temporal resolution**| 1h |
| **Preferred data format** |  |
| **Preferred data access mechanism** |  |

### Used interference data


