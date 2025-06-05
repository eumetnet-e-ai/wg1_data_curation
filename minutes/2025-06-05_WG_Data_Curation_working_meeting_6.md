# Minutes of the WG1 Data Curation Working Meeting 6 

## Participants  
**05 Jun 2025**
- Stephan Siemen (ECMWF)  
- Roope Tervo (EUMETSAT)  
- Arianna Valmassoi (DWD)  
- Marek Jacob (DWD)  
- Sina Montazeri (EUMETSAT)  
- Yordan Radev (ECCC)  
- Oriol Hinojo (EUMETSAT)  
- Milena Dimitrijevic (ECCC)  
- Ben Fitzpatrick (UKMO)  
- Adam Jaczewski (IMWM)  

## Agenda
- Action review  
- Canadian use cases / Milena  
- July workshop schedule  
- Zarr sub-group schedule  
- New activity to be covered: feature detection  
- EUMETNET Data Workshop in Oslo  
- Next meetings  

## Links for Convenience
- **Our GitHub**: [eumetnet-e-ai/wg1_data_curation: Material and Scripts for Data Curation](https://github.com/eumetnet-e-ai/wg1_data_curation)  
- **Gap analysis document**: [GitHub Draft - Gap Analysis](https://github.com/eumetnet-e-ai/wg1_data_curation/tree/draft/gap_analysis)  
- **Nowcasting**: [Google Doc](https://docs.google.com/document/d/1iknFj36XdV19udaIsYJhVJLv2Hq-ARjO85jD0jfrYqw/edit?tab=t.0#heading=h.g7k4377ea9doMLCast)  
- **ML LAM**: [Google Doc](https://docs.google.com/document/d/1KzMHjl08ESMSpEwJ1eopbWfBp_2MXL-XL63KljWQCZU/edit?tab=t.0#heading=h.66rsmcqr6xup)  

---

## Minutes

### Actions
- Everyone to add their own use cases and advertise them in their organisations  
- `lcd@dmi.dk` to add regional reanalysis datasets list in ML LAM community document in the Gap Analysis document – Leif on parental leave for the next couple of months  
- Leif and Ben to coordinate on joint use case for the gap analysis ← to be done by and discussed in the next meeting. Data-driven regional model use case: ERA5 + regional reanalysis + additional observations. Stephan and Ben will coordinate with pilot project to get joint use case. We can then discuss in the meeting  

**Gap Analysis Document**
- People to approach: developers and service providers in our own organisations, related both to ML and classical applications  

### Milena Dimitrijevic - Canadian Use Cases
- CaSR ML/AI applications – previous limitations described (temporal/spatial resolution, data cube)  
- Noted the importance of feedback about acknowledged problems to improve CaSR data  
- Great Lakes runoff intercomparison project – one ML model (LSTM) trained with meteo input  
- CaSR beyond hydro-application to broader community: higher resolution, precipitation analysis, more observations in Land DA by adding satellite data, evolving land-cover and vegetation, representation of cities and lakes  

Summary of improvments: 
- Smaller grid spacing (e.g., 2.5 km) needed for surface modelling applications
- Upgrading precipitation analysis (e.g., snow in winter)
- Improve land data assimilation (SMAP, SMOS, GOES)
- Upgraded land surface modelling (more advanced surface schemes - SVS)
- Evolving land cover/vegetation
- Adding representation of cities (town energy balance model)
- Adding representations of lakes (Canadian small lake model)

Some general challenges related to use of data with ML/AI models:
- Combining different data sources for training and predictions
- Volume of data: surface level versus 3D data cube

#### Q&A
- Challenges at 2.5 km: meteorological forcing available is too coarse for the hydrology model, computing resources are a limitation, coupling to the ocean  
- Some application developers have indicated that 2.5 km resolution would not be sufficient. One possibility might be to do application-specific downscaling for those applications.
- Combine data sources: how to combine historical period with the forecast? One should use the closest config to the operational model. How to handle the data? – currently converting everything to NetCDF, but it's ad-hoc and not the best for data cubes. Inference is now possible from the operational weather model. Some very preliminary tests have been done.
- Radar data inclusion: problem due to resources and data availability  
- Why is the model region going so far in South? The project is funded by US and Canada with a goal to get consistent data over whole North America

---

## July Workshop Schedule
**Website**: [EUMETNET AI Workshop 2025](https://www.eumetnet-ai.eu/2025/workshop3/)  
**Online option**: Register and when asked if attending in Offenbach, select “Other” and write “online”

### Proposed Schedule
- **09:00 – 09:40**: Data curation, Gap analysis and missing datasets  
  - Roope/Stephan present (15 minutes)  
  - Discussion (25 minutes), Roope chair, Stephan co-chair  
- **09:40 – 10:10**: Zarr best practices  
  - Roope present (10 minutes)  
  - Discussion (Roope chairs)  
- **10:10 – 10:30**: DestinE Data Lake → to be moved to Tuesday  
  - Miruna present  
- **11:00 – 11:15**: New OPERA – SEVIRI dataset on common grid  
  - Roope present  
- **10:30 – 11:00**: Coffee break  
- **11:15 – 11:45**: CDR (climate data records) vs NRT (near real time)  
  - Arianna  
  - Discussion, Arianna & Roope  
- **11:45 – 12:15**: Anemoi Datasets  
  - Stephan  
  - Discussion, Stephan & xx  
  - A bit longer time: how far we can go with Anemoi, what to do with applications where Anemoi is not optimal  
- **12:15 – 12:30**: Discussion (e.g. where are you stuck? What did you try?)  
  - Who wants to chair?  
  - Chaired by: Stephan & Arianna  

---

## Zarr Sub-Group Presentation Schedule

| Organisation      | Presenter         | Title / Topic                                | Time      |
|-------------------|-------------------|----------------------------------------------|-----------|
| ECMWF             | Florian Pinault   | Experiences of using Zarr within Anemoi      | June 13   |
| AEMET / NWC SAF   | Llorenç Lliso     | virtualizarr/icechunk experiments            | June 13   |
| GeoSphere         | Irene Schicker    | Reanalyses in Zarr                           | July 4    |
|                   |                   | *(Chaired by Miruna)*                        |           |

---

## Best Practices Document Timeline

- **Concept and Table of Content**: September  
- **First Draft**: October  

---

## Feature Detection Sub-Activity

New sub-activity to be covered under the E-AI WG1 umbrella:  
The Earth System Feature Detection group will build a joint working environment containing:
- Manual annotation platform  
- Data preparation tools  
- Database of identified features  
- Visualisation tools  

The platform will be hosted in the EWC and be available for those entitled to access (no EWC tenancy required).  

EUMETSAT is also starting to compose a global Earth System Feature Database to contain long time series of features identified from satellite data (especially from Climate Data Records).  

Currently, meetings are held once per month discussing the setup of the joint working environment. Interested people should contact Roope to get invited.  

[Minutes of the regular meetings](https://docs.google.com/document/d/10iaLfdiHha32JVd_-DUDpzQnRAasCeHQD5J7SB9jiMo/edit?tab=t.0)

---

## EUMETNET Data Workshop in Oslo
We are looking forward to an interesting hybrid workshop from **4–6 November** in Oslo  
**Website**: [https://www.met.no/prosjekter/dmw2025](https://www.met.no/prosjekter/dmw2025)  

Topics covered:  
- Data Rescue  
- Climate Observations  
- Quality Control  
- Data Management  
- Data Services  
- Homogenisation  
- Climate Data Analyses  
- Machine Learning / Artificial Intelligence use in those areas  

---

## Next Meetings
- **July 3**: Normal meeting  
- **August 7**: No meeting  
- **September 4**: Meeting as usual  
- **October onwards**: Normal schedule  

**EMS** will take place in the week of 7 September; data group presentation in the open data session.
