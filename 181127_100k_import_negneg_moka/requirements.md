# 100k Genome Project - Import negative negative cases to Moka
## Participants
- Product owner: Viapath Genome Informatics
- Team: Viapath Genome Informatics
- Stakeholders: Viapath Genome Informatics, Viapath Genetics laboratories
- Other key relationships:

## Current Status
Draft

## Purpose
Negative negative 100k Genome Project cases are defined as cases where no Tier 1, 2 (and also CIP candidates where this analysis has been performed) have been identified. These cases can have negative reports issued automatically. The processs of reporting negative negatives is in the process of being automated. The first step of this process requires negative negative cases to be identified and booked into Moka at regular intervals.

## Project Goals & Objectives
* Automatically import all new negative negative 100k results into Moka to allow generation of negative reports.

## Requirements
### Functional
* Identify negative negative cases in the Genomics England Clinical Interpretation Portal that are not already in Moka.
* For each case:
  * If patient is not already in Moka, import details from GeneWorks.
  * Create an NGS test record in Moka, recording the Interpretation Request ID and Participant ID (proband) and assigning a negative negative result code.
  * Look up referring clinician in LabKey:
    * If clinician name has an exact match in the Moka Checker table, record them as referring clinician in Moka.
    * Otherwise, alert user that they will need to add clinician manually.

### Technical (non-functional)
* Interact with the CIP-API using [JellyPy](https://github.com/NHS-NGS/JellyPy) and [GeL models](https://gelreportmodels.genomicsengland.co.uk/) 
  * Python 3
  * Linux
  * N3 network
* Incorporate into existing Moka system:
  * Microsoft Access front end
  * MS SQL server backend
* Adhere to minimal viable product
* Reusable code

### Usability
- Set up to run automatically each night
