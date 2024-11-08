

## Detecting tropical storms using transfer learning

Detecting tropcial storms using transfer learning from Himawari infrared channel. See [article](https://ieeexplore.ieee.org/document/10436346) for more details.

### Contact
Roope Tervo

### Used training data

| Topic | Content |
|-------|---------|
| **Data source** | Himawari and GSM infrared channels (some data in [EWC](https://confluence.ecmwf.int/display/EWCLOUDKB/EUMETSAT+-+Data+Access=), more info from the programs: [GMS](https://www.eoportal.org/satellite-missions/gms) and [Himawari-8 and 9](https://www.eoportal.org/satellite-missions/himawari-8-9)) |
| **Data content** | Single infrared channel |
| **Geospatial resolution**| 5km at nadir|
| **Temporal resolution**|30 minutes |
| **Data format**| JMA native |
| **Preferred data format** | Zarr / GeoTiff |
| **Preferred data access mechanism** | Preferred access mechanism if any |
| **Data preprocessing** | Generated grayscale images which were downscaled to 1024x1024 pixels for training |
| **Reason for usage** | As part of GeoRing project, lots of tropical storms, straight forward test case for transfer learning |
| **Challeneges** | 1) Handling native format is challenging. 2) License restrictions for usage. 3) Large data volumes took time and resources. |


| Topic | Content |
|-------|---------|
| **Data source** | [International Best Track Archive for Climate Stewardship (IBTrACS)](https://www.ncei.noaa.gov/products/international-best-track-archive) containing hurricane reports |
| **Data content** | See [documentation](https://www.ncei.noaa.gov/sites/g/files/anmtlf171/files/2024-07/IBTrACS_version4r01_Technical_Details.pdf) |
| **Geospatial resolution**| center points of storms |
| **Temporal resolution**| 3 hours |
| **Data format**| CSV / NetCDF |
| **Data preprocessing** | Generated xml of bounding boxes for the times we have images in the format required by the used model |
| **Reason for usage** | Best long time series of hurricanes according to our knowledge |
| **Challeneges** | 1) Data not very accurate, required a lot of manual tuning. Also a lot of missing storms. 2) Contain only storm center points. |
