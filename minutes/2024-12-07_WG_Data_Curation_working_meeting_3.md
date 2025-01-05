
# Minutes of the WG1 Data Curation Working Meeting 3

## Participants
**5 Dec 2024**

- Roope Tervo (EUMETSAT)
- Sina Montazeri (EUMETSAT)
- Anna-Lena Erdmann (EUMETSAT)
- Adam Jaczewski (IMWM, Poland)
- Oriol Hinojo (EUMETSAT)
- Llorenç Lliso (AEMET Spain)
- Leif Denby (DMI)
- Marek Jacob (DWD)
- Arianna Valmassoi (DWD)
- Albert Rabaneda
- Ben Fitzpatrick
- José Lorenzo Lliso Valverde
- Rónán Darcy
- Stephan Siemen

## Agenda
- Setting up
- Status & action check
- Use cases & report
- Other actions, Zarr standardisation & discovery
- Next year’s meetings
- Next steps

## Links for Convenience
- Our GitHub: eumetnet-e-ai/wg1_data_curation: Material and Scripts for Data Curation
- Nowcasting: Google Doc
- ML LAM: Google Doc

## Minutes

### Actions
#### Next Steps Gap Analyses:
- Everyone to check and start writing the content
- Everyone to send the invitation to their contacts
- Stephan to invite ECMWF side (including EWC use cases) to contribute - add by this week
- Everyone to add your own use cases
- Leif to add use cases from MLLAM and MLCast community work so far
- Llorenzo to add METAR data
- Everyone to write gap analyses
- Everyone to keep providing use cases
- Roope to send meeting invitation for next year

#### Zarr Standardization Next Steps:
- Roope to draft vision of Zarr profile subgroup and send to E-AI stakeholders
- Miruna to ask NASA and CMEMS for Zarr input
- Arianna and Marek to discuss inside DWD to find someone to contribute

### Important Dates:
- **E-AI Products and Services Workshop:** 2025-07-07 – 2025-07-10, in-person workshop in Offenbach (Germany)

### Use Cases & Report
- We need to add further cases to the list + start writing the text.
- Met Office and AEMET will add more cases in the next week(s).
- Add MLLAM and MLCast use cases, focusing on the challenges even if the work is still in progress.

### Other Actions

#### Zarr Profiles 

Invitations
```
The need to have joint conventions on Zarr formats for ML/AI applications has become evident in several discussions, including E-AI workshops and working groups. Hence, as part of the E-AI Working Group on Data Curation, we would like to invite experts to join the work of creating Zarr profile(s) to be used in the activities.

The Zarr profiles should focus on data-related definitions such as whether to include all parameters into a single Zarr or dividing them over multiple Zarrs, chunking, compression, etc., and also guidelines for metadata (e.g. by following CF-conventions).

The first goal is supporting applications in the E-AI program, but later work could be integrated with initiatives such as OGC. The team is expected to deliver the first version of the profile(s) in 2025.

If you have interest and the possibility to contribute, please fill out the doodle poll for the first meeting at Doodle Poll (and feel free to forward to potential contributors).

You are also welcome to provide feedback regarding the scope, working methods, timeline, etc!
```

Similar actions have been also taken by MLCast/mllam: GitHub - mllam/mllam-data-interface. They have it as a python package - interface from both the data and ML-model side. Traceability of the data should be included as well, affecting mainly metadata requirements. Different applications and training and interference have different requirements so more than one profile is needed.

Also, ECMWF has quite much material regarding the Zarr standardization which will be shared by Stephan.

#### Data Sharing and Discovery
- MLCast working group have done great work already: bit.ly/mlcast
- MLCast uses an intake catalogue, allowing a convenient way for online access to datasets on different systems.
- Remote caching: Xarray Tutorial
- Pangeo intake catalog: Pangeo Catalog (with CMIP)
- IPFS is a tool to implement local caching of globally available data.

##### Goals for This Group's Actions:
- Resolve discovery problem from application point of view
- Provide place for more documentation, tools to use and convert the data
- Provide mechanism to share data which are not shared via other data services

Intake could be used to achieve these goals.

##### Why Not Anemoi?
- Insufficient functionality for wider goals
- Will be fully OSS and open to contribution
- Needs central hosting
- Too tight on the graph structure.

##### Why Not Hugging Face?
- More a repo to deposit the data, is it possible to use it to build a catalogue?
- Expensive? But all the ML world is using it.
- Can we still use it for data that are not open?

##### Possibility:
- GitHub repository of lots of JSON metadata for the main obs and model datasets, similar to STAC JSON, which will then go and populate a STAC catalogue.
- Using STACK with intake: Intake-STAC, STAC would also be an option, but it is more restrictive than intake in that there is a query protocol that is specific to geographical data, whereas intake doesn't prescribe anything.

### Next Year’s Meetings
- First Friday of the month at 2PM CEST
- Link: will be a recurrent link.

### Next Steps
- Everyone to write gap analyses
- Everyone to keep providing use cases
- Roope to send meeting invitation for next year
