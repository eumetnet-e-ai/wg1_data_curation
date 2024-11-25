Sure, here's the markdown version:

# Minutes of the WG1 Data Curation Working Meeting 2

**22 Nov 2024**

## Participants
- Roope Tervo (EUMETSAT)
- Stephan Siemen (ECMWF)
- Sina Montazeri (EUMETSAT)
- Adam Jaczewski (IMWM, Poland)
- Marek Jacob (DWD, Germany)
- Arianna Valmassoi (DWD)
- José Lorenzo Lliso Valverde (AEMET Spain)
- Miruna Stoicescu
- Rónán Darcy

## Agenda:
- Setting up
- Status & action check
- Discuss writing the report/analyses
- Other potential actions for the group, i.e. Zarr standardisation
- Next steps

## Links for Convenience
- [Nowcasting](https://docs.google.com/document/d/1iknFj36XdV19udaIsYJhVJLv2Hq-ARjO85jD0jfrYqw/edit?tab=t.0#heading=h.g7k4377ea9doMLCast_Community)
- [ML LAM Document](https://docs.google.com/document/d/1KzMHjl08ESMSpEwJ1eopbWfBp_2MXL-XL63KljWQCZU/edit?tab=t.0#heading=h.66rsmcqr6xup)

## Minutes:

### Action review:
- Roope to update the template -DONE
- Roope to onboard others to GitHub as maintainer -DONE
- Roope to formulate an invitation (all welcome to comment!) -DONE
- Everyone to send the invitation to their contacts
- Roope EUMETSAT side of the EWC use cases -DONE
- Stephan ECMWF side
- Marek to send the invitation to contribute to E-AI -DONE
- Everyone to add your own use cases
- Roope, Stephan, and Arianna to prepare analysis document structure

### Important Dates:
- **E-AI Products and Services Workshop:** 2025-07-07 – 2025-07-10, in-person workshop in Offenbach (Germany)
- **Gap analyses draft deadline:** 5 December - 10AM (i.e. next meeting)

### First Draft of Analyses Document Structure:
- [Proposed structure](../gap_analysis/e_ai_data_gap_analyses.md)

### Gap Analyses:
- We do not want too many examples at the moment, since we have 2 months left to finish the report. The example of usages can grow afterwards, but at the moment we keep it simple. NB: we just look at what people need, but then of course we can go back to our institutions and give feedback so that the needs can be addressed.
- Forward an invitation with concrete todo to the other WGs in E-AI? --> done with use cases, could try to involve others

#### Structure of the Gap Analyses Discussion:
- At the moment we have 4 use cases. For us it is interesting to know already what would be required and what is missing.
  - Cloudcast
  - Icing
  - Multi Source to Precipitation
  - Tropical Storm Detection

- Should we produce a tool or should we produce the data cubes? That is the complex question, and maybe we will stay in the middle: producing the data cubes for the widely used dataset, and maybe only give the tools for the very specific applications. This will be better defined next year, maybe at the workshop that is planned in Offenbach.

- Add category of the use case and/or available data if possible
- Add a new Chapter for “future data inventory” - include there the basic info, do not write too much, same as for the current dataset.
- Future directions: do/donts feedback from the ML applications to the different data providers (best practices).
- Joint use case characteristics and preferences analyses

#### How to Write:
- By next time we should have a draft ready - 5 December 10AM
- Keep flexible and short.

### Zarr Standardization:
- It is very urgent, cause many people are writing the Zarr files right now! So it is really needed to avoid re-creating the Zarr again.
- Effort ongoing at the ANEMOI side, but still needs harmonisation, maybe the internal structure will be different to what we are used to NetCDF.
- Contacts internally to check what is already ongoing - ESA has an ITT to convert Sentinel data to Zarr with rather detailed definition
- Operational approach to maintain the Zarr file, as well as the bufr/netcdf.
- Zarr is a very broad data format, the format behind it can be very different and same for metadata associated.

## Next Steps

### Gap analyses
- Roope to update the document structure following the discussion
- Everyone to check and start writing the content
- Everyone to send the invitation to their contacts
- Stephan to invite ECMWF side (including EWC use cases) to contribute
- Everyone to add your own use cases
- Roope, Stephan, and Arianna to prepare analysis document structure

### Zarr Standardization Next Steps
- Roope to draft vision of Zarr profile subgroup and send to E-AI stakeholders
- Miruna to ask NASA and CMEMS for Zarr input
- Arianna and Marek to discuss inside DWD to find someone to contribute
- Stephan to contact Anemoi for Zarr work
