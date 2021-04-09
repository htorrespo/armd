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

JOB - for specifying overall JOB control options (all stages); 

UPPERAIR -   for processing NWS UPPER AIR data (Stages 1 and 2); 

SURFACE -    for processing NWS hourly SURFACE data (Stages 1 and 2); 

ONSITE - for processing ONSITE meteorological data (Stages 1 and 2);

MERGE - to MERGE the three data types into one file, including 1-minute 
ASOS wind data, if available (Stage 2); 

METPREP -   for METeorological data PREParation for use in a 
dispersion Model (Stage 3). 



