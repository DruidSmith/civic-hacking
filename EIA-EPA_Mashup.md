## Collection of Energy Mashup Tips

Suggestions for mashing up Department of Energy data (EIA-860 Power Generation) with EPA data from EPA websites and APIs.

### Starting point:  How to get to EPA facility data using a Department of Energy ORIS ID

EPA integrates EIA-860 power plant data in its [Facility Registry Service (FRS)](http://epa.gov/frs) on an annual basis.  As such, the EIA-860 ORIS identifiers are available there.  FRS integrates facility data across 90 different datasets to provide a means of linking and crosswalking these datasets.  This can typically be done via the EPA Registry ID.

### FRS Facility Lookup REST Service

FRS has a [Facility Lookup REST Service](http://www.epa.gov/enviro/html/fii/FRS_REST_Services.html) which can be queried using program IDs.  

### Basic Example

Example:  The Keystone Power Plant in Shelocta, PA has an EIA-860 ORIS ID of 3136.
This can be queried via the FRS Facility Lookup Service as follows (simplest example, with defaults:

[http://ofmpub.epa.gov/enviro/frs_rest_services.get_facilities?pgm_sys_acrnm=EIA-860&pgm_sys_id=3136](http://ofmpub.epa.gov/enviro/frs_rest_services.get_facilities?pgm_sys_acrnm=EIA-860&pgm_sys_id=3136)

Deconstructing this call, the key elements and parameters are
- endpoint: http://ofmpub.epa.gov/enviro/frs_rest_services.get_facilities
- Program System Acronym is 'EIA-860': pgm_sys_acrnm=EIA-860
- Program System ID is '3136': pgm_sys_id=3136

The default response type is XML

### Useful Parameters

To specify JSON or JSONP, append these as an output parameter, example:

http://ofmpub.epa.gov/enviro/frs_rest_services.get_facilities?pgm_sys_acrnm=EIA-860&pgm_sys_id=3136&output=JSON

To request additional EPA program outputs, add 'program_output=yes' as a parameter, example:

[http://ofmpub.epa.gov/enviro/frs_rest_services.get_facilities?pgm_sys_acrnm=EIA-860&pgm_sys_id=3136&program_output=yes&output=JSON](http://ofmpub.epa.gov/enviro/frs_rest_services.get_facilities?pgm_sys_acrnm=EIA-860&pgm_sys_id=3136&program_output=yes&output=JSON)

Program output may be useful for accessing some reports and data, for example accessing EPA E-GGRT greenhouse gas data.  This will be shown in more detail below.

### Useful Outputs

Note that the service returns many core elements that may be useful in applications, for example latitude and longitude:

> "Latitude83":"40.659509",
"Longitude83":"-79.337818"

These can be useful for displaying a simple map, for example using [Leaflet.js](http://leafletjs.com/).

However, the one that can be very powerful in terms of mashups and unlocking a lot of additional data is the FRS Registry ID

> "RegistryId":"110000538525",

### Using the Registry ID to access an FRS Facility Detail Report

This Registry ID can be used to retrieve a number of EPA reports by simply plugging in the ID into the URL, for example an FRS Facility Detail Report:

http://iaspub.epa.gov/enviro/fii_query_detail.disp_program_facility?p_registry_id=110000538525

### EPA ECHO Enforcement and Compliance Report

http://echo.epa.gov/detailed_facility_report?fid=110000538525

### EPA Envirofacts Detailed Report

http://oaspub.epa.gov/enviro/multisys2_v2.get_list?facility_uin=110000538525

### Greenhouse Gas Report

For some EPA reports, a program ID may be needed, for example, to retrieve information from EPA's Greenhouse Gas reporting program, the E-GGRT ID is needed.

> "ProgramSystemAcronym":"E-GGRT",
"ProgramSystemId":"1000883",
"ProgramFacilityName":"KEYSTONE"

http://ghgdata.epa.gov/ghgp/service/html/2012?id=1000883

This call will retrieve a snippet of HTML containing detailed information about greenhouse gas emissions for this plant

### Accessing Data via Envirofacts REST API

EPA's Envirofacts data warehouse additionally contains significant data resources, which can be accessed via a [REST API](http://www.epa.gov/enviro/facts/services.html)

This Envirofacts REST API utilizes canonic calls which can access data by specifying the table of interest and parameters for retrieval, based on the [Envirofacts Data Model](http://www.epa.gov/enviro/facts/efovw.html)

In a similar manner to the reports above, the facility identifiers can be used to unlock data from the Envirofacts REST API.
