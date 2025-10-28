# ImperviousWaterQuality-Vu
Impervious Cover by Land Use in Calgary - GEOG 587

Author: Tram Anh Vu

Overview: This repository packages my geospatial analysis on Impervious Cover by Land Use in Calgary

Folder Structure: 
   - `data/` - raw and processed dataset
      - `Raw` CityBoundary, Impervious_Surface_Calgary_original.csv, FloodMap-Calgary_original, LandUse_Calgary_Original
      - `Processed` FloodMap_Calgary, ImperviousByLandUse, 
   - `outputs/` - layout of final maps:
      - % IMPERVIOUS AND FLOOD ZONE BY Land Use CALGARY.pdf
      - % IMPERVIOUS BY Land Use CALGARY.pdf
   - `Documentation` -  README     

Coordinates Systems and Data formats
   - `Coordinates Systems` Projected NAD 1983 3TM 114W
   - `Data Formats` csv, pdf

Data Source
   - `City of Calgary Open Data Portal`
     - `Impervious Surface 2021` last updated May 28, 2024, was accessed on October 1, 2025, link for access https://data.calgary.ca/Environment/Impervious-Surface-2021/rgsu-3v7u/about_data
     - `Land Use Districts` last updated October 22, 2025, was accessed on October 13, 2025, link for access https://data.calgary.ca/Base-Maps/Land-Use-Districts/qe6k-p9nh/about_data
     - `Regulatory Flood Map (Bylaw Flood Hazard)` last updated June 27, 2024, was accessed on October 22, 2025, link for access https://data.calgary.ca/Environment/Regulatory-Flood-Map-Bylaw-Flood-Hazard-/tp6q-x2v7/about_data
   - `Esri`, `USGS`, `CGIAR`, `TomTom`, `Garmin`, `FAO`, `NOAA`, `OpenStreetMap Contributors`, and the `GIS User Community`
     - `World Topographic Map` accessed on October , 2025, link for access https://services.arcgisonline.com/ArcGIS/rest/services/World_Topo_Map/MapServer

Data Dictionary

   - `Imp_Area_m2` area of Impervious Surfaces in each land use categories in meter square. It was calculated using the Geometry Field Calculator tool.
   - `LU_Simple` description of each land use categories such as Commercial, Industrial, Institutional, Parks, Residential, Transportation and Agriculture
   - `LU_Area_m2` area of total land use for each categories in meter square
   - `% Impervious` Percentage of Impervious Surface in each land use categories. It was calculated using the Field Calculator tool. It was calculated using the formula (Imp_Area_m2)*100/(LU_Area_m2)
    
Workflow Summary

   Raw data obtained from the City of Calgary Open Data Portal was analyzed using geospatial tools in ArcGIS Pro.
   
   - Reclassifiation of the detailed `LandUse_Calgary_original` dataset to simplify it into 9 main categories:
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
