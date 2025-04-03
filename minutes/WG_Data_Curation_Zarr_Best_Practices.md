# Minutes of the WG1 Data Curation Zarr-profiles

## Meeting #1 24 Jan 2025

### Participants
- Roope Tervo (EUMETSAT)
- Stephan Siemen (ECMWF)
- Florian Pinault (ECMWF)
- Christian Lessig (ECMWF)
- Santeri Oksman (FMI)
- Irene Schicker (GeoSphere Austria)
- Petrina Papazek (GeoSphere Austria)
- Mark Burgoyne (UK Met Office)
- Jeremy Tandy (UK Met Office)
- Anna-Lena Erdmann (EUMETSAT)
- Simon De Kock (RMI (Belgium), VUB)
- Carlos Horn (EUMETSAT)
- Andreas Tack
- Sina Montazeri (EUMETSAT)
- Miruna Stoicescu (EUMETSAT)
- Oriol Hinojo Comellas (EUMETSAT)
- Michael Schick (EUMETSAT)
- Gabriela Aznar Siguan (MeteoSwiss)
- Patrik Senn (MeteoSwiss)
- Nikolay Koldunov (AWI)

## Background
WG1 Data curation WG meeting 3 concluded:

“Zarr standardisation” is very urgent, cause many people are writing the Zarr files right now! So it is really needed to avoid re-creating the Zarr again.
Effort ongoing at the ANEMOI side, but still needs harmonisation, maybe the internal structure will be different to what we are used to NetCDF.
Zarr is a very broad data format, the format behind it can be very different and same for metadata associated.

Which lead to an invitation:

The need to have joint conventions on Zarr formats for ML/AI applications has become evident in several discussions, including E-AI workshops and working groups. Hence, as part of the E-AI Working Group on Data Curation, we would like to invite experts to join the work of creating Zarr profile(s) to be used in the activities.

The Zarr profiles should focus on data-related definitions such as whether to include all parameters into a single Zarr or dividing them over multiple Zarrs, chunking, compression, etc., and also guidelines for metadata (e.g. by following CF-conventions).

The first goal is supporting applications in the E-AI program, but later work could be integrated with initiatives such as OGC. The team is expected to deliver the first version of the profile(s) in 2025.

The same meeting also noted:

Similar actions have been also taken by MLCast/mllam: GitHub - mllam/mllam-data-interface. They have it as a python package - interface from both the data and ML-model side. Traceability of the data should be included as well, affecting mainly metadata requirements. Different applications and training and interference have different requirements so more than one profile is needed.

## Agenda:
- Setting up
- ToR
- Way forward
- Contributors
- Used tools (GitHub / Google docs)
- Next steps & practicalities

## Minutes:
### Terms of Reference for this work
- Do we agree with the original idea?
- Exact content? To be discussed in the next meeting?

We need status quo, we should start sharing best practices, maybe first little virtual workshop to tell current activities with 2 slides.

What’s objective? We want to ease both writing Zarr and consuming Zarr in some specific use cases. We should be very clear which use cases we can address. Notably, just exchanging information is an objective. Addressing low level optimisation such as chunking should not be addressed too early. Point for later discussion: are we thinking about "native" Zarr, or Zarr + indexes onto grib / netCDF ... VirtualiZarr / Kerchunk. Maybe it doesn't matter if we focus on the "metadata" parts of a Zarr object? Other things to address:
- Missing values
- Zarr versions
- Controlled vocabularies to use, e.g., for parameter names

### Existing initiatives:
- ESA Sentinel data
- CMEMS
- Anemoi
- OGC GeoZarr [GeoZarr Spec](https://github.com/zarr-developers/geozarr-spec/blob/main/geozarr-spec.md)

### Discussion on different ways to categories:
- analyses/forecast vs. observations
- gridded vs. non-gridded (LEO, ground observations, etc.)
- training or data exchange

There was discussion on what kind of data is Zarr suitable for? E.g. simulation data (regular hypercubes) - or observation data (irregular data, or tabular data) or both? Zarr is clearly more suitable for regular hypercubes but on the other hand is used also for LEO satellite data in ML training.

Roope questioned whether the participants see the work worth doing. The meeting concluded that exchanging information makes sense and that we should also follow OGC very closely. Notably, OGC progress will be relatively slow but this group will need time too.

## Way forward
Agreed to start discussion and collect the best practices to as knowledge base. These can possibly be enhanced to as profile(s) if that seems sensible. Information regarding use cases are needed also, they can be added to wg1_data_curation/gap_analysis/e_ai_data_gap_analyses.md at main · eumetnet-e-ai/wg1_data_curation.

### Contributors
Roope offered to facilitate the group but asked for others to step in. No-one volunteered in the meeting but later Carlos promised to co-facilitate the group starting from the second half of the year.

Who can contribute in analysing?
- ECMWF will provide input
- EUMETSAT will provide input
- Miruna promised to invite relevant people to report regarding GeoZarr

Others willing to facilitate the group or who can contribute to the analyses are asked to add their names here or be in contact with the E-AI WG Data Curation facilitators.

### Tools & practicalities
- Github or google docs? → notes in google docs and analysis and profile in:
- eumetnet-e-ai/wg1_data_curation: Material and Scripts for Data Curation
- EWC discussion platform (https://chat.europeanweather.cloud)
- Meeting frequency

The group agreed that once per month is a good meeting frequency. However, the group noted that with this tempo, it is very important to agree on actions for the next meeting. Every meeting should have clear goals on what we want to achieve.

Presumably: first meeting in 2-3 weeks, first Friday of each month 14-15 CET

Agreed that participants can add preferences but no additions were given.

## Next steps
Agreed that next step is to have necessary amount of meetings to exchange everyone’s use cases

Following actions were agreed:
- Roope will set up a table for people to indicate whether and how long presentation they want to provide
- Everyone to fulfill the table
- Everyone can add they preferences about their meeting times
- Roope to send invitation to the next meetings

### Presentation schedule

| Organisation | Presenter | Title | Preferred duration | Preferred month |
|--------------|-----------|-------|--------------------|-----------------|
| EODC         | Christoph Remer | Zarr experiences at ESA | 20 min | 11 Apr |
| EUMETSAT     | Anna-Lena Erdman, Armagan Karatosun | Zarr experiments at EUMETSAT | | 11 Apr |
| UKMO         | Mark Burgoyne | Experiments in storing NWP data as Zarr/Kerchunk/VirtualiZarr | | May |
| GeoSphere    | Irene Schicker | Reanalyses in Zarr | | May |
| ECMWF        | TBC | Experiences of using zarr within Anemoi framework | 15-20 min | June? |
| AEMET / NWC SAF | Llorenç Lliso | virtualizarr/icechunk experiments | | June 13 |

## Meeting on 14 March

### Participants
- Roope Tervo
- Irene Schicker
- Christian Lessig
- Mark Burgoyne
- Petrina Papazek
- Miruna Stoicescu

### Minutes
- ESA webinar series on Zarr data:
  - [LinkedIn Announcement](https://www.linkedin.com/feed/update/activity:7305156712443854848)
  - [Link for registration](https://us02web.zoom.us/webinar/register/WN_MzGnEYQKSc6zGYOchzCznQ#/registration)
- ECMWF and UKMO are working on ‘containerized Zarr’ / virtual zarrs based on original formats (grib / fdb) to avoid needing to duplicate the data.

We should get in touch with climate community
- Roope and Christian to invite relevant people