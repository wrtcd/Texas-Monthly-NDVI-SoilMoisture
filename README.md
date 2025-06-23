# Texas Monthly NDVI & Surface Soil Moisture (2019–2023)

This repository provides monthly vegetation greenness and surface soil moisture statistics for the state of Texas from January 2019 to December 2023. The analysis leverages Google Earth Engine (GEE) to compute spatially averaged values of NDVI (Normalized Difference Vegetation Index) and SMAP surface soil moisture across the state boundary.

## Dataset Summary

| Variable               | Source Dataset                                              | Spatial Resolution | Temporal Resolution |
|------------------------|-------------------------------------------------------------|--------------------|----------------------|
| NDVI                  | Sentinel-2 Surface Reflectance Harmonized (`COPERNICUS/S2_SR_HARMONIZED`) | 10–30 meters       | Monthly (median)     |
| Surface Soil Moisture | SMAP Level 4 (`NASA/SMAP/SPL4SMGP/007`)                      | ~9 km              | Monthly (mean)       |

## Methodology

- **NDVI** is calculated from Sentinel-2 imagery using the normalized difference of near-infrared (B8) and red (B4) bands. A monthly median composite is used after cloud filtering.
- **Surface Soil Moisture** is derived by averaging the SMAP Level-4 surface moisture (`sm_surface`) values over each month.
- Both datasets are clipped to the Texas boundary using the U.S. Census TIGER/Line shapefiles.
- Monthly statewide mean values are calculated and exported as a single CSV file.

## Output

The final CSV file contains the following columns:

| Column               | Description                                              |
|----------------------|----------------------------------------------------------|
| `date`               | Month in `YYYY-MM` format                                |
| `mean_ndvi`          | Mean NDVI for Texas during that month (0 to 1)          |
| `mean_smap_surface`  | Mean surface soil moisture for Texas during that month (m³/m³) |

## Applications

- Monitoring vegetation response to rainfall and seasonal change  
- Assessing short-term soil moisture stress  
- Supporting drought tracking and agricultural water management in Texas

## Data Access

- **Sentinel-2 Harmonized**: [COPERNICUS/S2_SR_HARMONIZED](https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_SR_HARMONIZED)
- **SMAP Surface Soil Moisture (Level 4)**: [NASA/SMAP/SPL4SMGP/007](https://developers.google.com/earth-engine/datasets/catalog/NASA_SMAP_SPL4SMGP_007)
- **Texas Boundary**: [U.S. Census TIGER/Line Shapefiles](https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.html)

## License

This dataset is derived from publicly available sources including NASA SMAP Level-4 products and Copernicus Sentinel-2 imagery via Google Earth Engine.  
Please cite NASA and the European Space Agency (ESA) appropriately when using or referencing this dataset.  
The state boundary is based on U.S. Census TIGER/Line shapefiles.
