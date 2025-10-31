# ImperviousWaterQuality-Vu
Impervious Cover by Land Use in Calgary - GEOG 587

Author: Tram Anh Vu

## Overview: 
This project quantifies impervious within generalized land use categories for Calgary, then overlays Regulatory Flood Hazard polygons to interpret where elevated runoff potential intersects designated flood zones. The workflow is fully documented to support the analysis of the study.
## Purpose: 
To understand whether impervious surface functions as a practical indicator for urban water and soil impacts, giving its general role in generating runoff, transporting pllutants and alternating hydrographs. By overlaying land use with flood hazard, the analysis offers a simple, transparent approach that planners and students can replicate, critique and extend.

## Folder Structure: 
   - `data/` - raw and processed dataset
      - `Raw` CityBoundary, Impervious_Surface_Calgary_original.csv, FloodMap-Calgary_original, LandUse_Calgary_Original
      - `Processed` FloodMap_Calgary, ImperviousByLandUse, 
   - `outputs/` - layout of final maps:
      - % IMPERVIOUS AND FLOOD ZONE BY Land Use CALGARY.pdf
      - % IMPERVIOUS BY Land Use CALGARY.pdf
   - `Documentation` -  README     

## Coordinates Systems and Data formats
   - `Coordinates Systems` Projected CRS NAD 1983 3TM 114W, units: meters
   - `Data Formats` csv, pdf, lyrx 

## Data Source
**City of Calgary Open Data Portal**
- Impervious Surface 2021 — *last updated* 2024-05-28; *accessed* 2025-10-01  
  https://data.calgary.ca/Environment/Impervious-Surface-2021/rgsu-3v7u/about_data
- Land Use Districts — *last updated* 2025-10-22; *accessed* 2025-10-13  
  https://data.calgary.ca/Base-Maps/Land-Use-Districts/qe6k-p9nh/about_data
- Regulatory Flood Map (Bylaw Flood Hazard) — *last updated* 2024-06-27; *accessed* 2025-10-22  
  https://data.calgary.ca/Environment/Regulatory-Flood-Map-Bylaw-Flood-Hazard-/tp6q-x2v7/about_data

**Basemap & reference providers**  
Esri, USGS, CGIAR, TomTom, Garmin, FAO, NOAA, OpenStreetMap contributors, GIS User Community  
- World Topographic Map — *accessed* 2025-10  
  https://services.arcgisonline.com/ArcGIS/rest/services/World_Topo_Map/MapServer

## Data Dictionary

  ### ImperviousByLandUse data
   
   - `Imp_Area_m2` area of Impervious Surfaces in each land use categories in meter square. It was calculated using the Geometry Field Calculator tool.
   - `LU_Simple` description of each land use categories such as Commercial, Industrial, Institutional, Parks, Residential, Transportation and Agriculture
   - `LU_Area_m2` area of total land use for each categories in meter square
   - `% Impervious` Percentage of Impervious Surface in each land use categories. It was calculated using the Field Calculator tool. It was calculated using the formula (Imp_Area_m2)*100/(LU_Area_m2)

 ### FloodMap_Calgary data

   - `Descriptio` is the description of each flood hazardous zones in the city of Calgary
   - `flood-cd` is the number of year of flood reoccurence 
   - `Perimeter` is the perimeter of each polygons
    
### Methods/ Workflow Summary (ArcGIS Pro)

   Raw data obtained from the City of Calgary Open Data Portal was analyzed using geospatial tools in ArcGIS Pro.

1. **Reclassify Land Use**  
   - Create `LU_Simple` mapping detailed classes into 9 categories (above).  
   - *Tool(s):* Field mapping / attribute rule, then **Dissolve** by `LU_Simple` → `LandUse_Reclassified_Dissolved`.

2. **Prepare Impervious Layer**  
   - **Dissolve** all impervious polygons → `Impervious_Dissolved`.

3. **Intersect**  
   - **Intersect** `Impervious_Dissolved` with `LandUse_Reclassified_Dissolved` → `ImperviousByLandUse`.

4. **Add Geometry & Calculate Fields**  
   - **Add Geometry Attributes** to compute `Imp_Area_m2` (impervious parts) and `LU_Area_m2`.  
   - **Calculate Field**: `Pct_Impervious = (Imp_Area_m2 / LU_Area_m2) * 100`.

5. **Symbology**  
   - **Graduated Colors** on `Percent_Impervious`, **9 classes**, **Natural Breaks (Jenks)**.  
   - Light color = low %, dark red = high %.  
   - Add **FloodMap_Calgary** with ~30% transparency above the impervious choropleth.  
   - City boundary with a neutral grey, thick outline.

6. **Map Layouts**  
   - Export to `outputs/Calgary_Impervious_by_LandUse.pdf` and  
     `outputs/Calgary_Impervious_and_FloodZone_by_LandUse.pdf`.

## How to Reproduce
 - Software: **ArcGIS Pro**
 - Steps: Set the Map projection to Projected CRS NAD 1983 3TM 114W, units: meters. Add raw data layers to the Map Content.
 - Run tools in the *Methods/Workflow Summary* Section
 - Geoproecessing Tools to use: **Reclassify**, **Dissolve**, **Intersect**, **Add Field**, **Field Calculator**, **Geometry Calculator**
 - Symbology: Use Graduated colors on the `Percent_Impervious` field, set the flood categories to 30% transparency
   
## License

   - This repository is shared uner the Creative Commons Attribution 4.0 International (CC BY 4.0)
     
## Citation

  - Vu, T.A. (2025), *Impervious Cover by Land Use in Calgary*. GEOG 587 - University of Calgary
   
## Contact

  - Tram Anh Vu atramvu@gmail.com 
