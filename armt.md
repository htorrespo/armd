# Procesador AERMET


:camel:
AERMET [Manual de Usuario](https://gaftp.epa.gov/Air/aqmg/SCRAM/models/met/aermet/aermet_userguide.pd)

# Appendix A.Functional keyword/parameter reference

This appendix provides a functional reference for the keywords and parameters 
used by the input control files for AERMET. The keywords are organized 
by functional pathway and within each pathway the order of the keywords 
is alphabetical, excluding the keyword that identifies the start of a 
pathway.  The pathways used by AERMET are as follows, including the 
applicable AERMET processing stages and the in the order in which they 
appear in the tables that follow: 

**JOB** - for specifying overall JOB control options (all stages); 

**UPPERAIR** -   for processing NWS UPPER AIR data (Stages 1 and 2); 

**SURFACE** -    for processing NWS hourly SURFACE data (Stages 1 and 2); 

**ONSITE** - for processing ONSITE meteorological data (Stages 1 and 2);

**MERGE** - to MERGE the three data types into one file, including 1-minute 
ASOS wind data, if available (Stage 2); 

**METPREP** -   for METeorological data PREParation for use in a 
dispersion Model (Stage 3). 

Two types of tables are provided for each pathway.  The first table lists 
all of the keywords for that pathway, identifies each keyword as to its 
type (either mandatory or optional, either repeatable or non-repeatable, 
and if it is reprocessed), and provides a brief description of the 
function of the keyword.  The second type of table, which may take 
up more than one page, describes each parameter in detail. 

The following conventions are used in these tables.  The parameter 
names are intended to be descriptive of the input variable being 
represented.  Square brackets around a parameter indicate that the 
parameter is optional for that keyword.  The default that is used 
when an optional parameter is left blank is explained in the 
discussion for that parameter.

Beginning with version 11059, the maximum record length for the AERMET 
control file input file has been increased from 80 to 132 characters.  
Another important enhancement introduced with version 11059 of AERMET, 
which applies across all pathways, is that the maximum field length 
for filenames has been increased from 48 to 96 and the use of double 
quotes (???) as field delimiters for filenames is allowed to support 
filenames with embedded spaces

### Table A-1. Description of Job Pathway Keywords


**JOB**. `Optional, Non-repeatable`.  

`Optional, Non-repeatable`: Start of JOB pathway.  This statement is optional if the statements associated with this block appear first in the input control file.

**CHK_SYNTAX**. `Optional, Non-repeatable`.  

`Optional, Non-repeatable`: Flag indicating that only the syntax of the input statements should be checked for errors, i.e., no data are processed.

**MESSAGES**. `Mandatory, Non-repeatable`.  

`Mandatory, Non-repeatable`: Identifies the warning/error messages file.

**REPORT**. `Optional, Non-repeatable`.  

`Optional, Non-repeatable`: Identifies the general report file.



### Table A-2. Description of Keyword Parameters for the JOB Pathway

**CHK_SYNTAX** `<none>`

**MESSAGES**  `message_filename`

`message_filename`: The name of the file where all source-code-generated messages are written

**REPORT**  `summary_filename`

`summary_filename`: The name of the file where AERMET writes a summary of all preprocessor activity for the current run





### Table A-3. Description of UPPERAIR Keywords

**UPPERAIR** `Conditional, Non-repeatable` Start of UPPERAIR pathway.

**AUDIT**  `Optional, Repeatable`  Identify variables to be audited.  These are in addition to any automatically audited variables.

**DATA**  `Mandatory, Non-repeatable, Reprocessed`  File name of raw upper air data.

**EXTRACT**   `Mandatory, Non-repeatable`  File name of extracted upper air data. 

**LOCATION**  `Mandatory, Non-repeatable, Reprocessed`  Site ID and location information.  Required only for extractionprocessing.

**MODIFY**   `Optional, Non-repeatable, Reprocessed`   Flag indicating corrections should be made to the sounding data when extracted.  See '5 for a discussion of these corrections 

**NO_MISSING**   `Optional, Repeatable`  Identifies those variables to QA and summarize the messages only; detailed message identifying the violation and date is suppressed 

**QAOUT**   `Mandatory, Non-repeatable`  File name of upper air data for quality assessed output/ merge input

**RANGE**  `Optional, Repeatable, Reprocessed`  Set new upper and lower bounds and missing values for QA of the variable listed

**XDATES**  `Mandatory, Non-repeatable`    Inclusive dates identifying the period of time to extract from the archive data file




### Table A-4. Description of Keyword Parameters for the UPPERAIR Pathway 

**AUDIT**  `uaname1 ... uanameN`  

`uaname1 ... uanameN`: Name(s) of variables that are to be tracked and reported duringquality assessment (as defined in Table B-1 of Appendix B).

**DATA**  `archive_filename`  `file_format` 

`archive_filename`:  The name of the file containing the archive of upper air data.

`file_format`: 6201FB (TD-6201 fixed-length blocks), 6201VB (TD-6201 variable-length blocks), FSL for data retrieved from National Centers for Environmental Information (NCEI) web site. Also available online from the National Oceanic and Atmospheric Administration (NOAA) Earth System Research Laboratory (ESRL) Radiosonde Database at https://ruc.noaa.gov/raobs/

NOTE:  The blocking factor and data type (ASCII or EBCDIC) parameters are no longer supported by AERMET, beginning with version 11059.  The default values for these parameters are 1 for blocking factor and ASCII for data type.  AERMET will issue a warning message if these parameters are included on the DATA keyword. 


**EXTRACT** `extracted_data_filename`

`extracted_data_filename`: Name of the output file for data extracted from an archive data file and the name of the input file for upper air data QA

**LOCATION**  `site_id`    `lat(long)`    `long(lat)`    `[tadjust]`
 
`site_id`: Site identifier for which data are to be processed.

`lat(long)`: Station latitude (or longitude) in decimal degrees with the suffix N for sites north of the equator, S for sites south of the equator (or W for sites west of Greenwich, E for sites east of Greenwich).

`long(lat)`: Station longitude (or latitude) in decimal degrees with the suffix W for sites west of Greenwich, E for sites east of Greenwich (or N for sites north of the equator, S for sites south of the equator). 

`[tadjust]`: An integer used to convert the time reported in the database to local Standard time.  For standard upper-air data reported in Greenwich Mean Time (GMT), the value is the same as the time zone for thestation (e.g., a value of 5 for the Eastern time zone).  

NOTE:  Beginning with version 11059, the optional station elevation parameter is no longer supported on the UPPERAIR pathway.

**MODIFY**   `<none>`

**NO_MISSING**   `uaname1  ...   uanameN`

`uaname1  ...   uanameN`: Suppresses missing data messages for the upper air variables specified, as defined in Appendix B; the number of times the variable is missing is not tallied

***QAOUT*** `qa_output_filename`

`qa_output_filename`: Name of the output file from the QA/input to merge data

**RANGE** `uaname`  `lower_bound`  `<[=]`  `upper_bound`  `missing_indicator`

`uaname`:  Variable name, as defined in Table B-1 

`lower_bound`:  Minimum value of the valid range of values for uaname

`<[=]`:  Exclude (<) or include (<=) the lower and upper bounds (the endpoints) in the QA 

`upper_bound`:  Maximum value of the valid range of values for uaname

`missing_indicator`:  Value to indicate the value is missing

**XDATES**   `YB/MB/DB`  `[TO]`  `YE/ME/DE`

`YB/MB/DB`:  Beginning year, month and day to extract; the slash (/) between each part of the date field is required; there can be no blanks in this parameter 

`[TO]`:  Optional; used to make this record more readable

`YE/ME/DE`:  Ending year, month and day to extract; the slash (/) between each part of the date field is required; there can be no blanks in this parameter





### Table A-5. Description of SURFACE Pathway Keywords






