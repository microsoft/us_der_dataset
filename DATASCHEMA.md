## Data Schema: Utility Solar
For more information see the Berkeley Lab’s [Utility-Scale Solar dataset](https://emp.lbl.gov/utility-scale-solar) and the [EIA Form 860](https://www.eia.gov/electricity/data/eia860/). The primary source of information was the Berkeley Lab's dataset. This information was cross-referenced with the entries in Form 860 to find the voltage level at the interconnection point, to identify the distribution-level resources which are included in this dataset.
Data field name | Description | Data type, units, options
--- | --- | ---
project_name | Project name | String
eia_id | Identification number for EIA Form 860 | Numeric
type | Resource type: this dataset is for utility solar (UPV)  | String
latitude | Geospatial information | Numeric
longitude | Geospatial information | Numeric
region | The resource is located under the geographic purview of the following independent system operator, or other regional regulatory entity | String: {CAISO, ERCOT, HI, ISO-NE, MISO, NYISO, PJM, Southeast (non-ISO),SPP, West (non-ISO)}
state | U.S. State abbreviation | String, two letter abbreviation
state_fips | Federal Information Processing System (FIPS) Codes for state | Two digit numeric code
state_name | U.S. State name | String
year | Year of installation of solar resource | Numeric, year
capacity_DC_kW | Installed DC capacity for the resource | Numeric, kW
capacity_AC_kW | Installed AC capacity for the resource | Numeric, kW
inverter_loading_ratio | Inverter loading ratio for the installation, as a ratio of the DC to AC capacity | Numeric, unitless ratio > 1
mount_type | Type of mounting for the solar installation | String: {Fixed tilt, Tracking, Combo}
tracking_type | Method to track the sun throughout the day | String: {Fixed, Single, Double, Dual-axis}
tilt | Tilt angle, vertical angle measured from the ground | Numeric, degrees
azimuth | Azimuth angle, horizontal orientation | Numeric, degrees
average_global_horizontal_irradiance | Average shortwave solar radiation received by a surface horizontal to the ground, often abbreviated as GHI | Numeric
capacity_factor_average | Average capacity factor of the solar resource, where capacity factor is the ratio of the electrical energy produced by the solar generator to the electrical energy potential if operated at full power (i.e. nameplate capacity for a solar resource), over a duration of time | Numeric, unitless ratio between [0,1]
tech_class_primary | Primary solar technology class denoted by abbreviation | String: {Concentrated solar power (CSP), photovoltaic (PV)}
tech_class_secondary | Secondary solar technology class | Vector of strings: {c-Si, CPV, Thin-film, Tower, Trough}
storage_flag | Boolean flag indicating whether a storage resource is colocated with the solar resource | Boolean: {True, False}
storage_year | Year of installation of the storage resouce; has value -1 if not applicable | Numeric
storage_capacity | Power rating of the storage resource; has value -1 if not applicable | Numeric, MW
storage_energy | Energy rating of the storage resource; has value -1 if not applicable | Numeric, MWh
storage_tech | Technology type for the storage resource | String: {Lead acid, Lithium Iron Phosphate, Lithium-Ion (LIB), Molten salt}
hybrid_flag | Boolean flag indicating whether the solar resource is a hybrid resource with other generating technology, including other solar generating technology (ex. a colocated CSP and PV plant) | Boolean: {True, False}
hybrid_tech | Technology type of the hybrid generating resource | String: {PV, CSP, Fossil, Geothermal, Wind}
duplicate | Boolean flag indicating whether the entry is a duplicate entry based on EIA IDs | Boolean: {True, False}
sub_id | ID of the substation the resource is connected to, with IDs indicating the substation in the BES grid model | Numeric
interconnect_x | Resource is connected to one of three U.S. grid interconnections | String: {Eastern, ERCOT, Texas}
point_of_interconnect | Point of interconnection to the transmission or distribution system, as determined by the voltage level at interconnection point | String: {distribution-primary, distribution-secondary}
interconnect_y | Duplicate entry to interconnect_x | String: {Eastern, ERCOT, Texas}



## Data Schema: Distributed Small-scale Solar
For more information see the Berkeley Lab’s [Tracking the Sun dataset](https://emp.lbl.gov/tracking-the-sun), which was the primary source of information. Significant additional processing was done to determine geospatial information (zipcode and latitude-longitude coordinates) by constructing the zip-to-latlong lookup table. This table is also included in the data repository, and can be used to map additional resources to lat-long coordinates. 
Data field name | Description | Data type, units, options
--- | --- | ---
ID_1 | Resource ID from first data provider in original LBNL dataset, retained for compatibility | 
ID_2 | Resource ID from second data provider in original LBNL dataset, retained for compatibility | 
customer_class | Description of customer class of resource owner, denoted by abbreviation | String: {Residential (RES), Commercial (COM), School (SCHOOL), Government (GOV), Non-profit (NON-PROFIT), Unknown non-residential (NON-RES)}
zipcode | Zipcode of the solar resource | Numeric
city | City of the solar resource | String
state | U.S. State abbreviation | String, two letter abbreviation
state_fips | Federal Information Processing System (FIPS) Codes for state | Two digit numeric code
state_name | U.S. State name | String
utility_service_territory | Electric utility service territory | String
third_party_owned_flag | Boolean flag indicating whether the resource is owned by an entity other than the host entity (of the physical installation) | Boolean: {True, False}
year | Year of installation of solar resource | Numeric, year
month | Month of installation of solar resource | Numeric, month 1 thru 12
day | Date of installation of solar resource | Numeric, day 1 thru 31
capacity_DC_kW | Installed DC capacity for the resource | Numeric, kW
ground_mount_flag | Boolean flag indicating whether the resource is ground mounted or not | Boolean: {True, False}
tracking_type |  | 
azimuth_1 | Azimuth angle, horizontal orientation; 180 degrees is south facing resource (resource may have up to 3 reported orientations) | Numeric, degrees
azimuth_2 | Azimuth angle, horizontal orientation; 180 degrees is south facing resource (resource may have up to 3 reported orientations) | Numeric, degrees
azimuth_3 | Azimuth angle, horizontal orientation; 180 degrees is south facing resource (resource may have up to 3 reported orientations) | Numeric, degrees
tilt_1 | Tilt angle, vertical angle measured from the ground; i.e. zero degrees indicates a flat orientation  (resource may have up to 3 reported orientations) | Numeric, degrees
tilt_2 | Tilt angle, vertical angle measured from the ground; i.e. zero degrees indicates a flat orientation  (resource may have up to 3 reported orientations)| Numeric, degrees
tilt_3 | Tilt angle, vertical angle measured from the ground; i.e. zero degrees indicates a flat orientation (resource may have up to 3 reported orientations)| Numeric, degrees
capacity_mod_1 | Capacity of the installed resource for module 1 (resource may have up to 3 reported modules) | Numeric, kW
capacity_mod_2 | Capacity of the installed resource for module 2 (resource may have up to 3 reported modules) | Numeric, kW
capacity_mod_3 | Capacity of the installed resource for module 3 (resource may have up to 3 reported modules) | Numeric, kW
efficiency_1 | Energy conversion efficiency of module 1 (resource may have up to 3 reported modules) | Numeric, percentage
efficiency_2 | Energy conversion efficiency of module 1 (resource may have up to 3 reported modules) | Numeric, percentage
efficiency_3 | Energy conversion efficiency of module 1 (resource may have up to 3 reported modules) | Numeric, percentage
tech_class_primary | Technology type of module 1 (resource may have up to 3 reported modules) | String
tech_class_primary_2 | Technology type of module 2 (resource may have up to 3 reported modules) | String
tech_class_primary_3 | Technology type of module 3 (resource may have up to 3 reported modules) | String
storage_flag | Boolean flag indicating whether a storage resource is colocated with the solar resource | Boolean: {True, False}
storage_info | Additional information regarding the storage unit | 
storage_year | Year of installation of the storage resouce; has value -1 if not applicable | Numeric
storage_capacity | Power rating of the storage resource; has value -1 if not applicable | Numeric, MW
storage_energy | Energy rating of the storage resource; has value -1 if not applicable | Numeric, MWh
inverter_loading_ratio | Inverter loading ratio for the installation, as a ratio of the DC to AC capacity | Numeric, unitless ratio > 1
inverter_capacity_1 | Power capacity of the inverter | Numeric
inverter_capacity_2 | Power capacity of the inverter | Numeric
inverter_capacity_3 | Power capacity of the inverter | Numeric
inverter_micro_flag_1 | Boolean flag indicating whether the inverter is identified as a micro-inverter | Boolean: {True, False}
inverter_micro_flag_2 | Boolean flag indicating whether the inverter is identified as a micro-inverter | Boolean: {True, False}
inverter_micro_flag_3 | Boolean flag indicating whether the inverter is identified as a micro-inverter | Boolean: {True, False}
inverter_hybrid_flag_1 | Boolean flag indicating whether the inverter is shared by the solar and storage unit | Boolean: {True, False}
inverter_hybrid_flag_2 | Boolean flag indicating whether the inverter is shared by the solar and storage unit | Boolean: {True, False}
inverter_hybrid_flag_3 | Boolean flag indicating whether the inverter is shared by the solar and storage unit | Boolean: {True, False}
inverter_meter_flag_1 | Boolean flag indicating whether the inverter has a built in meter (ex. for net metering applications) | Boolean: {True, False}
inverter_meter_flag_2 | Boolean flag indicating whether the inverter has a built in meter (ex. for net metering applications) | Boolean: {True, False}
inverter_meter_flag_3 | Boolean flag indicating whether the inverter has a built in meter (ex. for net metering applications) | Boolean: {True, False}
zip_original | Duplicate entry to zipcode | Numeric
zip | Duplicate entry to zipcode, unless additional data processing and cleaning is required to update zipcode information | Numeric
latitude | Geospatial information, typically not provided in the original dataset; approximated by provided geospatial information (zipcode, city) and using zipcode to lat/long lookup table | Numeric
longitude | Geospatial information, typically not provided in the original dataset; approximated by provided geospatial information (zipcode, city) and using zipcode to lat/long lookup table  | Numeric
zip_city | Zipcode of the city, used when zipcode information is not provided in original dataset | Numeric
sub_id | ID of the substation the resource is connected to, with IDs indicating the substation in the BES grid model | Numeric
interconnect | Resource is connected to one of three U.S. grid interconnections | String: {Eastern, ERCOT, Texas}

## Data Schema: Storage
For more information see the [EIA Energy Atlas storage dataset](https://atlas.eia.gov/datasets/eia::battery-storage/about). 
Data field name | Description | Data type, units, options
--- | --- | ---
name | Project name | 
eia_id | Identificaiton number for EIA Form 860 | 
source | Indicates the source information from EIA dataset | String: {batteries}
sector | Sector of owenrship categorized | String: {Utility, Independent power producer (IPP), Commercial, Industrial}
chp | Boolean flag indicating whether the resource is part of a combined heat and power | Boolean: {True, False}
latitude | Geospatial information | Numeric
longitude | Geospatial information | Numeric
fips | Federal Information Processing System (FIPS) Codes for state | Two digit numeric code
state | U.S. State name | String
state_abbr | U.S. State abbreviation | String, two letter abbreviation
zip | Zipcode of the storage resource | Numeric
capacity | Power rating of the storage resource | Numeric, MW
collocated_with_solar | Boolean flag indicating whether the storage resource is colocated with solar | Boolean: {True, False} 
solar_mw | Nameplate capacity of the solar resource (if applicable) | Numeric, MW
period |  | 
sub_id | ID of the substation the resource is connected to, with IDs indicating the substation in the BES grid model | Numeric
interconnect | Resource is connected to one of three U.S. grid interconnections | String: {Eastern, ERCOT, Texas}
