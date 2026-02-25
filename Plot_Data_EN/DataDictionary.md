# Data Dictionary — Forest Inventory Prototype

This document describes **columns, types, units, and meaning** for every CSV grouped by dashboard section. 

---

## 1) Plot Situation (`Plot_1_SITUATION/PlotSituation_EN.csv`)

**Grain:** 1 row per plot (`Estadillo`).

| Column | Type | Meaning / Notes |
|---|---|---|
| `Estadillo` | integer | Plot identifier (primary key for joins). |
| `CoorX`, `CoorY` | numeric | Projected coordinates (m). |
| `IDCounty` | integer | County numeric code. |
| `County` | string | County name. |
| `Municipality` | string | Municipality name. |
| `IDMunicipality` | integer | Municipality code. |
| `ProtectedArea` | string | Protected area name (if any). |
| `ProtectionStatus` | string | Protection designation (e.g., “Natural Park”, “Protected Landscape”); may be empty. |
| `PublicForest` | string | Public forest (Yes/No). |
| `Ownership` | string | Owning entity (e.g., Municipality, ELM). |
| `BoundMarkers` | string | Boundary markers present (Yes/No). |
| `LegaDemarcated` | string | Legally demarcated (Yes/No). |

---

## 2) Natural Conditions (`Plot_2_NATURALCONDITIONS/`)

### 2.1 `PlotNaturalConditionsEN.csv` (1 row per plot)

| Column | Type | Units | Meaning |
|---|---|---|---|
| `Estadillo`, `CoorX`, `CoorY` | — | — | Join keys. |
| `Altitude_m` | numeric | m | Altitude above sea level. |
| `FuelModel` | integer | — | Fuel model (fire behavior code). |
| `Aspect` | numeric| ° | Aspect. |
| `Slope` | numeric | ° | Slope of main exposure. |
| `Exposure` | string | — | Cardinal exposure label (e.g., *Shady slope*, *Sunny slope*). |
| `Stoniness` | string | — | Surface stoniness class. |
| `Texture` | string | — | Soil texture class (*Loam*, *Sandy*, *Clay*). |
| `BioRigion` | string | — | Biogeographic region (*Atlantic*, *Mediterranean*). |
| `OrganicMatter` | string | — | Soil organic matter class. |
| `SoilpH` | string | — | Soil pH class. |
| `SoilType` | string | — | Parent material class (*Siliceous*, *Limestone*). |

### 2.2 `PlotClimate.csv` (12 rows per plot + annual)

| Column | Type | Units | Meaning |
|---|---|---|---|
| `Estadillo` | integer | — | Plot ID. |
| `period` | string | — | Climatology window (e.g., `1991_2020`). |
| `month` | string | — | `01`..`12` or `annual`. |
| `tmin_min/tavg_min/tmax_min` | numeric | °C | Lower bounds for Tmin/Tavg/Tmax. |
| `prec_min` | numeric | mm | Min precipitation. |
| `tmin/tavg/tmax` | numeric | °C | Mean values. |
| `prec` | numeric | mm | Mean precipitation. |
| `tmin_max/tavg_max/tmax_max` | numeric | °C | Upper bounds for Tmin/Tavg/Tmax. |
| `prec_max` | numeric | mm | Max precipitation. |
| `martonne` | numeric | — | Martonne aridity index. |

---

## 3) Forest Stocks (`Plot_3_FORESTSTOCKS/PlotForestStocks_EN.csv`)

**Grain:** multiple rows per plot and **species/DC class**.

| Column | Type | Units | Meaning |
|---|---|---|---|
| `Estadillo`, `CoorX`, `CoorY` | — | — | Join keys. |
| `SpeciesID` | integer | — | Species code. |
| `SpeciesName` | string | — | Scientific or short name (already provided). |
| `DC` | integer | cm | Diameter class midpoint. |
| `N_NFI*` | numeric | trees/ha | Tree density per edition. |
| `BA_NFI*` | numeric | m²/ha | Basal area per edition. |
| `V_NFI*` | numeric | m³/ha | Volume per edition. |

---

## 4) Forest Damage (`Plot_4_FORESTDAMAGE/`)

### 4.1 `DamageNFI2_EN.csv` — summary per plot

| Column | Type | Meaning |
|---|---|---|
| `Estadillo`, `CoorX`, `CoorY` | — | Join keys. |
| `DamageNFI2` | string | Damage status label. |

### 4.2 `DamageNFI3_EN.csv` / `DamageNFI4_EN.csv` — detailed

| Column | Type | Meaning |
|---|---|---|
| `Estadillo`, `CoorX`, `CoorY` | — | Join keys. |
| `IdDamageNFI*` | integer | Damage category code. |
| `DamageNFI*` | string | Damage category label. |
| `TreesDamNFI*` | integer | Damaged trees count in the plot. |
| `TotalTreesNFI*` | integer | Total trees measured in the plot. |
| `PercentageDamageNFI*` | numeric | `%` of damaged trees in the plot. |

---

## 5) Wood Quality (`Plot_5_WOODQUALITY/PlotQuality_EN.csv`)

**Grain:** multiple rows per plot (quality classes).

| Column | Type | Units | Meaning |
|---|---|---|---|
| `Estadillo`, `CoorX`, `CoorY` | — | — | Join keys. |
| `QualityClass` | string | class | Quality class code. |
| `Vol_m3_ha_NFI*` | numeric | m³/ha | Volume per class in the plot. |
| `VolTotal_NFI*` | numeric | m³/ha | Total volume per plot. |
| `PercVol_NFI*` | numeric | % | Class share of total volume. |

---

## 6) Carbon (`Plot_6_CARBON/PlotCarbon_EN.csv`)

**Grain:** 1 row per plot, **carbon pools** per edition.

| Column | Type | Units | Meaning |
|---|---|---|---|
| `Estadillo`, `CoorX`, `CoorY` | — | — | Join keys. |
| `Stem_NFI*` | numeric | tC/ha | Carbon in stems. |
| `BranchesOver7cm_NFI*` | numeric | tC/ha | Carbon in branches > 7 cm. |
| `Branches7to2cm_NFI*` | numeric | tC/ha | Carbon in branches 7–2 cm. |
| `BranchesUnder2cmLeaves_NFI*` | numeric | tC/ha | Carbon in branches < 2 cm and leaves. |
| `Roots_NFI*` | numeric | tC/ha | Carbon in roots. |
| `TotalC_NFI*` | numeric | tC/ha | Total carbon (sum of pools). |

---

## 7) Forest Status (`Plot_7_FORESTSTATUS/`)

### 7.1 `Plot_ForestEstatus_EN.csv` — stand-level indicators by edition

| Column | Type | Units | Meaning |
|---|---|---|---|
| `Estadillo`, `CoorX`, `CoorY` | — | — | Join keys. |
| `YearNFI2/3/4` | string/datetime | — | Field date or campaign year per edition. |
| `CanopyNFI*` | numeric | % | Tree canopy cover. |
| `NtreesNFI*` | integer | trees | Number of measured trees. |
| `HoNFI*` | numeric | m | Dominant height. |
| `HmNFI*` | numeric | m | Mean height. |
| `DgNFI*` | numeric | m | Quadratic mean diameter. |
| `DmNFI*` | numeric | m | Mean diameter. |
| `DeadTreesNFI*` | integer | trees | Standing dead trees. |
| `CompositionNFI*` | string | — | Stand composition (Pure/Mixed). |
| `StructureNFI*` | string | — | Stand structure (Even-aged/Uneven-aged). |
| `ShannonNFI*` | numeric | — | Shannon diversity index. |
| `SlendernessNFI*` | numeric | — | Height/DBH --> slenderness index. |
| `SDIR_NFI*` | numeric | 0–1 | Stand density index (relative). |
| `HartNFI*` | numeric | — | Hart-Becking index. |

### 7.2 `PlotTreeLayer_EN.csv` — main (tree) layer per species

| Column | Type | Meaning |
|---|---|---|
| `Estadillo` | integer | Plot ID. |
| `SpeciesID`, `SpeciesName` | — | Tree species code and name. |
| `NtreesNFI*` | integer | Trees counted per edition and species. |
| `AgeNFI3/4` | integer/NA | Age where available. |
| `SPdevelopmentNFI*` / `SPdevelopmentNFI*name` | code/string | Development stage (code + label). |
| `Origin1NFI*`, `Origin1NFI*_EN` | code/string | Stand origin, part I (code + label). |
| `Origin2NFI*`, `Origin2NFI*_EN` | code/string | Stand origin, part II. |
| `SPcoverNFI*` | numeric | % canopy cover by species and edition. |
| `RegenerNFI*`, `RegenerNFI*_EN` | code/string | Regeneration density classes. |

### 7.3 `PlotShrubLayer_EN.csv` — shrub layer per species

| Column | Type | Meaning |
|---|---|---|
| `Estadillo` | integer | Plot ID. |
| `SpeciesID`, `SpeciesName` | — | Shrub species code and name. |
| `CanopySHRNFI*` | numeric | % shrub canopy cover per edition. |
| `HmSHRNFI*` | numeric | m; shrub mean height per edition. |

---

## Appendix — Joins & tips

- **Primary keys**: `Estadillo` is sufficient for most joins; include `CoorX`, `CoorY` to reinforce uniqueness.  
- **Many-to-many**: some tables are long (multiple rows per plot). Summarise **after** joining.  

