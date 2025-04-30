# Minutes of the WG1 Data Curation Working Meeting 5


**Participants – 30 Apr 2025**
- Stephan Siemen (ECMWF)
- Roope Tervo (EUMETSAT)
- Arianna Valmassoi (DWD)
- Sina Montazeri (EUMETSAT)
- Rónán Darcy (Met Éireann)
- Ben Fitzpatrick (UK Met Office)
- Yordan Radev (ECCC)
- Hugo Vandenbroucke-Menu (ECCC)
- Milena Dimitrijevic (ECCC)

---

## Agenda:
- Action review  
- Status of the Gap Analysis document  
- Canadian Surface Reanalysis (CaSR) presentation / Milena  
- Round-table on whether use cases are covered  

---

## Links for Convenience

- **Our GitHub:** [eumetnet-e-ai/wg1_data_curation](https://github.com/eumetnet-e-ai/wg1_data_curation) – Material and scripts for data curation  
- **Gap analysis document:** [Draft](https://github.com/eumetnet-e-ai/wg1_data_curation/tree/draft/gap_analysis)  
- **Nowcasting:** [Google Doc](https://docs.google.com/document/d/1iknFj36XdV19udaIsYJhVJLv2Hq-ARjO85jD0jfrYqw/edit?tab=t.0#heading=h.g7k4377ea9doMLCast)  
- **ML LAM:** [Google Doc](https://docs.google.com/document/d/1KzMHjl08ESMSpEwJ1eopbWfBp_2MXL-XL63KljWQCZU/edit?tab=t.0#heading=h.66rsmcqr6xup)  

---

## Minutes

### Actions:
- Everyone to add their own use cases and advertise them in their organisations.  
- `lcd@dmi.dk` to add regional reanalysis datasets list in the ML LAM community document in the Gap Analysis.  
- Leif and Marek to coordinate on July workshop tutorial content.  
- Milena Dimitrijevic to add regional reanalysis data to the Gap Analysis – some challenges with GitHub, but in progress.  
- Leif and Ben to coordinate on joint use case to the Gap Analysis – to be done by and discussed in the next meeting.  

### Gap Analysis Document
We got a new case study has been added (sentinel3), including challenges 

We should still add use cases: do we need specific meetings to address gaps in the use cases, i.e. model developers? Discuss it also on Wed. of the July workshop.
Question to ask: what should we, as data providers, should improve to better provide data for applications, such as E-AI-topics? Some guidance for thinking and discussion can be found from the template.md file from the gap_analyses.

People to approach: developers and service providers in our own organization, related both to ML and classical applications.

Start with next month already if possible

### Milena Dimitrijevic – Canadian Surface Reanalyses
Shared website (https://hpfx.collab.science.gc.ca/~scar700/rcas-casr/index.html Canadian Surface Reanalysis (CaSR))  that includes the versions tracking, including the list of contributors.

Technical details are summarized in the dataset specifics, including the explanation of the domain that includes the trans-boundaries watersheds. Focused especially providing boundaries for hydrological models. 

Other types of users are there for your data? Several university GMC. Helped in the correction of specific problems that are later corrected in follow-up versions. 

There are plans to reprocess the data in a Climate change projection- friendly format for application in explaining the impacts.

Advanced users: access to their model code is more complicated due to security access.

Data assimilation performed only in the land component,  the atmosphere is a forecast started from ERA5.

They provide 2 types of precip: 
Direct precip output from the model
Precipitation corrected by observations.

Output available through their online archive: https://github.com/julemai/CaSPAr/wiki/Available-products

Contains also confidence index for part of the params

https://hpfx.collab.science.gc.ca/~scar700/rcas-casr/data/CaSRv3.1/netcdf/ <- path to the files

Reanalyses is not real-time: 1.5 years lag. They provide a temporary script that can extend NRT if needed, but it uses the operational atmosphere system. It provides data from NWP data. ECCC keeps one continuous time series of old model runs containing the latest forecast lead times of each hour. 

There is the specific page on how to access the data, including a webpage that allows to select fields/regions in the data.

Format: netcdf.

Quality analyses: going from reanalyses to NRT - work in progress.

Assimilated observations not available. They are based on NOAA hourly observations, though, which are available. (Integrated surface observations, another available but not used here https://psl.noaa.gov/data/nnja_obs/). 

Do other agencies share assimilated observations? DWD shares with other agencies (e.g. within the COSMO-consortium) but not publicly. Having clear tools/framework to share the data is challenging. Could we use WIS2 for that?

How much Zarr is used? Not much in reanalyses context due to the legacy. Having multiple bufr dialects cause a lot of problems. In general, observations are using more and more zarr, i.e. ESA, EUMETSAT and Anemoi. 

Satellite data are not used in CaSR at the moment due to time limitations. Getting historical data is challenging due to consistency challenges.  JMA have good concept for reanalyses and limiting observational systems (e.g. radar/satellites): DWD and BOM are applying it as well. 

Radar data are also not used at the moment. Data is not homogenous enough for the long time series. 

EUMETSAT, NOAA are having a GeoRing project to create global harmonised FCDR fromall geostationary satellites of the EUMETSAT, NOAA and JMA satellites. The data are provided as satellite-specific and composite data. The test data should be out end of 2025. 

### Data Tooling tips

gribscan (used to convert DANRA GRIB files to zarr): https://github.com/gribscan/gribscan, and here's a recent demo Leif gave: https://github.com/leifdenby/gribscan-demo
Iris (https://scitools-iris.readthedocs.io/en/latest/further_topics/ugrid/data_model.html) can do various operations on unstructured grids, but no differential calculus - will save link to pyshtools

Do we want to contain a list of tools in the gap analyses?
- probably as separate document
- are we giving recommendations? We should get context right and keep list living
- others can also add their software if they prefer to - based on comprehensive and detailed pull-requests.
- more detailed aspect of the analyses to be discussed later in these meetings, possibly late this year or early next year

### Zarr sub-group presentation schedule

| Organisation       | Presenter                     | Title                                                      | Preferred Duration | Preferred Month |
|--------------------|-------------------------------|------------------------------------------------------------|--------------------|-----------------|
| UKMO               | Mark Burgoyne                 | Experiments in storing NWP data as Zarr/Kerchunk/VirtualiZarr | –                  | 9 May           |
| GeoSphere          | Irene Schicker                | Reanalyses in Zarr                                         | –                  | 9 May           |
| ECMWF              | TBC, contact: Stephan Siemen  | Experiences of using Zarr within Anemoi framework          | 15–20 min          | June 13         |
| AEMET / NWC SAF    | Llorenç Lliso                 | virtualizarr/icechunk experiments                          | –                  | June 13         |

### Next meeting

On 5 June