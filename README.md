# SyntheticPopulations
RTI Synthetic Population Data (README)

U.S. Synthetic Population
2010 Version 1.0
Quick Start Guide
May, 2014 (Original) Apr, 2024 (Updated and converted to README)
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

# Data Sources
The following data sources were used to compile the information in the synthesized population data.
- 2007–2011 Public Use Microdata Sample: The Public Use Microdata Sample (PUMS) files are generated from responses to the ACS and include most of the variables that are included in the survey. The smallest geographic unit for which the PUMS data are collected is the Public Use Microdata Area (PUMA). These PUMAs are defined for each decennial census and are based on minimum population thresholds of 100,000 people. This research used the 5% sample PUMA data, which reflect 5% of actual household responses used to create the dataset. This method ensures the confidentiality of respondents.
  * Download: The 2007–20011 PUMS data were downloaded from http://www2.census.gov/acs2011_5yr/pums/.
- U.S. Census Bureau Topologically Integrated Geographic Encoding and Referencing (TIGER) Data Block Group Boundaries: The TIGER 2010 version of block group boundaries includes all 50 states and the District of Columbia but not Puerto Rico. Water features (lakes, wide rivers, coastal water, etc.) within the block groups were removed, along with block groups that were entirely on water. Other block groups were either modified or replaced, resulting in nationwide block group data that match the ACS coding.
  * Download: U.S. Census Bureau 2010 Census Redistricting (P.L. 94-171) TIGER/Line Shapefiles were downloaded from the following FTP site: ftp://ftp2.census.gov/geo/pvs/tiger2010st/.
- 2007–20011 American Community Survey (ACS): The ACS data were collected over 60 months, between January 2007 and December 2011. The values represent the average characteristics over the 5-year period.
  * Download: The 2007–2011 5-year summary files were downloaded from http://www2.census.gov/acs2011_5yr/summaryfile/2007-2011_ACSSF_All_In_2_Giant_Files(Experienced-Users-Only)/.
- Integrated Climate and Land Use Scenarios (ICLUS). Baseline gridded population data at 90-meter resolution. This dataset was used to place synthetic households across the landscape.
  * Download: Information on ICLUS and download options available at: http://www.epa.gov/ncea/global/iclus/.
- ESRI Business Analyst: This data source provided some locations for nursing homes, universities, prisons, and military bases.
- 2010 Census SF1: Counts of households by household size by blockgroup and data on age and gender distributions in group quarters was provided by the 2010 Census SF1 files.

# Data Files Contained in Each Synthesized Dataset
Synthesized datasets are provided to the user community in subsets defined by geographic area (e.g., a county, set of counties, state, or set of states). Each synthesized dataset contains several individual ASCII text files that, together, provide all the synthesized data for a particular geographic area. The individual ASCII text files are detailed in Table 1.

**Table 1. List of ASCII files in a synthetic population dataset.**

| File | Contents | 
| :---------------------- | :------------------------------------------------------------------------------ | 
| [prefix]_metadata.txt|Contains metadata on the contents of the extract synthetic population data. | 
|[prefix]_synth_households.txt|Contains the location and descriptive attributes for each household. Household records in the synth_households.txt file link to individual person records in the synth_people.txt table.| 
|[prefix]_synth_people.txt|Contains a record for each person, along with his or her age, race, and sex. These synthetic person records link to the synth_households.txt file (via the sp_hh_id field) and/or to the U.S. Census Public Use Microdata Sample (PUMS) attributes from pums_p.txt (via the serialno field).|
|[prefix]_schools.txt|Contains locations and descriptive attributes of each public and private school. The sp_school_ids link to the school_id variable in the synth_people.txt table.|
|[prefix]_workplaces.txt|Contains locations and sizes of each workplace. The sp_work_id links to the work_id variable in the synth_people.txt table.| 
|[prefix]_synth_gq.txt|Contains locations of group quarters and counts of individuals in each one by group quarters type.|
|[prefix]_synth_gq_people.txt|Contains age and sex characteristics and link to group quarters type for each group quarters resident.|
|[prefix]_pums_h.txt|Contains complete PUMS household records from the original PUMS 5% data. Links to the [prefix]_synth_households.txt file via the serialno field.|
|[prefix]_pums_p.txt|Contains complete PUMS person records from the original PUMS 5% data. Links to the [prefix]_synth_persons.txt file the serialno field.|
|[prefix]_age_compare.txt|Contains data on the expected count of households and the actual count of households for each block group and each of the seven age categories (see Appendix B for codes).|
|[prefix]_race_compare.txt|Contains data on the expected count of households and the actual count of households for each block group and each of the five race categories (see Appendix B for codes).|
|[prefix]_income_compare.txt|Contains data on the expected count of households and the actual count of households for each block group and each of the seven income categories (see Appendix B for codes).|
|[prefix]_size_compare.txt|Contains data on the expected count of households and the actual count of households for each block group and each of the seven size categories (see Appendix B for codes).|
|[prefix]_summary_compare.txt|Contains summary information on the expected and final matches for each of the four matching variables and a summary value, by block group, that provides an overall measure of how closely the synthesized households for a block group match the expectations of the ACS data.|

# Geographic Contents of Each Synthesized Dataset
Because the synthetic population has been exported into state and county study areas, it is important to understand how the boundary issues are handled in each exported dataset. Figure 1 illustrates the spatial contents of each individual state or county dataset.

**TBD placeholder**
**Figure 1. Spatial contents of a synthetic populatoin dataset.**

The result is that each dataset includes all households and persons who reside in the state or county dataset you are downloading. The data set also includes ALL schools or workplaces that those residents are assigned to, whether or not the school/workplace is inside the state or county. No synthetic persons that reside outside the study area are included in the data set nor are they included in the schools/workplace assignments.

The metadata.txt file (see Appendix C) contains information to help you understand the effects of this issue by reporting on schools and workplaces both inside and outside the study area.

As a result of this extraction method, many schools and workplaces may not appear to be filled to capacity.

# Generating Synthesized Households
To generate synthesized households, RTI used a method developed at the Los Alamos National Laboratory for use with the TranSims transportation simulation package. This method selects households from the PUMS data (the 5% sample) to fit marginal distributions of various aggregated census counts by census block group. The statistical method, called Iterative Proportional Fitting, results in household records from the PUMS 5% sample being selected and replicated so that a complete 100% household dataset is derived for each census block group. A complete description of the TranSims population generator algorithms can be found in an article by Beckman, Baggerly, and McKay (1996).

Four matching variables are used to select households from the PUMS data to match aggregated counts at the block group level. The synthetic population generator attempts to select households from the PUMS data so that the count of households in each of four categories (i.e., age of the head of household, household income, household size, and race of head of households), in each block group, equal the count of households for these same categories that are estimated in the ACS data.

The Census Bureau weights its ACS estimates of households by household size according to housing units, but does not control household size counts in other household characteristics estimates. Therefore, we used the 2010 Decennial Census counts of households by household size by census block group (which are assumed to be the most accurate data on this subject) as the baseline households by household size measure. We then adjusted the ACS estimates in the three other household input files mentioned above.

As an example, census block group 370010201002 contains counts of households by household size from the 2010 Decennial Census and 2007-2011 ACS as shown in Table 2.

**Table 2. Differences in household size estimates.**
|Bin (size)|2010 Census|2007-2011 ACS|
| :-----------| :-----------| :-----------|
|1|186|229|
|2|210|258|
|3|68|83|
|4|65|80|
|5|19|23|
|6|5|6|
|7+|1|1|
|Total|554|683|


