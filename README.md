# NYC Public Restroom Accessibility and Facility Location Optimization

A geospatial analysis of public restroom accessibility across New York City, combining demographic data, spatial accessibility metrics, and facility-location optimization to identify underserved areas and recommend candidate locations for new public restrooms.

## Full Analysis

For the complete analysis, including Python code, methodology, visualizations, and interactive maps:

[**View Full Interactive Analysis**](https://chaeyeonlee01.github.io/nyc-restroom-accessibility-optimization/)

---

## Project Overview

Public restroom infrastructure is unevenly distributed across New York City. High population density does not necessarily correspond to better restroom access, while some parks and tourist-oriented areas contain disproportionately large concentrations of facilities.

This project evaluates public restroom accessibility across **1,600+ NYC census tracts** and addresses two main questions:

1. Which census tracts experience the greatest public restroom accessibility shortages?
2. Where should new restroom facilities be located to improve accessibility in the most underserved areas?

The analysis develops a composite **Priority Score** to identify underserved census tracts and applies a **weighted p-median facility-location model** to recommend candidate restroom locations within the five highest-priority areas.

---

## Data

The project integrates **nine public datasets** from NYC Open Data, the Metropolitan Transportation Authority (MTA), and the U.S. Census Bureau.

Key data sources include:

* NYC Public Restrooms
* U.S. Census TIGER/Line Census Tract Boundaries
* American Community Survey (ACS) Population Estimates
* MTA Subway Stations
* MTA Bus Stops
* NYCHA Facilities and Service Centers
* NYC School Locations
* NYC Parks
* NYC Facilities Database

These datasets were spatially integrated to capture both existing restroom supply and potential local demand around community facilities.

---

## Methodology

### 1. Geospatial Data Integration

Public restroom locations, census tract boundaries, population estimates, and community-facility datasets were cleaned and integrated using Python and GeoPandas.

Spatial joins and distance calculations were used to construct tract-level accessibility measures across New York City.

### 2. Accessibility Indicator Construction

Four tract-level indicators were calculated:

* **Population Density**
* **Distance to the Nearest Public Restroom**
* **Restroom Count**
* **People per Restroom**

Because several indicators exhibited strongly right-skewed distributions, selected variables were log-transformed and standardized prior to index construction.

### 3. Priority Score

A composite **Priority Score** was constructed using standardized measures of:

* population density,
* nearest-restroom distance, and
* people-per-restroom ratio.

Higher scores represent census tracts where high potential demand coincides with limited restroom availability and poor spatial access.

The five highest-scoring census tracts were selected for detailed facility-location analysis.

### 4. Facility-Location Optimization

Community facilities located within approximately **1,500 ft** of the five highest-priority tracts were used as demand proxies.

Six facility categories were incorporated:

* Subway stations
* Bus stops
* Schools
* Parks
* NYCHA facilities
* Social service facilities

A **weighted p-median model (p = 1)** was applied within each priority tract to identify a candidate location that minimizes weighted distance to surrounding demand points.

---

## Key Findings

* Public restroom availability showed substantial spatial inequality across New York City and was not consistently aligned with population density or residential demand.
* The highest-priority census tracts combined **high population density, long distances to existing restrooms, and limited restroom infrastructure**.
* Spatial analysis of nearby community facilities revealed additional concentrations of potential restroom demand around the identified priority areas.
* The weighted p-median model generated candidate restroom locations for each of the five highest-priority census tracts.
* Adding the proposed facilities was projected to reduce distance to the nearest restroom by approximately **66%–86%** across the five priority tracts.

---

## Analytical Workflow

`Public Data Integration`
→ `Geospatial Preprocessing`
→ `Accessibility Indicator Construction`
→ `Priority Score`
→ `Identification of Underserved Tracts`
→ `Community-Facility Demand Analysis`
→ `Weighted p-Median Optimization`
→ `Accessibility Improvement Evaluation`

---

## Tools & Techniques

**Python · GeoPandas · pandas**

**Geospatial Analysis · Spatial Joins · Distance Analysis · Data Standardization · Composite Index Construction · Facility Location Optimization · p-Median Model · Interactive Mapping**

