# Forest Inventory Plots — Prototype Dashboard Data (NFI2/NFI3/NFI4)

This repository contains a **prototype dataset for the Palencia Forest Model** and a **single-plot example** (Plot ID: *Estadillo* 160) to support the development of a future dashboard for Spain’s **National Forest Inventory** editions (**NFI2**, **NFI3**, **NFI4**).

---

## Repository structure

```
.
├─ Plot_1_SITUATION/
│  └─ PlotSituation_EN.csv
├─ Plot_2_NATURALCONDITIONS/
│  ├─ PlotClimate.csv
│  └─ PlotNaturalConditionsEN.csv
├─ Plot_3_FORESTSTOCKS/
│  └─ PlotForestStocks_EN.csv
├─ Plot_4_FORESTDAMAGE/
│  ├─ DamageNFI2_EN.csv
│  ├─ DamageNFI3_EN.csv
│  └─ DamageNFI4_EN.csv
├─ Plot_5_WOODQUALITY/
│  └─ PlotQuality_EN.csv
├─ Plot_6_CARBON/
│  └─ PlotCarbon_EN.csv
├─ Plot_7_FORESTSTATUS/
│  ├─ Plot_ForestEstatus_EN.csv
│  ├─ PlotTreeLayer_EN.csv
│  └─ PlotShrubLayer_EN.csv
├─ docs/
│  └─ DataDictionary.md
└─ Plot_160_EN.pdf
```

Each top-level folder corresponds to a **dashboard section** and contains one or more CSV files with **plot-level** attributes.

---

## Key concepts 

- **Plot (`Estadillo`)**: unique plot identifier used to join all tables (and optionally `CoorX`, `CoorY`).  
- **Coordinates (`CoorX`, `CoorY`)**: projected coordinates (ETRS89 / UTM, EPSG:25830) used to locate the plot.
- **NFI2/NFI3/NFI4**: different editions (field campaigns) of the national forest inventory through time (every 10 years approx).  
- **Species codes (`SpeciesID`)**: numerical identifiers mapped to scientific names (`SpeciesName`).  
- **Units & conventions**: Coordinates in meters (projected CRS), Altitude in meters, Slope in degrees, Canopy in %, Volume in m³/ha, Carbon in tC/ha (unless stated otherwise).
- **NFI codes**: Many categorical variables—such as species codes, quality classes, origin codes, regeneration classes, and damage categories—follow the official coding definitions of the Spanish National Forest Inventory (in Spanish).
Full documentation:
https://www.miteco.gob.es/content/dam/miteco/es/biodiversidad/servicios/banco-datos-naturaleza/documentador_bdcampo_ifn3_tcm30-282240.pdf


 