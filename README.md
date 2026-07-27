# Python-for-raster-handling-in-SQL
Using SQL with Python for raster processing
# NOAA GRIB to PostGIS Raster: Python Workflow

## Overview

This project demonstrates a Python-based workflow for processing NOAA weather GRIB data, converting it into a geospatial raster format, storing it in PostgreSQL/PostGIS Raster, and visualizing the resulting raster tiles.

The workflow integrates raster processing, spatial database management, and web-based visualization using open-source geospatial tools.

This work is inspired by the PostGIS Raster demonstrations by Paul Ramsey and the Crunchy Data team. This repository provides a Python-focused implementation adapted for weather raster processing and visualization.

---

## Dataset

The workflow uses the NOAA National Weather Service National Digital Forecast Database (NDFD) Probability of Precipitation dataset.

**Dataset details:**

- Product: `ds.pop12.bin`
- Format: GRIB
- Variable: 12-hour Probability of Precipitation
- Spatial coverage: CONUS
- Projection: NOAA Lambert Conformal Conic

The dataset is accessed directly from NOAA using GDAL virtual file system capabilities without requiring manual downloads. The data has been displayed below.

![Precipitation Animation](outputs/pop12_bands.gif)

---

## Workflow

The workflow consists of:

1. Accessing NOAA GRIB data using GDAL/rioxarray
2. Preserving the native NOAA Lambert Conformal Conic projection
3. Handling raster NoData values correctly
4. Exporting the processed raster as GeoTIFF
5. Loading the raster into PostgreSQL/PostGIS Raster
6. Creating raster tiles and spatial indexes
7. Querying and validating raster tiles using SQL
8. Visualizing raster tile footprints using Folium
9. Creating raster band animations for visual inspection

---

## PostGIS Raster Implementation

The raster is stored in PostGIS using tiled raster storage.

Key features:

- Raster tiling for efficient storage and querying
- Spatial indexing for faster spatial operations
- Raster metadata constraints
- SQL-based raster validation

A custom spatial reference identifier (SRID 99000) is used to represent the NOAA Lambert Conformal Conic projection because the dataset uses a spherical Earth model rather than a standard WGS84 datum.

---

## Outputs

### Raster Tile Visualization

The PostGIS raster tiles were queried and transformed for visualization in a web map environment.

The interactive Folium map displays the spatial organization of the raster tiles stored in PostGIS.

Interactive output:

[Tile Footprint Visualization](outputs/tile_footprints_pop121.html)
