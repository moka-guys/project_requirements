# Detection of unique spiked-in sample identifiers in CGH Array data
## Participants
- Product owner: Graeme Smith
- Team: Viapath Genome Informatics
- Stakeholders: Arrays, Viapath Genome Informatics

## Current Status
Draft
- 11/1/2018

## Purpose
Check for sample mix-ups in CGH Array data.

## Project Goals & Objectives
Ensure that any possible sample swaps are detected from Array CGH data and flagged for further investigation by Clinical Scientists.  This is accomplished using a unique combination of 3 'spiked-in' probes which identify each sample.  This App compares the detected 'spiked-in' probes to those expected on the sample sheet and raises a flag if there is a mismatch. Additionally the script throws an error if more or less than 3 probes are detected in a sample as this may indicate a sample switch, contamination, or that one or more spike in probes have failed.    

## Requirements
### Functional
The Resulting App should:
* Allow users to run the app from within Moka.
* As good practice two sets of plate layouts should be provided for spiking-in probes (Sets A & B).  Selection of set A or B will be done manually by the person creating runsheets with the set used being alternated between runs.
* Two use case scenarios need to be catered for:
    * Full 96 plate runs (Wells A-H:1-12)
    * Half 96 plate runs (Wells A-H:1-3 & A-H:7-9)
* In total 96 unique probes are required - 48 for the Red Channel and 48 for the Green Channel.

The App should also:
* Record in Moka that this QC step has been run for audit purposes.
* If the QC step is passed (Sample and Unique Trio match)
    * Record in Moka that QC step was passed.
* If QC step is Failed
    * Record in Moka that QC step failed.
    * Flag issue to user.
    * Provide a table to user showing the details of the samples which failed.
* Full results must be available as a text file to aid in troubleshooting.

### Technical (non-functional)
* Incorporated into existing Moka system.
* The Moka table ArrayLabelledDNA requires a column identifying which trio of identifying probes are assigned to each well (Two columns - Set A and B).
* Python script to parse the relevant feature extraction file from \Genetics\Data2\Array\FeatureExtraction - the file name required can be constructed from the ArrayID key in Moka 
* Script checks each of the 10 spiked-in probes (present in triplicate on the array) in the FE file, probe is considered present if that probe is saturated (Boolean Value of 1 in the 'gIsSaturated' or 'rIsSaturated' fields)
    * If <3 probes detected - throw an error (Probe has failed)
    * If >3 probes detected - throws an error (Cross-contamination possible)
    * If mismatch between sample ID and unique identifying probes flag issue to user.
        * Produce minimal summary table in Moka to aid in troubleshooting.
        * Record full results in txt file to aid any further troubleshooting.
    * Additional QC columns required in the Moka table 'ArrayLabelling' to display these results and record that this test has been performed.  
* Adhere to minimal viable product

### Usability
* Must be simple for clinical scientists to access and use.
* Must be consistent with existing Moka data structures and application logic.
