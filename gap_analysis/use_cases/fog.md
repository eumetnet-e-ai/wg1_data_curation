## Use case nowcAstIng

nowcAstIng is a toolbox develloped by the NWC SAF.  
The toolbox provide and environment where to test ML models for fog nowcsating in the airports. The idea behind is to exploit simustaneously METAR data and the NWCSAF Clouds. The software downloads from ICARE small stamps of the NWC SAF cloud products and build an individual netcdf file with a very long time coordinate. It does the same for METAR reports downloading them from the IOWA University.  
The nowcAstIing toolbox is in the format of a Jupyter notebook collection, allowing:
1. To download the NWC SAF clouds and collocate them with METAR reports ;
2. To get insight on the fog formation ;
3. To establish baseline models ;
4. To develop ML models to forecast the occurrence of fog ;
5. To store their models for operational reuse.

https://gitlab.eumetsat.int/eumetlab/weather/nowcasting.git


### Contact
jllisov@aemet.es

### Used training data

Please copy the underlying table for each used dataset and fulfil from applicable parts. Don't worry! It does not need to be complete! 

Please note that also non-publicly available datasets are in scope as well.

| Topic | Content |
|-------|---------|
| **Data source** | Short description + [url to data source](README.md) |
| **Data content** <br> (parameters / products / levels / etc.) | As accurate list of the content as possible. Notably, we can't use very specific terminology because different domains use different vocabulary (e.g. channels vs. paramaters vs. variables vs. products) |
| **Geospatial resolution**| e.g. 2x2km or 0.05 deg |
| **Temporal resolution**| e.g. 5 min regular, or in average of 2 times per day |
| **Data format**| Available and used data formats |
| **Preferred data format** | Preferred data format if any |
| **Preferred data access mechanism** | Preferred access mechanism if any |
| **Data preprocessing** | Short description of preprocessing and used tools|
| **Reason for usage** | Short description why this data were used |
| **Challenges** | If you have occured some challenges in using the data, please describe them here |

### Missing data

Please describe which data are you missing / which data you believe would make usage better. 

| Topic | Content |
|-------|---------|
| **Explanation** | Explanation what's missing | 
| **Data content** <br> (parameters / products / levels / etc.) | As accurate list of the content as possible. Notably, we can't use very specific terminology because different domains use different vocabulary (e.g. channels vs. paramaters vs. variables vs. products) |
| **Geospatial resolution**| e.g. 2x2km or 0.05 deg |
| **Temporal resolution**| e.g. 5 min regular, or in average of 2 times per day |
| **Preferred data format** | Preferred data format if any |
| **Preferred data access mechanism** | Preferred access mechanism if any |

### Used interference data

Please copy the underlying table for each used dataset and fulfil from applicable parts **in case interference data differs from training data**.

| Topic | Content |
|-------|---------|
| **Data source** | Short description + [url to data source](README.md) |
| **Data content** <br> (parameters / products / levels / etc.) | As accurate list of the content as possible. Notably, we can't use very specific terminology because different domains use different vocabulary (e.g. channels vs. paramaters vs. variables vs. products) |
| **Data format**| Available and used data formats |
| **Geospatial resolution**| e.g. 2x2km or 0.05 deg |
| **Temporal resolution**| e.g. 5 min regular, or in average of 2 times per day |
| **Preferred data format** | Preferred data format if any |
| **Preferred data access mechanism** | Preferred access mechanism if any |
| **Data preprocessing** | Short description of preprocessing |
| **Reason for usage** | Short description why this data were used |
| **Challenges** | If you have occured some challenges in using the data, please describe them here |

