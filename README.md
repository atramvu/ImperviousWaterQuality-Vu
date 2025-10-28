# ImperviousWaterQuality-Vu
Impervious Cover by Land Use in Calgary - GEOG 587
Author: Tram Anh Vu
Overview: This repository packages my geospatial analysis on Impervious Cover by Land Use in Calgary
Folder Structure: 
- `data/` - raw and processed dataset
   - `Raw` CityBoundary, Impervious_Surface_Calgary_original.csv, FloodMap-Calgary_original, LandUse_Calgary_Original
   - `Processed` FloodMap_Calgary, ImperviousByLandUse, 
- `outputs/` - layout of final maps: % IMPERVIOUS AND FLOOD ZONE BY Land Use CALGARY.pdf and % IMPERVIOUS BY Land Use CALGARY.pdf
- `Documentation` -  README
Coordinates Systems and Data formats
- `Coordinates Systems` Projected NAD 1983 3TM 114W
- `Data Formats` csv, pdf
Data Source
- `City of Calgary Open Data Portal`
  - `ImpervioususWaterQuality-Vu
Impervious Cover by Land Use in Calgary - GEOG 587
Author: Tram Anh Vu
Overview: This repository packages my geospatial analysis on Impervious Cover by Land Use in Calgary
Folder Structure: 
- `data/` - raw and processed dataset
   - `Raw` CityBoundary, Impervious_Surface_Calgary_original.csv, FloodMap-Calgary_original, LandUse_Calgary_Original
   - `Processed` FloodMap_Calgary, ImperviousByLandUse, 
- `outputs/` - layout of final maps: % IMPERVIOUS AND FLOOD ZONE BY Land Use CALGARY.pdf and % IMPERVIOUS BY Land Use CALGARY.pdf
- `Documentation` -  README
Coordinates Systems and Data formats
- `Coordinates Systems` Projected NAD 1983 3TM 114W
- `Data Formats` csv, pdf
Data Source
- `City of Calgary Open Data Portal`
  - `Impervious Surface 2021` last updated May 28, 2024, was accessed on October 1, 2025, link for access https://data.calgary.ca/Environment/Impervious-Surface-2021/rgsu-3v7u/about_data
  - `Land Use Districts` last updated October 22, 2025, was accessed on October 13, 2025, link for access https://data.calgary.ca/Base-Maps/Land-Use-Districts/qe6k-p9nh/about_data
- `Esri`, `USGS`, `CGIAR`, `TomTom`, `Garmin`, `FAO`, `NOAA`, `OpenStreetMap Contributors`, and the `GIS User Community`
  - `World Topographic Map` accessed on October , 2025, link for access https://services.arcgisonline.com/ArcGIS/rest/services/World_Topo_Map/MapServer

Data Dictionary
 - `Imp_Area_m2` area of Impervious Surfaces in each land use categories in meter square. It was calculated using the Geometry Field Calculator tool.
 - `LU_Simple` description of each land use categories such as Commercial, Industrial, Institutional, Parks, Residential, Transportation and Agriculture
 - `LU_Area_m2` area of total land use for each categories in meter square
 - `% Impervious` Percentage of Impervious Surface in each land use categories. It was calculated using the Field Calculator tool. It was calculated using the formula (Imp_Area_m2)*100/(LU_Area_m2)
Workflow Summary

License
   This repository is shared uner the Creative Commons Attribution 4.0 International (CC BY 4.0)
Citation
   Vu, T.A. (2025), *Impervious Cover by Land Use in Calgary*. GEOG 587 - University of Calgary
Contact
   Tram Anh Vu atramvu@gmail.com 
