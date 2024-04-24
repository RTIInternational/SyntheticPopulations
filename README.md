# SyntheticPopulations
RTI Synthetic Population Data (README)

U.S. Synthetic Population
2010 Version 1.0
Quick Start Guide
May, 2014
Prepared by
RTI International
3040 Cornwallis Road
Research Triangle Park, NC 27709

This work was supported by the Models of Infectious Disease Agency Study (MIDAS) from the National Institute of General Medical Sciences (NIGMS), grant number U24GM087704. The content is solely the responsibility of the authors and does not necessarily represent the official views of the NIGMS or the National Institutes of Health.

# Overview and Introduction
RTI has developed a nationwide synthetic population of households and persons called the 2010 U.S. Synthesized Population dataset. The synthetic population is a detailed, spatially-explicit representation of the socio-demographic distribution of the U.S. population in a microdata form.

The data are distributed in a compressed file containing a series of ASCII files with comma-separated value.

# Downloading and Processing
The 2010 U.S. Synthesized Population data are available for download by state or by county from this repo. Users can download any combination of states or counties.
The names of the ASCII files provided with each extract follow a naming convention that identifies the version and contents of the data. Each ASCII file in a particular distribution contains a prefix consisting of:

- The synthetic population source year (e.g., “2010”)
- Synthesized population version number for that source year (e.g., “ver1”)
- Geographic identifier (e.g., FIPS state code for entire state extracts; FIPS state and county codes for county extracts)

For example, extract files for Version 1 of the 2010 data have the following naming convention:

- 2010_ver1_01_synth_households.txt (for an extract of state FIPS “01,” which is Alabama)
- 2010_ver1_01005_synth_households.txt (for an extract of state FIPS “01,” county FIPS “005,” which is Barbour County, Alabama)

If you wish to combine several county extracts into a single dataset prior to loading into your database or model, then simply remove the header line from each file, and then concatenate the records.

If you need help building a specific multi-county or multi-state study area dataset, please contact James Rineer (jrin@rti.org) or Nick Kruskamp (nkruskamp@rti.org).

# Data Identification and Metadata
Because different versions of the dataset have different contents, the metadata file that accompanies each set of ASCII files extracted for end user delivery is used to help identify and track versions.

The metadata file (e.g., 2010_ver1_[fips]_metadata.txt) is an ASCII file that contains essential information about the exact contents, source, and version of any particular synthetic population download, including information on the version number, data sources, and files in the distribution of each dataset. A complete description of the contents of the metadata file can be found in the data dictionary in Appendix C.

# Citing the U.S. Synthetic Population Database
RTI and its funding agency, the National Institutes of General Medical Sciences (NIGMS) request that you cite the 2010 U.S. Synthetic Population database in any publications or journal articles in which the data were used. The correct citation for the data is:
Wheaton, W.D. (May, 2014) 2010 U.S. Synthetic Population Ver. 1. RTI International. Retrieved from [https://github.com/RTIInternational/SyntheticPopulations](https://github.com/RTIInternational/SyntheticPopulations)

This Quick Start guide should be cited as:
Wheaton, W.D. 2014. “U.S. Synthetic Population Database 2010: Quick Start Guide”. RTI International. Retrieved from [RTI Synthetic Population Data (README)](https://github.com/RTIInternational/SyntheticPopulations/edit/main/README.md)


