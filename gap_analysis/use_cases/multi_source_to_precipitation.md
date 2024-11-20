## Earthformer for multi-source-to-precipitation nowcasting for INCA domain (EF4INCA)

Precipitation nowcasting tailored for convective events using space- and ground-based observation together with NWP data. For further details, please see:
* [Preprint](https://arxiv.org/abs/2409.10367)
* [Dataset](https://zenodo.org/records/13740315)
* [Code repository](https://github.com/caglarkucuk/earthformer-multisource-to-inca)
* [Model weights](https://zenodo.org/records/13768229)

### Dataset

The dataset contains more than 7800 events, each spanning over 4 hours, sampled over 5 years, from 2019 to 2023, during summer periods April to September, when convective activity is highest over Austria. Temporal sampling of the events
is stratified in order to avoid clear-sky conditions dominating the dataset and to increase the focus
on convective events.

#### Satellite:
| Topic | Content |
|-------|---------|
| **Data source** | [Rapid Scan High Rate SEVIRI Level 1.5 Image Data - MSG](https://user.eumetsat.int/catalogue/EO:EUM:DAT:MSG:MSG15-RSS) |
| **Data content** | Four infrared channels are used: With central wavelengths of $6.2$, $7.3$, $8.7$, and $10.8 \mu m$ (namely CH5, CH6, CH7, and CH9)  |
| **Geospatial resolution**| 2x2km at nadir, ~3.5x4km around Austria |
| **Temporal resolution**| 5 min |
| **Data format**| .tif |
| **Preferred data access mechanism** | s3 buckets |
| **Data preprocessing** | Downloaded using `eumdac`, removed irrelevant bands, reprojected and cropped for INCA domain using `gdal`|
| **Reason for usage** | Infrared bands are useful for convective activity. See Sec. 2.1.1 in [preprint](https://arxiv.org/abs/2409.10367) |
| **Challenges** | Rather long download time when a large archive is needed |

#### Precipitation radar:
| Topic | Content |
|-------|---------|
| **Data source** | C-band ground-based radar towers used in INCA predictions |
| **Data content** | 2D precipitation estimates |
| **Geospatial resolution**| 1x1km |
| **Temporal resolution**| 5 min |
| **Data format**| .h5 |
| **Preferred data access mechanism** | s3 buckets |
| **Data preprocessing** | Tower-based data mosaicked using `python`|
| **Reason for usage** | Great source for precipitation |

#### Lightning:
| Topic | Content |
|-------|---------|
| **Data source** | Ground-based observations from [EUCLID network](https://www.euclid.org/) |
| **Data content** | Point-based lightning detections |
| **Geospatial resolution**| NA |
| **Temporal resolution**| NA |
| **Preferred data access mechanism** | s3 buckets |
| **Data preprocessing** | Tabular data gathered using `SQL`, rasterized using `python`|
| **Reason for usage** | Great diagnostic for convective activity |
<!-- | **Challenges** |  | -->

#### INCA precipitation analysis:
| Topic | Content |
|-------|---------|
| **Data source** | See corresponding [paper](https://doi.org/10.1175/2010WAF2222451.1) |
| **Data content** | Most accurate precipitation product over the domain |
| **Geospatial resolution**| 1x1km |
| **Temporal resolution**| 5 min |
| **Data format**| .asc.gz |
| **Data preprocessing** | Read from the internal archive and synched with the rest for space and time using `python` |

#### INCA Convective Available Potential Energy (CAPE):
| Topic | Content |
|-------|---------|
| **Data source** | See corresponding [paper](https://doi.org/10.1175/2010WAF2222451.1) |
| **Geospatial resolution**| 1x1km |
| **Temporal resolution**| 1 hour |
| **Data format**| .asc.gz |
| **Data preprocessing** | Read from the internal archive and synched with the rest for space and time using `python` |
| **Reason for usage** | Good diagnostic for convective activity |

### Missing data

#### Satellite:
| Topic | Content |
|-------|---------|
| **Explanation** | MTG FCI and LI data| 
| **Data content**  | Same infrared channels used from MSG, as well as lightning observations |
