# E-AI WG Data Curation Kick-off Meeting Minutes

## Time
14 October 2024 13 - 15 CEST

## Attendees
- Roope Tervo, EUMETSAT, roope.tervo@eumetsat.int
- Arianna Valmassoi, DWD, arianna.valmassoi@dwd.de
- Stephan Siemen, ECMWF, stephan.siemen@ecmwf.int
- ...

## Agenda
| Time   | Agenda                                      |
|--------|---------------------------------------------|
| 13:00  | Greetings and background                    |
| 13:15  | Round-table / Get to know each other poll   |
| 13:30  | Proposed ToR / tasks for the WG             |
|        | - What do we want to do as a group?           |
|        | - "I would need this"/ "I would like to participate with this N hours per month"     |
|        | First deliverables                          |
| 14:30  | Working practices, tools, meetings          |
| 14:50  | Next steps                                  |

Live draft here: https://docs.google.com/document/d/1jYyMo1h8u_xzHiIZBCH5z-mTcQLVabQ62-bLRPGyLnE/edit?tab=t.0 

## Discussion
41 participants

Following summaries the discussion during the kick-off. 

### Round-table / Get to know each other poll 
(https://www.menti.com/altmce3sswaa)

* Participants are asked to add email and github handle to the form to keep track on interested participants
* Initial poll results indicate that about 10 people are able to contribute more than 4 hours per month, supported by over 10 people being able to contribute 1-2 hours per month
* Participants are welcomed to list more specific application use of AI/ML and more specific type of data people are producing
* The group need to diversify between data and application (comment from the poll)
Future meetings, gap analyses, or discussion (Rocket) should specify AI/ML applications and different sorts of input data participants are working on

### Proposed ToR / tasks for the WG  
* The group discussed on questions: “What do we want to do as a group? “I would need this"/ "I would like to participate with this N hours per month“​
* Aim is to have first deliverables​ towards the end of 2024
* As in all E-AI groups, there are “active” and ”passive” groups. 
* It was noted that Git issues could be used not only for comments but to point out what is missing

#### 1st deliverable:
* Identify gaps of what we need in E-AI by the end of the year
* Interested participants are requested to contact via email/chat to express interests.

Timeline of the 1st deliverable - end of 2024: Should be just a simple document / list of datasets, their usage, and most important needs from an E-AI point of view.

#### Further work on gap analysis / as separate deliverable
Common best practice and common infrastructure would be needed:
* EWC or similar could be used for prototypes and testbeds
* Sharing of tools is important, i.e. internal/in-house dev of tools for converter of data format, how to best share these things so that they can work out of the box, including easy examples

Common infrastructure:
* It was noted that common infrastructure (similar to EWC) would be needed also for reprocessing.
Infrastructure. as code was proposed with a note that we have to avoid overlap with other WGs. 
* There is an open tenancy in the EWC (ECMWF side), currently sponsored by DWD. It is currently used especially for CI/CD pipelines.
* United Weather Centres (UWC, 11 countries) are doing data format conversions and preparation and volunteered to share the assets with a wider group. That would be an excellent starting point for the WG work.

Outlook of the next step after the first deliverable - it will be a wider discussion.

Having standards for encoding and naming conventions (i.e. parameter vocabulary) is important: e.g. use converting tools that works toward the standard formats with standard namings. For example the CORDEX variables for regional climate modeling (less targeted at weather forecasting though).

UWC has started to work on standardized formats. We should engage with this group to not duplicate the work.

Warning process (from the weather forecasting group): how to use the AI activities to not re-do the text warnings that are sent out in different languages. For this the Data Curation working group should consider impact data as one type of data. That was recognised as important but requires people to do the analyses. Such a catalogue would be useful for many application areas as well.

The topic of traditional data vs non-traditional data, either as training data or non-supervised learning, or validation was briefly discussed.

#### ToR: other activities 
There are other things beyond the gap analysis (but these are only ideas, add your own - their development/extension will depend on the interest from the community):

Propositions from the group:
1. Metadata: we do not mention metadata in any of the specific parts: how do we do it? We include it in the standardisation. In the first time, it is also intended as “how the lack of metadata hinders the use of this/that data”. We should make this more clear, as where it is included. Self-describing data formats such as CF-compliant NetCDF and maybe Zarr enforce some metadata.
2. The need to analyse and share data-proximate processing possibilities need to be added to the analysis. Would be important to focus on next steps and tools to make available
3. The lack of practical ways to share EO observations is still a big hinderage. That should be kept in focus. Hence, creating, or analyzing mechanism to share the data could be part of the gap analysis. 

##### Is there something missing? Different expectations from this meeting?
* Data compression + metadata filling so that we do not have too many different ways should be considered.
* Discussion on whether we should mirror repositories to avoid duplication/merge of multiple code in one? Link the developments in other E-AI WGs.
* Discussion on training vs. inference. Publishing training datasets is nice, but each training dataset needs its inference counterpart: a real-time inference data stream (metadata needed here!). This could be in some best practices or gap analysis that. We have to work with MLOps to avoid duplication.
* Tutorials (e.g. notebooks) are important


### Working practices, tools, meetings  
Next the group discussed practicalities how best to work together in the coming months:

* **Minutes**: they are now live, but they will be moved to github in a week or so.
* **Resources**: the work of the group will be managed through a repo in github - the coordination will be there and openly readable by everyone, but the code can be also somewhere else.
First deliverable written in markdown? or something else?
* **Email list**: is to be setup, it could be possible to register - include for now here: https://terminplaner6.dfn.de/en/p/753c865520370db6acb9aa4a80a43bfe-911670
* **Chat**: Hosted on EWC (https://chat.europeanweather.cloud) sync with the other WGs, done by the central management, and then everyone can join other WGs. public WGs channels for general discussion, and then private channels for discussion of ongoing deliverable/work, and have a public one once the work is done.

Meeting frequencies:
* Every 2 weeks for the gap analysis especially -> at least 3 meetings by the end of the year! We send polls for times for meetings, later next year we decide a fixed time.
  * Other sub-groups, once formed, can decide the timeline/frequency
  * “interest groups”: say something relevant to people that are interested but not working on these topics - every 3 months?

How to collect general info? 
* How to best make use of the github features/issues? There is also the Github discussion that could be used!

### Next steps and actions:
* Minutes will be open until rest of the week and curated to the github
* Interested people are asked to contact facilitators (roope.tervo@eumetsat.int; arianna.valmassoi@dwd.de; stephan.siemen@ecmwf.int) or via web form: https://terminplaner6.dfn.de/en/p/753c865520370db6acb9aa4a80a43bfe-911670 and provide email address, github handle, and how one wants to contribute
* Interested people are encouraged to register to EWC Rocket.chat https://chat.europeanweather.cloud 
Facilitators will send Doodle for working meetings for the rest of the year to everyone who has provided their email address (and via Rocket.chat) 

## Resources
- Presentations: [Kick-off slides](../presentations/2024-10-14_E-AI_WG%20Data_Curation_Kick-off.pdf)
- Discussion platform: https://chat.europeanweather.cloud
- Doodles on [front-page](../README.md)
