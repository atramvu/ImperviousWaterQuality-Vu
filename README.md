# ImperviousWaterQuality-Vu
Impervious Cover by Land Use in Calgary - GEOG 587

Author: Tram Anh Vu

## Overview: This project quantifies impervious within generalized land use categories for Calgary, then overlays Regulatory Flood Hazard polygons to interpret where elevated runoff potential intersects designated flood zones. The workflow is fully documented to support the analysis of the study.
## Purpose: to understand whether impervious surface functions as a practical indicator for urban water and soil impacts, giving its general role in generating runoff, transporting pllutants and alternating hydrographs. By overlaying land use with flood hazard, the analysis offers a simple, transparent approach that planners and students can replicate, critique and extend.

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

   ** City of Calgary Open Data Portal**
     - `Impervious Surface 2021` last updated May 28, 2024, was accessed on October 1, 2025, link for access https://data.calgary.ca/Environment/Impervious-Surface-2021/rgsu-3v7u/about_data
     - `Land Use Districts` last updated October 22, 2025, was accessed on October 13, 2025, link for access https://data.calgary.ca/Base-Maps/Land-Use-Districts/qe6k-p9nh/about_data
     - `Regulatory Flood Map (Bylaw Flood Hazard)` last updated June 27, 2024, was accessed on October 22, 2025, link for access https://data.calgary.ca/Environment/Regulatory-Flood-Map-Bylaw-Flood-Hazard-/tp6q-x2v7/about_data
     
   **Basemap & Reference providers** 
   Esri, USGS, CGIAR, TomTom, Garmin, FAO, NOAA, OpenStreetMap Contributors, and the GIS User Community
     - `World Topographic Map` accessed on October, 2025, link for access https://services.arcgisonline.com/ArcGIS/rest/services/World_Topo_Map/MapServer

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
   
   1. **Reclassifiation Land Use**
      - Create `LU_Simple` mapping detailed classes into 9 main categories:
         - Agricultural and Natural Resources,
         - Parks/Open Space,
         - Institution,
         - Transportation/Utility,
         - Other,
         - Residential   
         - Low/Medium Density,
         - Residential Hight Density,
         - Industrial, and
         - Commercial/Mixed Use
   
   - Dissolve all polygons within each reclassified land use categories to merge them into one feature using the Dissolve tool.
   - Dissolve all Impervious Polygons to create a single Impervious Surface layer using the Dissolve tool
   - Intersect the Impervious Surface layer with the Dissolved Land Use layer to calculate the Impervious Surface by Land Use, this create a new data called `ImperviousByLandUse`.
   - In the `ImperviousByLandUse` data, calculated 2 fields: Impervious Area in m2 and Land Use in m2, both fields were calculated using the Geometry Calculator tool.
   - In the `ImperviousByLandUse` data, calculated another field called `% Impervious by Land Use`, used the field calculator tool and compute this formula (Imp_Area_m2)*100/(LU_Area_m2)
   - Displayed the `ImperviousByLandUse` data using the field `% Impervious` using the Graduated Colours option with 9 classes and Natural Breaks (Jenks) method, the colour scheme was light as least % Impervious Surface to dark red as most % Impervious Surface
   - Rename the `Regulatory Flood Map (Bylaw Flood Hazard)` data to `FloodMap_Calgary`, displayed it with 30% transparent overlay on top of the Impervious surface data.
   - The City Boundary was displayed as grey thick outline 
    
License

   - This repository is shared uner the Creative Commons Attribution 4.0 International (CC BY 4.0)
     
Citation

  - Vu, T.A. (2025), *Impervious Cover by Land Use in Calgary*. GEOG 587 - University of Calgary
   
Contact

  - Tram Anh Vu atramvu@gmail.com 
