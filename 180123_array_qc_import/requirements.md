# Array Batch QC Import Requirements
## Participants
- Product owner: Viapath Genome Informatics
- Team: Viapath Genome Informatics
- Stakeholders: Viapath Genome Informatics, Viapath Genetics laboratories
- Other key relationships:

## Current Status
Final
- 23/01/2018

## Purpose
Currently array QC metrics are entered manually into Moka, and a pdf report is attached as an OLE link. This process is laborious and the performance has degraded significantly since swithcing to Access 2013. The purpose of this project is to automate the process for importing array QC metrics into Moka.

## Project Goals & Objectives
* Automatically import QC metrics for an array run into Moka.

## Requirements
### Functional
* Identify folder containing feature extraction files for a particular run
* Extract QC metrics from the feature extraction files
* Insert the QC metrics into Moka

### Technical (non-functional)
* Incorporated into existing Moka system:
  * Microsoft Access front end
  * MS SQL server backend
* Python script to parse feature extraction files
* Adhere to minimal viable product

### Usability
- Incorporate into existing batched array QC form to maintain backwards compatibility
