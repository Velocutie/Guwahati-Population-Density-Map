# Guwahati-Population-Density-Map

````markdown
# 🗺️ Mapping Population Density of Guwahati Using GIS

## 📍 Project Overview

This project maps and analyses the spatial distribution of population density across the **60 wards of Guwahati Municipal Corporation (GMC), Assam, India**.

The project was created using **ArcMap** and uses a **choropleth map** to represent population density spatially.

The main purpose of the project is to understand how population is distributed across Guwahati and identify areas with relatively high and low population densities.

---

## 🎯 Objectives

The main objectives of this project are:

1. To map the 60 administrative wards of Guwahati Municipal Corporation.
2. To associate population data with each ward.
3. To calculate population density for each ward.
4. To create a choropleth map showing spatial variation in population density.
5. To identify areas with relatively high and low population density.
6. To understand how GIS can be used for demographic analysis.

---

# 📍 Study Area

The study area is **Guwahati Municipal Corporation (GMC), Assam, India**.

Guwahati is an important urban centre in Northeast India and is situated along the Brahmaputra River. The city contains a mixture of densely developed urban areas, relatively less-developed areas, hills, water bodies and major transportation corridors.

For this project, the study area is divided into **60 GMC wards**.

---

# 📊 Data Used

## 1. Ward Boundary Data

A GIS layer containing the boundaries of the **60 Guwahati Municipal Corporation wards** was used.

The ward layer contains attributes identifying individual wards, including values such as:

```text
Guwahati (M Corp.) - Ward No.1
Guwahati (M Corp.) - Ward No.2
Guwahati (M Corp.) - Ward No.3
...
Guwahati (M Corp.) - Ward No.60
````

The `sourceward` field was used to identify the individual wards.

---

## 2. Population Data

Population values were entered into the GIS attribute table for each ward.

The population data used in this project are **Census 2011-based population figures**.

Therefore, these values should **not** be interpreted as the current population of Guwahati in 2026.

---

## 3. Ward Area

The area of every ward was calculated using ArcMap after projecting the spatial layer into a projected coordinate system.

The area is expressed in:

```text
km²
```

---

## 4. Population Density

Population density was calculated using population and ward area.

The result is expressed as:

```text
persons per square kilometre (persons/km²)
```

---

# 🛠️ Methodology

The overall workflow followed in this project was:

```text
60-Ward Boundary Data
        ↓
Import into ArcMap
        ↓
Inspect Ward Attributes
        ↓
Add Population Field
        ↓
Enter Ward-wise Population
        ↓
Project Spatial Layer
        ↓
Calculate Ward Area
        ↓
Add Density Field
        ↓
Calculate Population Density
        ↓
Apply Graduated Colours
        ↓
Create Choropleth Map
        ↓
Add Cartographic Elements
        ↓
Export Final Map
```

---

# 1. Importing the Ward Map

The 60-ward GIS boundary layer was added to ArcMap.

### ArcMap workflow

```text
File
→ Add Data
→ Add Data
→ Select Ward Shapefile
→ Add
```

The attribute table was opened to inspect the available fields.

---

# 2. Identifying the Ward Field

The attribute table contained several fields, including identifiers and geographic metadata.

The `sourceward` field contained the ward names.

Examples:

```text
Guwahati (M Corp.) - Ward No.1
Guwahati (M Corp.) - Ward No.2
Guwahati (M Corp.) - Ward No.3
...
Guwahati (M Corp.) - Ward No.60
```

The ward number was used to match demographic information to the correct geographic feature.

---

# 3. Adding the Population Field

A new field named:

```text
Population
```

was created in the attribute table.

### Field properties

```text
Field Name: Population
Field Type: Long Integer
```

### ArcMap workflow

```text
Open Attribute Table
→ Table Options
→ Add Field
→ Field Name: Population
→ Type: Long Integer
→ OK
```

The population of each ward was then entered into the corresponding row.

---

# 4. Projecting the Spatial Layer

The original ward layer used:

```text
GCS WGS 1984
```

This is a geographic coordinate system based on latitude and longitude.

Because accurate area calculations require a suitable projected coordinate system, the layer was projected into:

```text
WGS 1984 UTM Zone 46N
```

This projected coordinate system uses metres.

### ArcMap workflow

```text
ArcToolbox
→ Data Management Tools
→ Projections and Transformations
→ Feature
→ Project
```

### Output coordinate system

```text
WGS 1984 UTM Zone 46N
```

A new projected layer was created instead of modifying the original layer.

---

# 5. Creating the Area Field

A new field was created:

```text
Area_km2
```

### Field properties

```text
Field Name: Area_km2
Field Type: Double
```

### ArcMap workflow

```text
Table Options
→ Add Field
→ Area_km2
→ Double
```

---

# 6. Calculating Ward Area

The area of each ward was calculated using ArcMap's geometry calculator.

### ArcMap workflow

```text
Right-click Area_km2
→ Calculate Geometry
→ Property: Area
→ Units: Square Kilometers
→ OK
```

This generated the area of each of the 60 wards in km².

---

# 7. Creating the Density Field

A new field was created:

```text
Density
```

### Field properties

```text
Field Name: Density
Field Type: Double
```

---

# 8. Calculating Population Density

Population density was calculated using the following formula:

```text
Population Density = Population / Area
```

The ArcMap Field Calculator expression was:

```text
[Population] / [Area_km2]
```

The result represents:

```text
persons/km²
```

### Example

```text
Population = 10,000
Area = 5 km²

Density = 10,000 / 5

Density = 2,000 persons/km²
```

---

# 9. Creating the Choropleth Map

The `Density` field was used to create the choropleth map.

### ArcMap workflow

```text
Layer Properties
→ Symbology
→ Quantities
→ Graduated Colors
```

### Settings

```text
Value: Density
Classes: 5
Classification Method: Natural Breaks (Jenks)
```

The five classes represent different levels of population density.

The colour gradient allows areas with higher population density to be visually distinguished from areas with lower population density.

---

# 10. Classification Method

The **Natural Breaks (Jenks)** classification method was selected because the population-density values vary considerably between wards.

Natural Breaks groups values according to natural differences within the dataset.

This allows the map to display meaningful groups of relatively similar density values.

---

# 11. Choropleth Map

The final choropleth map represents:

```text
Low Population Density
        ↓
Moderate Population Density
        ↓
High Population Density
        ↓
Very High Population Density
```

Each ward is represented by a colour based on its calculated population density.

---

# 12. Map Layout

After completing the choropleth, the map was arranged using:

```text
View
→ Layout View
```

The following cartographic elements were added.

---

## 🏷️ Title

```text
Population Density of Guwahati Municipal Corporation (60 Wards)
```

---

## 📊 Legend

The legend displays the five population-density classes.

Unit:

```text
persons/km²
```

---

## 🧭 North Arrow

A north arrow was added to indicate geographic orientation.

### ArcMap workflow

```text
Insert
→ North Arrow
```

A simple north-arrow style was selected.

---

## 📏 Scale Bar

A scale bar was added to show geographic distance.

### ArcMap workflow

```text
Insert
→ Scale Bar
```

The scale bar was displayed using appropriate distance units.

---

## 📚 Source Information

A source note was added to the map:

```text
Source: Guwahati Municipal Corporation / GMDA;
population data based on Census 2011.
```

---

## 🌐 Coordinate System

The projected coordinate system used for the analysis was:

```text
WGS 1984 UTM Zone 46N
```

---

## 📝 Map Information

The final map includes:

* Title
* 60 ward boundaries
* Population-density classification
* Legend
* North arrow
* Scale bar
* Data source
* Coordinate system

---

# 📈 Spatial Analysis

The resulting choropleth map can be used to identify spatial differences in population density across Guwahati.

The analysis can examine:

* High-density wards
* Low-density wards
* Medium-density wards
* Spatial clusters
* Distribution of population across the city

The density pattern can also be compared with geographical and urban factors such as:

* Major roads
* Commercial areas
* Built-up areas
* Rivers
* Water bodies
* Hills
* Terrain
* Accessibility
* Urban development

---

# ⚠️ Data Limitation

An important limitation of this project is the difference between the **current 60-ward administrative boundary framework** and the **Census 2011-based population data**.

The GIS boundary framework used in this project consists of the 60 GMC wards, while the population figures are based on Census 2011-era demographic data.

Therefore, the map should be interpreted as:

> **A population-density analysis using the 60-ward GMC spatial framework and Census 2011-based population data.**

It should **not** be interpreted as an exact representation of Guwahati's population density in 2026.

Future studies could use updated ward-level population estimates when reliable and compatible data become available.

---

# 💻 Software

The project was created using:

```text
ArcMap
```

ArcMap was used for:

* Spatial data management
* Attribute-table editing
* Population data entry
* Coordinate projection
* Area calculation
* Population-density calculation
* Choropleth mapping
* Cartographic layout
* Map export

---

# 📁 Project Structure

A recommended project structure is:

```text
Guwahati-Population-Density-GIS/
│
├── README.md
│
├── data/
│   ├── ward_boundary/
│   ├── population/
│   └── reference_data/
│
├── maps/
│   ├── Guwahati_Population_Density.pdf
│   └── Guwahati_Population_Density.png
│
├── arcmap/
│   └── Guwahati_Population_Density.mxd
│
└── documentation/
    └── methodology.md
```

---

# 📤 Exporting the Map

The final map can be exported from ArcMap using:

```text
File
→ Export Map
```

Recommended formats:

### PDF

Best for:

* University reports
* Printing
* Maintaining vector quality

### PNG

Best for:

* README files
* Presentations
* Word documents
* Online portfolios

A resolution of approximately:

```text
300 DPI
```

is recommended for a high-quality project map.

---

# 💾 ArcMap Project File

The ArcMap project should be saved as:

```text
Guwahati_Population_Density.mxd
```

The `.mxd` file stores the map document, including:

* Layer arrangement
* Symbology
* Map layout
* Legend
* Scale bar
* North arrow
* Text
* Map settings

The underlying shapefile and other datasets should remain in their original project folders.

---

# 📊 Population Data

The ward-wise population dataset used for the project is based on Census 2011.

The population values entered into the GIS layer are:

| Ward | Population |
| ---: | ---------: |
|    1 |     16,692 |
|    2 |     16,613 |
|    3 |     11,106 |
|    4 |     10,731 |
|    5 |     12,526 |
|    6 |     10,171 |
|    7 |     20,366 |
|    8 |      7,593 |
|    9 |      6,746 |
|   10 |     10,216 |
|   11 |     18,514 |
|   12 |     39,995 |
|   13 |     29,041 |
|   14 |     17,629 |
|   15 |     19,228 |
|   16 |     39,056 |
|   17 |     21,292 |
|   18 |      7,431 |
|   19 |     14,957 |
|   20 |     11,887 |
|   21 |      7,718 |
|   22 |     21,169 |
|   23 |     10,837 |
|   24 |     17,830 |
|   25 |     20,707 |
|   26 |     10,431 |
|   27 |     12,008 |
|   28 |      9,828 |
|   29 |      6,988 |
|   30 |      5,688 |
|   31 |      7,387 |
|   32 |     10,332 |
|   33 |      8,368 |
|   34 |     11,088 |
|   35 |     11,012 |
|   36 |     13,966 |
|   37 |     15,854 |
|   38 |      8,589 |
|   39 |     11,574 |
|   40 |      7,782 |
|   41 |     21,514 |
|   42 |     16,649 |
|   43 |      9,295 |
|   44 |     15,073 |
|   45 |     12,537 |
|   46 |     28,309 |
|   47 |      9,772 |
|   48 |     12,686 |
|   49 |     30,124 |
|   50 |     14,084 |
|   51 |     30,057 |
|   52 |      9,000 |
|   53 |     14,890 |
|   54 |     24,226 |
|   55 |     13,670 |
|   56 |     26,625 |
|   57 |     13,359 |
|   58 |     31,876 |
|   59 |     25,709 |
|   60 |     26,951 |

---

# 🔬 Research Workflow Summary

The complete research process can be summarized as:

```text
RESEARCH QUESTION
        ↓
How is population density distributed across
the 60 wards of Guwahati?
        ↓
STUDY AREA
        ↓
Guwahati Municipal Corporation
        ↓
SPATIAL DATA
        ↓
60 Ward Boundary Layer
        ↓
DEMOGRAPHIC DATA
        ↓
Census 2011 Population
        ↓
DATA PREPARATION
        ↓
Population + Ward Area
        ↓
CALCULATION
        ↓
Population / Area
        ↓
POPULATION DENSITY
        ↓
CARTOGRAPHY
        ↓
Graduated Colours
+ Natural Breaks
        ↓
CHOROPLETH MAP
        ↓
SPATIAL ANALYSIS
        ↓
Interpretation of high- and low-density areas
```

---

# 🎓 Conclusion

This project demonstrates how GIS can be used to analyse and visualize demographic information.

By combining ward boundaries, population data and calculated ward areas, population density was calculated for each ward of Guwahati Municipal Corporation.

The resulting choropleth map provides a visual representation of spatial variation in population density across the city.

The project demonstrates the importance of:

* Correct spatial boundaries
* Reliable demographic data
* Appropriate coordinate systems
* Accurate area calculations
* Correct density calculations
* Appropriate classification methods
* Effective cartographic design

The project also highlights an important GIS principle:

> **Spatial data and attribute data must correspond to the same geographic units for meaningful analysis.**

---

# 👤 Author

**Archit Dhruw**

**Project:** Mapping Population Density of Guwahati Using GIS

**Study Area:** Guwahati Municipal Corporation, Assam, India

**Software:** ArcMap

**Coordinate System:** WGS 1984 UTM Zone 46N

---

# 📚 Keywords

```text
GIS
ArcMap
Geography
Population Density
Guwahati
Assam
Guwahati Municipal Corporation
Choropleth Map
Spatial Analysis
Demographic Mapping
Cartography
Census 2011
```

```
```
