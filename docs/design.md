# A summary of how the corpus was made

This site covers the basics. You can also read our [open-access paper describing the corpus](https://www.aclweb.org/anthology/2020.lrec-1.503/).

## Participants

Thirty-four early Cantonese English bilinguals were recruited from the UBC community in Vancouver, BC, Canada. They were recruited via word of mouth, social media, clubs, the linguistics subject pool, and other similar methods. A detailed summary of the participants' language background information is provided in the [corpus download](/download). 

It is worth noting that the Cantonese-speaking community in the Metro Vancouver area is a unique kind of bilingual community. Not only is Cantonese very widely spoken in the area, it has been for a *long time*, and by a heterogeneous group of people. Statistics Canada has very useful visualizations for getting a broad picture of the linguistic landscape&mdash;in particular: [Proportion of mother tongue responses for various regions in Canada, 2016 Census](https://www12.statcan.gc.ca/census-recensement/2016/dp-pd/dv-vd/lang/index-eng.cfm). 

## Recording setup

All of the recordings in the SpiCE corpus were conducted by two Cantonese-English bilingual research assistants, in a quiet room in Stores Road Annex at the University of British Columbia. The participant and research assistants were all seated around a table

Recordings were made in Audacity, using:

- Sound Devices USBPre2 Portable Audio Interface
- AKG C520 head-mounted microphones

Recordings are:

- Stereo (L: participant, R: interviewer), with the exception of one mono file with just the participant
- 44.1 KHz sampling rate
- 24-bit resolution

## Procedures

Participants spent approximately 90 minutes in the lab, and completed three tasks for each language, following informed consent. The order of languages was counterbalanced (this information is included in the participant summary file). 

### Task 1: Sentences


### Task 2: Storyboard

Participant narrated the same cartoon in both languages. The cartoon&mdash;[Thank You Notes](http://totemfieldstoryboards.org/stories/thank_you_notes/)&mdash;was originally developed for field research and elicited vocabulary related to family members and simple gift-giving.

### Task 3: Interview

The conversational interview covered a variety of everyday topics such as culture, food, school, hobbies, and family.


## Transcription & Annotation

Broadly, the pipeline follows these steps:

1. Initial transcripts produced with Google Cloud Speech-to-Text
2. Hand-correction of orthographic transcripts by researchers (additional detail to be provided by time of release)
3. Forced-alignment with the Montreal Forced Aligner

