# Analyzing the 2025 Los Angeles Wildfires: Remote Sensing and Environmental Justice

## About

This repository contains geospatial analysis of the January 2025 Eaton and Palisades fires in Los Angeles County, combining remote sensing techniques with environmental justice data to understand both the physical impacts and the social dimensions of these devastating wildfires.

The analysis includes two complementary approaches:

1. **False Color Visualization** - Using Landsat 8 satellite imagery to identify burn scars and assess fire severity through infrared band composites
2. **Environmental Justice Analysis** - Examining the socioeconomic characteristics of fire-affected communities using the CDC/ATSDR Environmental Justice Index

**Key outputs:**
- False color composites (SWIR/NIR/Red) highlighting burn scars
- Maps overlaying fire perimeters on satellite imagery
- Spatial analysis of census tracts affected by the fires
- Comparative visualization of socioeconomic vulnerability between fire areas

This project demonstrates the importance of integrating remote sensing with demographic data to understand who bears the burden of climate disasters and to inform equitable recovery planning.

This project was completed as part of EDS 220: Working with Environmental Datasets at the Bren School of Environmental Science & Management, UC Santa Barbara.

## Repository Structure

```
eaton-palisades-fires-analysis/
│
├── README.md
├── notebooks/
│   ├── false-color-analysis.ipynb           # Landsat 8 false color visualization
│   └── environmental-justice-analysis.ipynb # EJI analysis
├── .gitignore
└── data/                                    # See Data section below
```

## Data

### Data Sources

**Landsat 8 Surface Reflectance Data**

Atmospherically corrected surface reflectance data from the Landsat 8 satellite, collected on February 23, 2025. This simplified dataset contains five spectral bands (red, green, blue, near-infrared, and shortwave infrared) from the Landsat Collection 2 Level-2 product. The data was retrieved from the Microsoft Planetary Computer data catalogue and clipped to an area surrounding the Eaton and Palisades fire perimeters.

**Eaton and Palisades Fire Perimeter Data**

Dissolved fire perimeter shapefiles for the Eaton Fire and Palisades Fire that burned in Los Angeles County in January 2025. These ESRI shapefiles delineate the spatial extent of the burned areas as of January 21, 2025, and are used to overlay fire boundaries on satellite imagery and to identify affected census tracts.

**Environmental Justice Index (EJI) Data**

The CDC/ATSDR Environmental Justice Index (2024) provides census tract-level data on environmental and socioeconomic factors for California. The dataset includes 174 variables covering demographic information, poverty statistics, housing characteristics, and environmental burden indicators. This analysis uses percentile rankings (EPL variables) to compare vulnerability across communities, where values of 0-1 represent percentile ranks from 0th to 100th percentile relative to all census tracts in the state.

### Data Access

**Landsat 8 Imagery:**

The Landsat data (`landsat8-2025-02-23-palisades-eaton.nc`) is **not included** in this repository due to file size. The data is available through the EDS 220 course shared Google Drive folder. Download the file and place it in a `data/` directory in your local repository before running the analysis notebooks.

**Fire Perimeter Shapefiles:**

The fire perimeter data is **not included** in this repository. Access the shapefiles from ArcGIS Hub:
- Palisades and Eaton Dissolved Fire Perimeters: https://hub.arcgis.com/maps/ad51845ea5fb4eb483bc2a7c38b2370c

Download the shapefiles and store them in the `data/` directory to run the analysis.

**Environmental Justice Index Data:**

The EJI data (`EJI_2024_California.gdb`) is **not included** in this repository due to file size. Download the California EJI dataset from:
- CDC/ATSDR Environmental Justice Index: https://atsdr.cdc.gov/place-health/php/eji/eji-data-download.html

Select the 2024 California geodatabase and place it in the `data/` directory.

**Note:** All three datasets must be downloaded separately and placed in a local `data/` directory to reproduce the analyses.

## Requirements

This analysis requires Python 3.x with the following packages:

- `xarray` - Multi-dimensional array handling and NetCDF file operations
- `rioxarray` - Geospatial raster data operations and CRS management
- `geopandas` - Vector geospatial data handling (shapefiles, geodatabases)
- `matplotlib` - Data visualization and plotting
- `pandas` - Data manipulation and analysis
- `numpy` - Numerical operations

## Highlights

**False Color Analysis:**
- Uses SWIR/NIR/Red band combinations to highlight burn scars
- Demonstrates CRS management and reprojection between raster and vector data
- Creates multi-layer maps combining satellite imagery with vector boundaries

**Environmental Justice Analysis:**
- Applies spatial joins to identify census tracts within fire perimeters
- Uses clipping operations to focus on directly affected areas
- Compares socioeconomic vulnerability between the two fires
- Reveals disparate impacts on low-income communities

## Key Findings

The analysis reveals stark differences in socioeconomic vulnerability between the two fires:

- **Palisades Fire** primarily affected areas with lower proportions of economically vulnerable residents (10th-40th percentile rankings)
- **Eaton Fire** disproportionately impacted communities with higher economic vulnerability (50th-90th percentile rankings), particularly in Altadena

These findings underscore the unequal distribution of climate disaster impacts and the importance of targeting recovery resources to vulnerable populations.

## References

Bennett, M. M., Chen, J. K., Alvarez León, L. F., & Gleason, C. J. (2022). The politics of pixels: A review and agenda for critical remote sensing. *Progress in Human Geography*, *46*(3), 729–752. https://doi.org/10.1177/03091325221074691

Centers for Disease Control and Prevention, & Agency for Toxic Substances and Disease Registry. (2024). *Environmental Justice Index* [Dataset]. https://atsdr.cdc.gov/place-health/php/eji/eji-data-download.html

Galaz García, C., Cawse-Nicholson, K., Frew, A., & Fontenot, R. (2024). *EDS 220: Working with environmental datasets* [Course materials]. Master of Environmental Data Science, Bren School of Environmental Science & Management, University of California, Santa Barbara. https://meds-eds-220.github.io/MEDS-eds-220-course/

NASA Earth Observatory. (n.d.). *Why is that forest red and that cloud blue? How to interpret a false-color satellite image*. https://earthobservatory.nasa.gov/features/FalseColor

Palisades and Eaton Dissolved Fire Perimeters. (2025). *Fire perimeter shapefiles* [Geospatial dataset]. ArcGIS Hub. https://hub.arcgis.com/maps/ad51845ea5fb4eb483bc2a7c38b2370c

U.S. Geological Survey. (2025). *Landsat 8 Collection 2 Level-2 surface reflectance data* [Satellite imagery dataset]. Microsoft Planetary Computer. https://planetarycomputer.microsoft.com/dataset/landsat-c2-l2

## License

This project is licensed under the terms included in the LICENSE file.

---

*This project is part of the curriculum for the Master of Environmental Data Science program at the Bren School of Environmental Science & Management, UC Santa Barbara.*