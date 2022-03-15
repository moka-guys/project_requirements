# SNP Haplotying
## Participants
- Product owner: Graeme Smith
- Team: Viapath Genome Informatics
- Stakeholders: PGD team, Viapath Genome Informatics, Pam Renwick,  Heema Hewitson

## Current Status
Draft
- 0/3/2022

## Purpose
Provide automated SNP Haplotyping analysis of SNP Array data for PGD reports

###

## Project Goals & Objectives
The PGD are currently doing manual filtering of SNP Array data - this process would benefit from automation.
This need to be done by the end of April.

## Requirements

### Functional

Support is required for the following modes of inheritance:
* Autosomal dominant
* Autosomal recessive
* X-linked recessive
* Autosomal exclusion (Rarely used) TODO Discuss whether it needs implementing in 1st  

# Input
* The user would like to provide the metadata for the analysis as an csv, it should contain:
  * The mode of inheritance
  * Metadata on the analysis
  * Metadata on the parents and reference (affected, unaffected, carrier, relationship to proband)
* The summary SNP array data will be input as a text file which has already been filtered for the region of interest.

# Output
Useful SNPs should be counted:
  * Within gene
  * Within 1mb flanking regions
  * Within 2mb flanking regions
TODO Check with PGD team if 'With in 2mb' should count genes in 0-2mb or 1-2mb

The following QC metrics should be produced:
* Number of discordant genes
* Number of No Calls

Classify embryos based on low risk or high risk alleles
  * Useful SNPs should be annotated with dbSNP RS IDs

### Technical (non-functional)
* Easily maintainable by the Viapath Bioinformatics team
  * Written in python3

### Usability
* Must be simple to access and use. TODO Discuss where to host script and best way to run it from Trust

