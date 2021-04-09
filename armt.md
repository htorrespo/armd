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
quotes (“) as field delimiters for filenames is allowed to support 
filenames with embedded spaces

### Description of Job Pathway Keywords


__JOB___. `Optional, Non-repeatable`.  Start of JOB pathway.  This statement is optional if the statements associated with this block appear first in the input control file.

___CHK_SYNTAX___. _Optional, Non-repeatable_.  Flag indicating that only the syntax of the input statements should be checked for errors, i.e., no data are processed.

___MESSAGES___. _Mandatory, Non-repeatable_.  Identifies the warning/error messages file.

___REPORT___. _Optional, Non-repeatable_.  Identifies the general report file.

