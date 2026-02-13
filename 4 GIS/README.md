# 🌊 Flood Risk Zones in Harris County, Texas (GIS Project)

**Course:** Apps in Geospatial Analytics (CE502D1_F24) — Fall 2024  
**Professor:** Prof. Mehmet Ozdes  
**Author:** Nikhil Chhatraband  

---

## 🚀 Project Summary (1-minute read)
Harris County, Texas (Houston area) is one of the most flood-prone and densely populated regions in the U.S. Its proximity to the Gulf of Mexico combined with rapid urbanization makes it highly vulnerable to catastrophic flooding events like **Hurricane Harvey (2017)**.

This GIS project investigates how **flood risk relates to impervious cover and elevation** by integrating:
- **FEMA floodplain zones**
- **Impervious surface coverage (City of Houston / SIMMER)**
- **National Elevation Dataset (NED)**

The goal is to highlight areas that face elevated flood risk due to **low infiltration + low elevation + high impervious development**.

---

## 🎯 Problem Statement
Managing flood risk is not just about identifying where floods have happened—it’s about understanding **why certain areas are more vulnerable**.

This study explores:
- The relationship between **impervious cover levels** and **floodplain zones**
- How **elevation and watercourses** influence flood risk
- Whether high impervious development aligns with higher risk zones

✅ **Hypothesis:**  
High impervious cover is associated with increased flood risk, lower elevation, and proximity to water sources.

---

## 🧠 Key Questions
1. Do high impervious cover areas overlap with FEMA 100-year flood zones?
2. How does elevation correlate with floodplain locations?
3. Which parts of Harris County show the highest combined risk?

---

## 🗺 Data Sources
| Dataset | Source | Notes |
|---|---|---|
| Harris County Boundary (Shapefile) | HCAD GIS | Used for clipping and study boundary |
| Impervious Cover | City of Houston (SIMMER) | Reclassified into Low/Medium/High |
| Elevation (Raster Tiles) | National Elevation Dataset (NED) | Mosaic to new raster → clipped to county |
| FEMA Floodplain | FEMA 2015 | Flood zones clipped to Harris County |

📌 Links (as used in the report):
- Harris County Boundary: https://hub.arcgis.com/datasets/HarrisCounty::hcad-harris-county-boundary  
- Impervious Cover: https://www.h-gac.com/land-use-and-land-cover-data  
- NED (Texas): https://data.tnris.org/collection?c=e0ead9bd-0c01-4716-97e9-808ec330afd2  
- FEMA Floodplain: https://h-gac.sharefile.com/share/view/s3afeac2a3314e4bb  

---

## 🛠 Tools & Tech
- ArcMap / ArcGIS (primary)
- Spatial Analyst tools
- Raster operations (Mosaic, Clip, Reclassify, Raster Calculator)

---

## 🔬 Methodology (Clear Workflow)
### 1) Data Preparation
- Loaded topographic basemap
- Reprojected datasets to consistent CRS  
- Clipped basemap to Harris County boundary

### 2) Impervious Cover Processing
- Clipped impervious coverage to county boundary
- Classified using **Natural Breaks** into 3 levels:
  - **Low:** 0–38%  
  - **Medium:** 38–58%  
  - **High:** 58–92%

### 3) FEMA Floodplain Processing
- Clipped FEMA floodplain to Harris County
- Consolidated key flood zones:
  - **Zone X:** Outside 100-year floodplain
  - **Zones A/AE/AO:** Within 100-year floodplain
  - **Zone VE:** Coastal hazard floodplain

### 4) Elevation Processing
- Downloaded multiple NED raster tiles
- Used **Mosaic to New Raster**
- Clipped raster to Harris County boundary

### 5) Combined Flood Risk Ranking (Raster Model)
Converted both layers to raster and ranked them:

**Impervious Ranking**
- Low → 1  
- Medium → 2  
- High → 3  

**Flood Zone Ranking**
- Zone X → 1  
- A/AE/AO → 2  
- VE → 3  

**Final Risk Calculation**
- Used Raster Calculator:  
  `flood_reclass + imp_reclass`

Result: final risk surface ranked from lower to higher risk (green → blue gradient).

---

## ✅ Results & Key Insights
### 🔥 Main Finding
High impervious development aligns strongly with higher flood risk—especially in the dense urban core.

- **Central Harris County (Houston)** shows higher impervious cover and higher combined risk.
- Suburban areas show lower impervious cover and are often outside the 100-year floodplain (Zone X).
- Flood zones closely track **watercourses and lower elevation corridors**, supporting FEMA’s risk zoning logic.

### 🌱 Practical Interpretation
- Urbanization increases impervious cover → decreases infiltration → increases flood severity.
- As population grows, impervious cover will likely grow → increasing flood vulnerability without mitigation.

---

## 🧩 Mitigation Discussion (Real-world Impact)
Houston has already taken steps to reduce flood damage after Harvey, including:
- Channel improvements
- Stormwater retention measures
- Levee planning
- Bayou system engineering (widening/deepening + vegetation management)

These interventions align with the spatial patterns identified in this analysis.

---

## 🖼 Visual Outputs (Add your images here)
Create a folder: `4 GIS/images/` and add exported maps with these names:

- `figure_1_fema_floodzones.png`
- `figure_2_elevation_map.png`
- `figure_3_impervious_cover.png`
- `figure_4_combined_risk.png`

Then they will show directly in GitHub:

### Figure 1 — FEMA Floodzones
![FEMA Floodzones](images/figure_1_fema_floodzones.png)

### Figure 2 — Elevation Map
![Elevation](images/figure_2_elevation_map.png)

### Figure 3 — Impervious Cover
![Impervious](images/figure_3_impervious_cover.png)

### Figure 4 — Flood Risk + Impervious Cover (Final Output)
![Final Risk](images/figure_4_combined_risk.png)

---


