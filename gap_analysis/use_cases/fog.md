## Use case nowcAstIng

nowcAstIng is a toolbox develloped by the NWC SAF.  
The toolbox provide and environment where to test ML models for fog nowcsating in the airports. The idea behind is to exploit simustaneously METAR data and the NWCSAF Clouds. The software downloads from ICARE small stamps of the NWC SAF cloud products and build an individual netcdf file with a very long time coordinate. It does the same for METAR reports downloading them from the IOWA University. 
Concerning the data, currently downloading the data from ICARE costs a lot of time, and building the cubes requires also a lot of computations. 
It could be great having the same content NWCSAF Clouds exposed via by example openDAP allowing to get temporary series in an easy way. I think tha it implies adding the time dimension to the files and storing them to be accessed from an individual point. The same referring to SEVIRI data.
#### Functionalities of the toolbox
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

#### NWC SAF Clouds

| Topic | Content |
|-------|---------|
| **Data source** | The data corresponding to the NWC SAF cloud products  are downloaded from ICARE https://www.icare.univ-lille.fr/)
| **Data content** <br> (parameters / products / levels / etc.) | Clouds observations from satellite (Cloud Mask, Cloud Type, Cloud top temperature) |
| **Geospatial resolution**| e.g. 3x3km at subsatellite point for satellite. |
| **Temporal resolution**| 15 min regular for satellite (SEVIRI)|
| **Data format**| Individual netcdf files packed in a single netcdf file for satellite  |
| **Preferred data format** | netcdf with a long time dimension, allowing to load quickly data as an xarray Dataset  |
| **Preferred data access mechanism** | Ideally an API allowing to download locally the data in small stamps packed in a way that the loading with xarray was fast|
| **Data preprocessing** |The software downloads the data and pack them in an individual netCDF CF files.The software includes a module that wrappes the download API for AERIS/ICARE, with name nwcsaf.py  ||
| **Reason for usage** | There is some signal in the satellite NWC SAF Cloud products related to the fog presence, also the fog or not presence can affect to the night cooling and promote the fog ocurrence|
| **Challenges** | The main challenge is related to the time needed to download and pack in a single file the satellite cloud data|


#### METAR data


| Topic | Content |
|-------|---------|
| **Data source** | The data corresponding to METAR reports downloaded from IOWA https://mesonet.agron.iastate.edu/request/download.phtml. 
| **Data content** <br> (parameters / products / levels / etc.) | Ground observations from airports (METAR). Temperature, humidity, wind speed...|
| **Geospatial resolution**| NA to ground observations |
| **Temporal resolution**| 30 min regular for METAR reports in Europe |
| **Data format**| Text transformed in netcdf.  |
| **Preferred data format** | netcdf with a long time dimension, allowing to load quickly data as an xarray Dataset  |
| **Preferred data access mechanism** | Ideally an API allowing to download locally the data packed in a way that the loading with xarray was fast|
| **Data preprocessing** |The software downloads the data and pack them in an individual netCDF CF files.The software includes a module that wrapp the download API for IOWA State University, with name: airport.py. ||
| **Reason for usage** | The ground dtat that includes the fog presence or not are crucial to nowcast the fog presence in the next hours|
| **Challenges** | The METAR report are issued with different schedules depending on the airport, some of them close at night and for this period they doesn't issue metars|

### Missing data

Satellite Brighness temperatures. 

| Topic | Content |
|-------|---------|
| **Explanation** | The satellite "raw" data maybe are foreseen as a valuable source of information| 
| **Data content** <br> (parameters / products / levels / etc.) | Brighness temperatures for IR channels and reflectivities for visible channels |
| **Geospatial resolution**| 3x3km at subsatellite point for SEVIRI |
| **Temporal resolution**| 15 min regular|
| **Preferred data format** | netcdf with a long time dimension, allowing to load quickly data as an xarray Dataset  |
| **Preferred data access mechanism** | Ideally an API allowing to download locally the data packed in a way that the loading with xarray was fast|

