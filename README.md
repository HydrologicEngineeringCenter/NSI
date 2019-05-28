**National Structure Inventory (NSI)**

March 2019




# Contents

[1. Mission Vision and Goals](#mission)

[2. Purpose](#purpose)

[3. Overview of the National Structure Inventory](#overview-of-the-national-structure-inventory)

[4. NSI Fields](#nsi-fields)

[5. USACE-Developed NSI Base Data](#usace-developed-nsi-base-data)

[6. 2019 Base Quality Level Data Generation](#base-quality-level-data-generation)

[7. Acronyms 8](#acronyms)

**National Structure Inventory (NSI)**

# Mission
Provide access to point based structure inventories with attribution to support evaluation of consequences from natural and man made hazards. 

# Vision
To support all federal agencies interested in collaborating on structure inventory data

# Goals
1. Provide access to the data to as many people and agencies as possible.
2. Improve the quality of the data.
3. Improve the ability for the U.S. to respond to disasters.
4. Improve the ability for the U.S. to plan for future disasters.



**Overview**

# Purpose

The National Structure Inventory (NSI) is a system of databases
containing structure inventories of varying quality and spatial
coverage. The purpose of the NSI databases is to facilitate storage and
sharing of point based structure inventories used in the assessment and
analysis of natural hazards. Flood damage analysis is the primary usage,
but sufficient data exists on each structure to compute damages due to
other hazard types. The purpose of this document is to describe the NSI
data structure and to document the processes utilized to produce the
2019 NSI base data.

# Overview of the National Structure Inventory

The structure inventory databases contained in the NSI are arranged by
the quality level of the data in the structure inventory. There are two
quality level categories: Base and High. The Base quality level contains
the National Structure Inventory Base layer created by the U. S. Army
Corps of Engineers (USACE). The USACE Base data layer was created to
simplify the GIS pre-processing workflow for the USACE Modeling Mapping
and Consequence center. The NSI is a repository of point structure
inventories with a structured RESTful API service, and each inventory
within the database contains a series of required attributes or fields
that describe each point in the inventory. Section 3 provides a detailed
list of the fields required for structure inventories to be contained in
the NSI repository.

**NSI Data Quality Levels**

There are potentially two NSI data quality levels for a given geographic
location. The Base quality data is available for the contiguous United
States as well as Hawaii and Alaska, while High quality data
availability will vary subject to where more detailed inventories have
been created and uploaded.

<table>
<thead>
<tr class="header">
<th><span class="underline">Base</span></th>
<th>The Base data supports performing portfolio-level decisions across the entire nation. Portfolio-level decisions require the Base data to have internal consistency and universal coverage. The NSI Base level also provides a basis from which more detailed inventories can be created by users. Base data has quality issues, but provides a consistent dataset characterized by nationally appropriate data sources and assumptions. For regional analyses, users should review the Base data for quality assurance prior to use. The USACE created the National Structure Inventory Base data layer, which provides data for the entire contiguous United States, plus Alaska and Hawaii. Section 4 describes the processes used to construct the NSI Base data from numerous nationwide datasets. In addition, Section 4 serves as the metadata for the Base quality data.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><span class="underline">High</span></td>
<td>The data in this quality level represent high resolution datasets such as user formatted parcel data and/or ground surveys. The data contained in the High quality level is appropriate in situations where consequences are driving decision-making, and the alternatives under consideration have high costs. Eventually qualified users will be able to upload High quality datasets with metadata documentation of the processes used to generate the datasets. This is a future feature, however, and there is currently no functionality in the NSI databases to upload or edit structure inventory data.</td>
</tr>
</tbody>
</table>

Disclaimer: It is up to the individual downloading data from the NSI to
review the metadata and assess whether the methodologies are consistent
with their needs.

# NSI Fields

The NSI application programming interface (API) requires structure
inventory attributes to be consistent across all datasets in the NSI
databases. These required attributes exist to meet the computational
constraints of the software using the NSI. To successfully upload
datasets to the NSI, the datasets must contain the required attributes –
with the fields populated whenever applicable. The analyst is
responsible for giving approximate values for each attribute, and
documenting the assumptions in providing those attributes. The full list
of fields for the NSI are:

![](media/image2.png)

# USACE-Developed NSI Base Data

This section of the document serves as the metadata for the NSI Base
data provided by USACE. The development team converted parcel data
available through CoreLogic, business location data available through
Esri/Infogroup, and HAZUS based previous versions of the NSI where those
datasets were unavailable. This Base quality data is not an exact
representation of reality, but rather contains many county-level,
state-level, or regional assumptions applied to individual structures,
often by random assignment. As such while county or other large
aggregations of structures will ideally be accurate *on average,*
individual structure characteristics may not be accurate. Although these
and other accuracy issues exist, the Base dataset functions as an
available common and consistent standard for the United States.
Appropriate uses include as a foundation on which to develop more
detailed and locally accurate inventories, use with necessary “ground
truthing”, situations where more accurate data is too costly to produce
and cannot be created, or when limited by time constraints. Another
general use of the NSI Base dataset is for assessments on a national
level, where inconsistent application or availability of regional
assumptions may introduce bias into the analysis.

The following sections describe the processes used to produce the NSI
Base data.

## 2019 Base Quality Level Data Generation

In 2018 and 2019 the NSI team created the data using the following
inputs from numerous input data sources. The two main sources of data
are CoreLogic parcel files for residential structures and ESRI business
layer for non-residential structures. Each data file used contains data
on the type of development that exists at a given location. For example,
the parcel data often stated whether a structure was Single Family
Residential or a multi-family structure; ESRI data reported the NAICS
code for each structure. These source data categories were converted to
a format consistent with one of 40 different HAZUS Occupancy Type
classification. Residential Occupancy types are further revised later in
the process based on other structure characteristic assignment, with
single family residences’ “RES1” classification being appended with the
number of stories and basement status (e.g. “RES1-2SNB”).

## Main Data Sources

<table>
<thead>
<tr class="header">
<th><strong>Source</strong></th>
<th><strong>Database</strong></th>
<th><strong>Dataset</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>HAZUS</strong></td>
<td>Bndrygbs.mdb</td>
<td>hzMeansCountyLocations</td>
<td>Provides county level price adjustments.</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>hzExposureOccupB</td>
<td>Informs estimated dollar per square foot used in structure valuation.</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>hzCensusBlock</td>
<td>Provides the structure building schemes and block type.</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>flSchemeCoastal, flSchemeRiverine, flSchemeGLakes</td>
<td>Provides information on foundation type and height.</td>
</tr>
<tr class="odd">
<td></td>
<td>MSH.mdb</td>
<td>flGenBldgScheme</td>
<td>Provides the construction type distributions and NFIP entry year for structures.</td>
</tr>
<tr class="even">
<td><strong>USACE</strong></td>
<td>NSI 2015</td>
<td>Base layer</td>
<td>Used in any Census Block that lacks ESRI or CoreLogic data.</td>
</tr>
<tr class="odd">
<td><strong>Homeland Infrastructure Foundation-Level Data</strong></td>
<td>CoreLogic</td>
<td>County Level Data</td>
<td>Parcel polygons and associated data tables; used for initial spatial location and Occupancy Type.</td>
</tr>
<tr class="even">
<td><strong>Esri</strong></td>
<td>Business Layer</td>
<td>InfoGroup</td>
<td>Provides initial structure location; NAICS code informs occupancy type, number of employee field informs square footage estimate and population weighting.</td>
</tr>
<tr class="odd">
<td><strong>Microsoft</strong></td>
<td>Building Footprints</td>
<td>State level polygons</td>
<td>Paired with parcel polygons to improve structure location and to inform structure aggregation.</td>
</tr>
<tr class="even">
<td><strong>U. S. Census Bureau</strong></td>
<td>American Community Survey</td>
<td>Population, Demographics</td>
<td>Informs population growth estimates, disability rates, and age distribution.</td>
</tr>
<tr class="odd">
<td></td>
<td>Characteristics of New Housing</td>
<td>Annual, Various</td>
<td>Provide structure characteristic data such as number of stories and square feet.</td>
</tr>
<tr class="even">
<td></td>
<td>Longitudinal Employer-Household Dynamic Database</td>
<td>Population Data</td>
<td>Contains worker counts by origin and destination census blocks.</td>
</tr>
<tr class="odd">
<td><strong>NCES</strong></td>
<td>Schools Database</td>
<td>School Data</td>
<td>Contains the locations of schools, number of teachers and students per school by census block.</td>
</tr>
<tr class="even">
<td><strong>U. S. Geological Survey</strong></td>
<td>National Elevation Dataset</td>
<td>10 Meter Dataset (?)</td>
<td>Provides raster ground elevation (in feet) data.</td>
</tr>
</tbody>
</table>

## Structure Placement Refinement

The XY location for each structure is initially provided by the source
data, such as the centroid of the parcel or the geo-reference of a
business’s address. However, the NSI Generator modifies these initial
locations by matching the structures to Microsoft buildings footprints
within the same parcel polygon. If there are multiple footprints within
a parcel polygon, structures are placed in the largest footprints first.
If there are multiple structures types within a parcel polygon, then
structures are paired with footprints in the following order: schools
first, then commercial structures, and finally residential structures.
Structures are placed in unpaired footprints until all footprints are
paired with structures, at which point multiple structures of the same
type may be stacked within the same footprint.

## Structure Aggregation

If structures are stacked within the same location, then the structures
may be partially or completely merged together. Residential units
stacked at the same location are assumed to be multi-family structures;
the number of units will be used later to update the occupancy type of
the structure (for instance, more than 50 units would mean that a
residential structure would be identified as a RES3F). However,
commercial structures are not completely merged; instead, the NSI
generator links the stacked structures so that they share certain
characteristics such as number of stories and construction material.
Each commercial business within the stack will receive a weighted
portion of the square footage which informs the valuation of each
structure.

## Population Growth and Assignment to Structures

County level population estimates were available for 2017, however the
most recent block level residential population estimates are from the
2010 Decennial Census. To account for this difference, the NSI Generator
was provided a table that recorded the number of increased persons
residing in a county above 2010 population levels (counties that lost
population received no adjustment). The NSI estimates block level
population growth in an iterative process until the total increased
population for the county is depleted. Population is first added to
structures that had no housing units in 2010 but now have housing units
in the newly generated inventory. Next population is distributed to
blocks whose number of housing units is greater in the NSI than it was
in the 2010 census. Finally, population is randomly assigned to census
blocks until the population growth is fully distributed.

Commercial worker population was derived from the U. S. Census Bureau’s
Longitudinal Employer-Household Dynamics (LEHD) database (website:
<https://lehd.ces.census.gov/>). This database contains counts for the
number of residents leaving a census block to work and the number of
workers arriving in a census block. Departing workers are subtracted
from the residential population; as are enrolled students.

Once block level population estimates are made, population is assigned
to particular structures within the block. Population is assigned from 8
separate pools, reflecting combinations of Day and Night, Over and Under
65 years of age, and Workers and Residents. Population is assigned from
commercial population pools to commercial businesses weighted by number
of employees, and from residential population pools to residences
weighted by number of housing units. The assignment process also
accounts for the relative likelihood of those over 65 years of age to
work or stay at home. Schools based on NCES data had student estimates
added directly to those structures in addition to the teachers added
through the worker assignment process.

## Structure Valuation

The HAZUS dataset contains dollars per square foot for each Occupancy
Type; these values are taken from 2014 RS Means estimates, except for
RES1 structures which are taken from 2006 estimates. These values are
indexed to 2018 prices levels using the ENR Construction Cost Index.
Dollars per square foot estimates are then multiplied by the square
footage estimate for each structure to obtain the structure value.

These replacement values for structures are then depreciated in order to
obtain depreciated replacement value; each structure is depreciated by
1% per year for the first 20 years, after which it is assumed that
routine maintenance would keep structure values at 80% of their
replacement values.

Content values are obtained by multiplying structure values against an
occupancy type specific structure to content value ratio. It is
important to note that RES1 structures assumed content values are equal
to structure values; this is because USACE Economic Guidance Memorandum
(EGM) depth damage functions implicitly assume such a relationship. If
NSI users are not relying on the USACE EGM curves, they should instead
assume a 50% relationship unless better data is available to suggest
otherwise.

## Construction Type

The hzCensusBlock table contains an attribute for building scheme, and
this attribute is related to the flGenBldgScheme tables from the MSH.mdb
database. The building scheme attribute is used to define structures as
Wood, Masonry, Concrete Block, Manufactured, and Steel using random
assignment based on the probabilities indicated in the HAZUS table.
Structures that were estimated to be more than 5 stories are assumed to
be of steel construction.

## Foundation Type and Height

Based on the information in the hzCensusBlock table for building scheme
and the tables in the MSH.mdb database that also contain the building
scheme attribute, structures are classified into Slab, Pier, Unattached,
and Basement using random assignment.

Foundation height (in feet) are calculated and provided based on the
foundation type and whether the structures are in blocks that were dated
pre- or post-NFIP.

## Vehicles

Vehicle values for each structure are based on the number of housing
units for residential structures or the number of employees for
commercial structures.

## Ground Elevations

Ground elevations (feet) are determined using the USGS National
Elevation Dataset (NED), based on the structure location (website:
<https://nationalmap.gov/elevation.html>).

# Acronyms

<table>
<thead>
<tr class="header">
<th>API</th>
<th>Application Programming Interface</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>EGM</td>
<td>Economic Guidance Memorandum</td>
</tr>
<tr class="even">
<td>FEMA</td>
<td>Federal Emergency Management Agency, Department of Homeland Security</td>
</tr>
<tr class="odd">
<td>FIPS</td>
<td>Federal Information Processing Standard</td>
</tr>
<tr class="even">
<td>FIRM</td>
<td>Flood Insurance Rate Maps</td>
</tr>
<tr class="odd">
<td>GIS</td>
<td>Geospatial Information Systems</td>
</tr>
<tr class="even">
<td>HAZUS</td>
<td>FEMA’s Hazards of the United States</td>
</tr>
<tr class="odd">
<td>LEHD</td>
<td>U.S. Census Bureau’s Longitudinal Employer-Household Dynamics Database, Department of Commerce</td>
</tr>
<tr class="even">
<td>NED</td>
<td>National Elevation Dataset</td>
</tr>
<tr class="odd">
<td>NFIP</td>
<td>National Flood Insurance Program</td>
</tr>
<tr class="even">
<td>NSI</td>
<td>National Structure Inventory</td>
</tr>
<tr class="odd">
<td>USACE</td>
<td>U. S. Army Corps of Engineers, Department of Defense</td>
</tr>
<tr class="even">
<td>USGS</td>
<td>U. S. Geological Survey, Department of the Interior</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
</tr>
</tbody>
</table>
