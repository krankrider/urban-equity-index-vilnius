# 🌱 Green for All LT  
## Urban Equity Index (UEI) for Vilnius

**Duration**: October – December 2025  

---

## Overview

**Green for All LT** analyzes **urban equity and accessibility** across **Vilnius elderships (seniūnijos)** by integrating environmental, social, transport, and infrastructure data into a unified **Urban Equity Index (UEI)**.

The project identifies neighborhoods where **low urban equity intersects with limited access to green spaces, public transport, services, and waste infrastructure**, supporting evidence-based urban planning, public health policy, and EU Green City objectives.

---

## Core Research Questions

- Which elderships in Vilnius experience **structural urban disadvantage**?
- How does access to **green space, transport, services, and waste infrastructure** vary across the city?
- Where do **high social vulnerability and poor accessibility overlap**?
- How can a composite index support **transparent prioritization of urban interventions**?

---

## Data Sources

| Type | Source | Description | Format |
|------|--------|------------|--------|
| **Administrative Boundaries** | Vilnius Data Portal (vplanas.lt) | Official eldership boundaries | GeoJSON |
| **Demographics & Socioeconomics** | Statistics Lithuania (stat.gov.lt) | Population, density, age structure, unemployment, income | CSV |
| **Green & Public Amenities (Live API)** | OSM / Municipal datasets | Green areas, education, health, cultural facilities | CSV / GeoJSON |
| **Transport Infrastructure (Live API)** | Vilnius GIS Services | Bus stops (real-time API) | REST / GeoJSON |
| **Environmental Data** | Municipal / Public datasets | PM2.5, NO₂ air pollution | CSV |
| **Waste Infrastructure** | Vilnius Open Data | Waste container locations | GeoJSON |
| **Benchmarks** | WHO / Eurostat | Green space standards (≥0.5 ha / 1,000 residents) | Guidelines |

> All data sources are **open, public, and license-compliant**.

---

## Tech Stack

- **Language**: Python  
- **Spatial Analysis**: `geopandas`, `shapely`  
- **Data Processing**: `pandas`, `numpy`  
- **Modeling & Indexing**: `scikit-learn`  
- **Visualization**: `matplotlib`, `seaborn`  
- **APIs**: REST (Vilnius GIS services)  
- **Tools**: Jupyter Notebook, VS Code, GitHub  

---

## Methodology

### 1. Spatial Unit
- Analysis conducted at **eldership (seniūnija)** level.
- All indicators are aggregated or normalized to this unit.

---

### 2. Urban Equity Index (UEI) — Core Backbone

UEI is the **central, unifying index** of the project.

**Components:**
- Green space availability per capita  
- Health facilities per capita  
- Education facilities per capita  
- Cultural facilities per capita  

**Adjustments:**
- Penalized by:
  - Elderly population share  
  - Unemployment rate  

**Outputs:**
- `UEI_final` — raw index (0–1)  
- `UEI_norm` — normalized UEI (used across all analyses)  

UEI is **defined once and reused consistently** across clustering, accessibility, vulnerability, and infrastructure analyses.

---

### 3. Clustering of Elderships
- KMeans clustering using:
  - UEI  
  - Population density  
  - Elderly share  
  - Unemployment rate  
- Elbow + silhouette methods used to select optimal clusters.
- Identifies **structural urban typologies**.

---

### 4. Built Environment & Density Analysis
- Dwelling density  
- Population density  
- Building height  
- Floor Area Ratio  
- Green space percentage  

Used to contextualize equity outcomes spatially.

---

### 5. Environmental Exposure
- PM2.5 and NO₂ concentrations  
- Correlation with:
  - Density  
  - Green space  
  - Socioeconomic indicators  

No imputation applied to pollution data to avoid artificial exposure values.

---

### 6. Transport Accessibility
- Live bus stop data via municipal API  
- Indicators:
  - Stops per km²  
  - Stops per 100 / 1,000 residents  
- Combined with green space and **UEI** into a **contextual accessibility score**.

---

### 7. Transport & Social Vulnerability Index (TSVI)

TSVI integrates:
- Social vulnerability (age, unemployment, income)  
- Transport deprivation  
- Inverted UEI (low equity increases priority)  

This index identifies **high-priority intervention zones**.

---

### 8. Multi-Criteria Accessibility Ranking
- Combines:
  - Transport access  
  - Green access  
  - Public services  
  - UEI  
  - Demographic vulnerability  
- Produces a ranked list of elderships for policy prioritization.

---

### 9. Waste Infrastructure Accessibility
- Spatial distribution of waste containers  
- Density, clustering, and nearest-neighbor analysis  
- Waste accessibility score **moderated by UEI**
  (low-equity areas penalized more strongly).

---

## Outputs

- Composite indices (UEI, TSVI, accessibility scores)  
- Static maps (equity, transport, waste, vulnerability)  
- Rankings of elderships by priority  
- Processed datasets (`/data/processed`)  
- Figures for reports and presentations (`/docs`)  

---

## Social & Policy Impact

- **Equity-driven**: Moves beyond raw accessibility to structural disadvantage  
- **Policy-ready**: Supports targeted municipal investment  
- **EU-aligned**: Contributes to EU Green City Accord and National Urban Policy  
- **Transparent**: Index construction is explicit, reproducible, and defensible 

#### Contribution
All team members contributed equally to the project development, data analysis, and report writing.
