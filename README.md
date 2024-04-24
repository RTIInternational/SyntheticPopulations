# SyntheticPopulations
RTI Synthetic Population Data (README)

U.S. Synthetic Population
2010 Version 1.0
Quick Start Guide (README)
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

Wheaton, W.D.. Rineer, J.I.. (May, 2014, Apr, 2024) 2010 U.S. Synthetic Population Ver. 1. RTI International. Retrieved from [https://github.com/RTIInternational/SyntheticPopulations](https://github.com/RTIInternational/SyntheticPopulations)

This Quick Start guide should be cited as:
Wheaton, W.D. 2014.. Rineer, J.I.. (May, 2014, Apr, 2024) “U.S. Synthetic Population Database 2010: Quick Start Guide (README)”. RTI International. Retrieved from [RTI Synthetic Population Data (README)](https://github.com/RTIInternational/SyntheticPopulations/edit/main/README.md)

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
|**Total**|554|683|

We use the 2010 Decennial Census households by household size counts as the input for the population generator. Since the 2007-2011 ACS estimates 683 households in that census block group we proportionally adjust the counts of households in each bin for household race, householder age, and household income so the final estimates total the 2010 Decennial Census counts of households (554), but maintain the proportion of households in each bin according to the ACS estimates. Tables 2-4 illustrate the adjustment process.

**Table 3. Adjustments to ACS householder race estimates for census block group 370010201002**
|Bin (race)|ACS Estimate|After Adjustment|Proportion Before|Proportion After|Proportional Difference|
| :-----------| :-----------| :-----------| :-----------| :-----------| :-----------|
|White|602|488|88.1|88.1|0|
|Black|63|51|9.2|9.2|0|
|Asian|0|0|0|0|0|
|Other|18|15|2.6|2.7|0.1|
|2+|Races|0|0|0|0|0|
|**Total**|683|554| | | |

**Table 4. Adjustments to ACS household income estimates for census block group 370010201002**
|Bin (race)|ACS Estimate|After Adjustment|Proportion Before|Proportion After|Proportional Difference|
| :-----------| :-----------| :-----------| :-----------| :-----------| :-----------|
|<$10K| 8| 6| 1.2| 1.1| -0.1|
|$10K-$15K|19|15|2.8|2.7|-0.1|
|$15K-$25K| 60| 49| 8.8| 8.8| 0|
|$25K-$35K|56|45|8.2|8.1|-0.1|
|$35K-$50K|114| 92| 16.7| 16.6| -0.1|
|$50K-$100K|322|261|47.1|47.1|0|
|>$100K| 104| 84| 15.2| 15.2| 0|
|**Total**|683|552 [^1] |100|99.6| |
[^1]: The adjustment process, due to rounding, sometimes results in total counts that are one or two households different than the 2010 Decennial Census counts. In these cases, we add or subtract the difference from the bin containing the largest proportion of households. In the case above, two additional households would be added to the $50K-$100K bin so the total of households equals 554.  

**Table 5. Adjustments to ACS householder age estimates for census block group 370010201002.**
|Bin (race)|ACS Estimate|After Adjustment|Proportion Before|Proportion After|Proportional Difference|
| :-----------| :-----------| :-----------| :-----------| :-----------| :-----------|
|<25 |43 |35 |6.3 |6.3 |0|
|25-34|126|102|18.4|18.4|0| 
|35-44 |103 |84 |15.1 |15.2 |-0.1|
|45-54|179|145|26.2|26.2|0| 
|55-64 |67 |54 |9.8 |9.7 |0.1|
|65-74|71|58|10.4|10.5|-0.1| 
|75+ |94 |76 |13.7 |13.7 |0|
|**Total**|683|554|99.9 |100| |

We refer to the final counts as the ‘adjusted ACS’ counts in the remainder of this document.
These four selection variables and the detailed categories used for matching to the adjusted ACS within each variable are shown in Tables 5 to 8.

**Table 6. Household Income Categories**
|Synthetic Population Category|Range|ACS Source Fields (sequence 53)|
| :-----------| :-----------| :-----------|
|1 |<$10,000 |B19001_002|
|2|$10,000–$15,000|B19001_003 |
|3 |$15,001–$25,000 |B19001_004 + b19001_005|
|4|$25,001-$35,000|B19001_006 + b19001_007 |
|5 |$35,001–$50,000 |B19001_008 + b19001_009 + b19001_010|
|6|$50,001–$100,000|B19001_011 + b19001_012 + b19001_013 7 >$100,000 B19001_014 + b19001_015 + b19001_016 + b19001_017|

**Table 7. Head-of-Household Age Categories.**
|Synthetic Population Category|Range|ACS Source Fields (sequence 96)|
| :-----------| :-----------| :-----------|
|1 |15–24 |B25007_003 + b25007_013|
|2|25–34|B25007_004 + b25007_014 3 35–44 B25007_005 + b25007_15|
|4|45–54|B25007_006 + b25007_016 5 55–64 B25007_007 + b25007_017 + b25007_008 + b25007_018|
|6|65–74|B25007_009 + b25007_019 7 >74 B25007_010 + b25007_011 + b25007_020 + b2500_021|

**Table 8. Household Size Categories.**
|Synthetic Population Category|Range|ACS Source Fields (sequence 33)|
| :-----------| :-----------| :-----------|
|1 |15–24 |B25007_003 + b25007_013|
|2|25–34|B25007_004 + b25007_014 3 35–44 B25007_005 + b25007_15|
|4|45–54|B25007_006 + b25007_016 5 55–64 B25007_007 + b25007_017 + b25007_008 + b25007_018|
|6|65–74||B25007_009 + b25007_019 7 >74 B25007_010 + b25007_011 + b25007_020 + b2500_021|

**Table 9. Head-of-Household Race Categories.**
|Synthetic Population Category|Values|ACS Source Fields (sequence 33)|
| :-----------| :-----------| :-----------|
|1 |White alone |B11001a_001|
|2|Black or African American alone|B11001b_001|
|3 |Asian alone |B11001d_001|
|4|Other|B11001c_001 + b11001e_001 + b11001f_001 5 Two or more races B11001q_001|

# Group Quarters and Group Quarters Residents
People who reside in group quarters (e.g., nursing homes, prisons, military barracks, college dormitories) accounted for 2.7% of the U.S. population in the 2007–2011 ACS. Because of their close living situations and frequent contact, residents of group quarters may be disproportionately important to infectious disease modeling.

Because the generic population generator provided by TranSims does not produce synthesized group quarters residents, RTI developed modules to generate locations for group quarters and synthesize persons who live in them.

Due to differences in how these group quarters are generated and because the synthesized group quarters residents do not exist in the PUMS data, these entities are provided in two separate files (i.e., the [prefix]_synth_gq.txt file and the [prefix]_synth_gq_people.txt file) instead of being incorporated directly into the household file and the persons file.

Group Quarters facility locations are derived first by using existing sources of locations from the HSIP Freedom database. Additional facilities are created (at block group centroids) in block groups when SF1 data indicates that there are group quarters residents in places where HSIP Freedom does not indicate group quarters facilities exist OR when group quarters sub-populations exist that logically would be housed in different facilities (for example, presence of juvenile prisoners and adult prisoners in a block group having only a single prison).

The following table provides a summary of the counts of group quarters facilities and of the count of synthetic persons created for them.

**Table 10. Group Quarters Facilities and Counts.**
|Type |Number of Facilities |Number of People|
| :-----------| :-----------| :-----------|
|Nursing Home |23,760 |1,502,264|
|Prison|19,786|2,429,326 |
|Military Base |307 |337,529|
|University|4,559|2,523,971|

After group quarters facilities are selected or generated, census SF1 data on counts of group quarters residents by type of facility, age groups, and gender are used to create the synthetic residents housed in each facility. More specific age distribution data noted below were used to supplement SF1. Data sources used to generate the group quarters data include:

**Table 11. Group Quarters data sources.**
|Type |Source for Age Distributions |Source for Facility Size|
| :-----------| :-----------| :-----------|
|Nursing Homes |CDC NCHIS Demographics |CDC Census of Nursing Home Statistics 2010|
|Prisons|DOJ Bureau of Justice Statistics|ESRI Business Analyst|
|Military Bases |Dept of Defense Selected Manpower Statistics Fiscal Year 2005 (most recent) |American Community Survey count of persons in military group quarters by block group.|
|Universities|American Community Survey PUMS data aggregated at the national level|ESRI Business Analyst|

The end result of the Group Quarters data development process is two files; one containing a list of facility locations, types, and capacities; the other containing a list of residents by age and gender for each facility.

# School Assignments
Synthetic persons who, according to PUMS attend primary or secondary schools, are assigned to actual schools based on school/grade capacity.

The basic assignment methodology is to process each synthetic person age 18 or less by examining his or her PUMS school enrollment code (SCH) and school grade level attending (SCHG) and, for those who attend school, assign each one to the closest school that services that grade level. Since the schools database being used contains both public and private schools and the synthetic persons have coding to determine which students attend public or private schools, the assignments for these two types of schools are handled independently.

If the student goes to a private school, then he or she is enrolled in the closest private school less than 50 kilometers (approximately 31 miles) away that has capacity for the student’s given grade category. If there are no private schools within 50 kilometers that have capacity, then the student is assigned to the closest private school servicing the students’ grade category (even if already full).

For students attending a public school, the assignment method, is as follows:
- Find the closest three schools,
 * For regular and magnet schools, the school must be within 50 kilometers of the student, in the same county, and have enrollment for the appropriate grade category.
 * For charter schools, the school must be within 50 kilometers of the student, in the same state, and have enrollment for the appropriate grade category.
- Assign the student to the school (from the set found above) that has the smallest ratio of currently enrolled students to grade range capacity. In other words, try to fill schools that are less full first.
- If all schools in the selected set are filled to capacity, continue to overfill using the same logic as above. The schools with the largest capacities will receive the most “extra” students.
- If no schools exist in the county (within 50 kilometers), then relax the criteria to include any schools in the state that are within 50 kilometers and repeat all the above steps.

School assignment data sources include:
- School locations: HSIP Freedom 2011.
- Enrollment data: National Center for Educational Statistics (NCES)
- School attendance status and grade: PUMS SCH and SCHG variables. The SCH variable contains data on school enrollment. SCH codes are:

**Table 12. PUMS SCH codes.**
|Code |Description |
| :-----------| :-----------|
|B |N/A (less than 3 years old)|
|1 |No, has not attended in the last 3 months |
|2 |Yes, public school or public college|
|3 |Yes, private school or private college|

The SCHG variable contains data on school grade level for those attending school. The SCHG codes are:

**Table 13. PUMS SCHG codes.**
|Code |Description |
| :-----------| :-----------|
|B |N/A (not attending school)|
|1|Nursery school/preschool| 
|2 |Kindergarten|
|3|Grade 1 to 4|
|4|Grade 5 to 8|
|5|Grade 9 to 12|
|6 |College undergraduate|
|7|Graduate or professional school|
  
