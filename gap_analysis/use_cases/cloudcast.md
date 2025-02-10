### Cloud fraction nowcasting for Scandinavian domain

Operationally-used cloud fraction nowcasting for up to three hours using geostationary data as input. Preprint at [arxiv.org](https://arxiv.org/abs/2410.21329).

### Contact
Mikko Partio

### Used training data


| Topic | Content |
|-------|---------|
| **Data source** | [NWCSAF/GEO CTTH](https://www.nwcsaf.org/ctth_description) |
| **Data content** <br> (parameters / products / levels / etc.) | Effective cloudiness, ie. cloud fraction |
| **Geospatial resolution**| Nominal resolution is 4x4km; effectively in high latitudes this is worse |
| **Temporal resolution**| 15 minutes |
| **Data format**| Archived as NetCDF in FMI; converted to numpy arrays for training |
| **Preferred data format** | zarr |
| **Preferred data access mechanism** | s3 bucket |
| **Data preprocessing** | Data was projected to lambert conformal conic over Scandinavia. |
| **Reason for usage** | The only available remote sensing data from geostationary satellites that provides a cloud fraction comparable to NWP ouput |
| **Challenges** | Multiple challenges related to quality of the data: 1) data is distorted in high latitudes due to satellite viewing angle (we are using parallax corrected data); 2) data has a lot of missing values; 3) data is known to be incorrect in certain weather situations; 4) instrument resolution is not enought to detect cumulus clouds; 5) our archive contains data from multiple NWCSAF versions and the netcdf layout has changed between versions; 6) gaps in timeseries data due to issues at FMI or EUMETSAT production systems |

### Missing data

Please describe which data are you missing / which data you believe would make usage better. 

| Topic | Content |
|-------|---------|
| **Explanation** | Cloud fraction from polar orbiting satellites | 
| **Data content** <br> (parameters / products / levels / etc.) | Polar orbiting satellites would offer an additional data source for cloud fraction but AFAIK no instantanious cloud fraction data exists from EUMETSAT LEO satellites  |
| **Geospatial resolution**| 1x1km |
| **Temporal resolution**| |
| **Preferred data format** | zarr |
| **Preferred data access mechanism** | s3 bucket |

### Used inference data

Please copy the underlying table for each used dataset and fulfil from applicable parts **in case inference data differs from training data**.

| Topic | Content |
|-------|---------|
| **Data preprocessing** | Missing values and known issues are fixed (to some degree) with a diagnostic-based algorithm relying on NWP data |

