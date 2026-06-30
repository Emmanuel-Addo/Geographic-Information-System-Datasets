# Ghana Geographic Information System (GIS) Datasets

A curated repository of spatial and demographic datasets of Ghana, tailored for **geography students**, spatial analysts, and GIS researchers. These datasets are ready to be used in academic projects, spatial analysis tasks, cartographic designs, and statistical modeling.

They are fully compatible with major GIS software suites, including **ArcGIS Pro / ArcMap**, **QGIS**, **ENVI**, and programming environments like **Python** and **R**.

---

## 📂 Dataset Catalog

This repository contains a wide range of spatial vector layers (points, lines, polygons), remote sensing rasters, and tabular datasets. Below is a detailed breakdown of the directories:

### 1. Administrative Boundaries (Regions & Districts)
* **Ghana Regions (16 Regions):**
  * **Location:** `GHANA REGIONS 16/`
  * **Format:** ESRI Shapefile (`GHnew16_regions.shp`) & Zip Archive (`GHnew16_regions z.zip`)
  * **Description:** Updated boundaries representing the 16 administrative regions of Ghana (established after the 2018/2019 regional restructuring). Excellent for macro-level regional mapping.
* **Ghana Districts (260 Districts):**
  * **Location:** `new ghana districts shps/`
  * **Format:** ESRI Shapefile (`Ghana_New_260_District.shp`)
  * **Description:** Modern boundary dataset representing the 260 administrative districts of Ghana. Perfect for high-resolution district-level statistics.
* **Ghana Districts (170 Districts):**
  * **Location:** `Districts 170/Districts 170/`
  * **Format:** ESRI Shapefile (`Ghana_Districts_170.shp`)
  * **Description:** Historical administrative boundaries of the 170 districts of Ghana. Useful for longitudinal studies comparing historical census data with modern structures.
* **Greater Accra Metropolitan Area (GAMA) Boundary:**
  * **Location:** `GAMA/` & `Data/Data/GAMA Boundary/`
  * **Format:** ESRI Shapefile (`GAMA.shp` / `GAMA_BOUNDARY.shp`), Google Earth KMZ (`GAMA.kmz`), and Zip (`GAMA.zip`)
  * **Description:** Spatial boundary for the capital region (GAMA), ideal for urban growth studies, local planning, and infrastructure planning.

### 2. Infrastructure & Infrastructure Networks
* **Ghana Roads Network:**
  * **Location:** `Ghana_Roads/`
  * **Format:** ESRI Shapefile (`Ghana_roads.shp`)
  * **Description:** Comprehensive national and regional road network linear dataset.
  * **Common Use Cases:** Network Analysis (routing, finding shortest path), transportation geography, and market accessibility modeling.
* **Ghana Settlements:**
  * **Location:** `Ghana_Settlements/`
  * **Format:** ESRI Shapefile (`Ghana_settlements.shp`)
  * **Description:** Vector representation of towns, villages, and human settlements throughout Ghana.
  * **Common Use Cases:** Spatial distribution of urban vs. rural centers, nearest-neighbor analysis, and demographic clustering.

### 3. Fieldwork Data 2025 (`Fieldwork_data_2025/`)
A collection of spatial layers mapped during local fieldwork exercises in 2025, perfect for local spatial pattern analysis and urban mapping.
* **Educational Facilities (`educational_facility.shp`):** Points/polygons representing schools, colleges, and educational institutes.
* **Filling Stations (`filling_station.shp`):** Locations of gas/refueling stations.
* **Health Facilities (`health_facility.shp`):** Local community clinics and healthcare facilities.
* **Mechanic Shops (`mechanic_shop.shp`):** Vehicle repair and mechanical shops.

### 4. Health & Service Facilities
* **OSM Health Facilities (2026):**
  * **Location:** `hotosm_gha_health_facilities_points_shp/`
  * **Format:** ESRI Shapefile (`hotosm_gha_health_facilities_points_shp.shp`)
  * **Description:** Exported from OpenStreetMap using the Humanitarian OpenStreetMap Team (HOT) raw data API (as of January 1, 2026).
  * **Common Use Cases:** Public health mapping, comparing community-sourced data against government datasets, and global health research.
* **Service Facilities Survey:**
  * **Location:** `Service_facilities/`
  * **Format:** ESRI Shapefile (`survey.shp`)
  * **Description:** Point survey data representing various community and retail services.

### 5. Spatial Statistics, Climate & Socioeconomics
* **Climate Centroid Points (`msc_spatialStatsData/climate_points.shp`):**
  * **Key Fields:** Monthly average precipitation (`prec_jan`, `prec_feb`, etc.) and temperature (`temp_jan`, `temp_feb`, etc.).
  * **Use:** Climate change modeling, interpolating continuous raster surfaces (using IDW or Kriging), and agricultural suitability planning.
* **Poverty Headcount Index (`msc_spatialStatsData/povertyheadcount_2014.shp`):**
  * **Description:** Socioeconomic vector dataset representing spatial inequality and poverty rates across Ghana (2014 data).
* **Savannah Accelerated Development Authority (SADA) Health Facilities (`msc_spatialStatsData/sada_Health_facilities.shp`):**
  * **Description:** Focuses on the northern and central regions of Ghana to analyze accessibility to healthcare.
* **Ghana Population (`population/Ghana-Population.shp`):**
  * **Description:** Spatial census distribution maps, useful for density mapping, choropleths, and calculating population per administrative district.

### 6. Remote Sensing & Tabular Data (`Data/Data/`)
* **Land Use Land Cover (LULC) Change (`LULC_Change.tif`):**
  * **Format:** GeoTIFF (Raster)
  * **Description:** Land use and land cover change raster map. Essential for environmental studies, remote sensing classifications, deforestation analysis, and change detection.
* **Major Cities Catalog (`Major_Cities.csv`):**
  * **Format:** Tabular CSV
  * **Description:** A comma-separated values database containing major city coordinates, names, and attribute details. Perfect for plotting coordinate points or joining with non-spatial tables.

---

## 🛠️ How to Load and Use the Datasets

### 1. In QGIS (Quantum GIS)
QGIS is a free and open-source desktop GIS application.
1. Open QGIS.
2. Go to the menu: `Layer` -> `Add Layer` -> `Add Vector Layer...`.
3. In the Source block, ensure the source type is set to **File**. Click the **`...`** browse button.
4. Navigate to the dataset folder (e.g., `population/`) and select the file ending with the `.shp` extension (e.g., `Ghana-Population.shp`). Click **Open** and then **Add**.
5. *Note:* QGIS will automatically parse the `.qmd` metadata file associated with the layer (such as the one found in the `population` directory) to render style and dataset information.

### 2. In ArcGIS (Pro or ArcMap)
ArcGIS is ESRI's industry-standard GIS platform.
1. Open your map project.
2. Under the **Map** tab, click **Add Data**.
3. Browse to the directory containing the files (e.g., `Districts 170/Districts 170/`).
4. Select the `.shp` file (e.g., `Ghana_Districts_170.shp`) and click **OK** to load it onto your canvas.
5. Right-click the layer in the *Contents* pane and select **Attribute Table** to examine the attributes (like GID codes, names, or population counts).

### 3. In ENVI
ENVI is primarily used for remote sensing and raster analysis, but handles vector overlays seamlessly.
1. Launch ENVI.
2. Select `File` -> `Open` from the main menu.
3. Choose a `.shp` vector file or raster `.tif` file (e.g., `LULC_Change.tif`).
4. The vector layer will appear in your **Layer Manager** and can be overlaid on top of multi-band rasters to outline administrative zones or fieldwork points.

### 4. Using Python (Jupyter Notebook / VS Code)
For modern geospatial data science, Python provides lightweight and powerful tools. Ensure you have `geopandas` and `rasterio` installed:
```bash
pip install geopandas rasterio matplotlib
```

Use the following snippet to load and plot a shapefile:
```python
import geopandas as gpd
import matplotlib.pyplot as plt

# Path to the shapefile
shapefile_path = "population/Ghana-Population.shp"

# Read the dataset
gdf = gpd.read_file(shapefile_path)

# View the attribute columns and first few rows
print(gdf.head())

# Project to UTM 30N if needed for distance calculations
# gdf = gdf.to_crs(epsg=32630)

# Quick visualization
gdf.plot(cmap="viridis")
plt.title("Ghana Population Spatial Distribution")
plt.show()
```

### 5. Using R
For statistical analysis of GIS datasets, R is highly recommended using the `sf` library:
```R
# Install and load the spatial features package
install.packages("sf")
library(sf)

# Read shapefile
ghana_districts <- st_read("new ghana districts shps/Ghana_New_260_District.shp")

# Plot the administrative boundaries
plot(st_geometry(ghana_districts), col = "lightblue", border = "darkgray")
```

---

## 💡 Important GIS Concepts & Best Practices

* **Keep Shapefile Components Together:** An ESRI Shapefile is not a single file, but a collection of multiple files with different extensions. For any dataset (e.g. `Ghana-Population`), you **must** keep all files with that name in the same folder.
  * `.shp`: Stores the feature geometry (polygons, lines, or points).
  * `.dbf`: Stores the attribute table database.
  * `.shx`: Index file linking geometry to attributes.
  * `.prj`: Stores the Coordinate Reference System (CRS) projection information (Without this, GIS software won't know where to position the data on Earth).
  * `.cpg`: Character encoding file (usually UTF-8).
* **Coordinate Systems (CRS):**
  * Geographic CRS (like `GCS_WGS_1984` or `EPSG:4326`) uses degrees as units. Great for global plotting, but not for calculating area (sq km) or distances (meters).
  * Projected CRS (like `WGS 84 / UTM zone 30N` or `EPSG:32630`) represents the curved Earth on a flat 2D plane. It uses meters as units. **Always use this projection when calculating density, distances, buffer zones, or areas in Ghana.**
* **Temporary Lock Files (`.lock`):**
  * You may see files ending with `.lock` (e.g., `Ghana-Population.shp.DESKTOP-xxxx.sr.lock`) in the directories. These are temporary lock files created by ArcGIS, QGIS, or other GIS software currently accessing the dataset to prevent editing conflicts. They are automatically deleted when the GIS software is closed.
