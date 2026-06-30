# Ghana Geographic Information System (GIS) Datasets

A curated repository of spatial and demographic datasets of Ghana, tailored for **geography students**, spatial analysts, and GIS researchers. These datasets are ready to be used in academic projects, spatial analysis tasks, cartographic designs, and statistical modeling.

They are fully compatible with major GIS software suites, including **ArcGIS Pro / ArcMap**, **QGIS**, **ENVI**, and programming environments like **Python** and **R**.

---

## 📂 Dataset Catalog

### 1. Ghana Administrative Boundaries (170 Districts)
* **Location:** `Districts 170/Districts 170/`
* **Format:** ESRI Shapefile (`.shp`, `.shx`, `.dbf`, `.prj`, etc.)
* **Coordinate Reference System (CRS):** WGS 84 (Geographic) / UTM Zone 30N (Projected)
* **Description:** Administrative boundaries representing the 170 districts of Ghana (historically defined boundary layout).
* **Common Use Cases:**
  * Base mapping and regional zoning.
  * Spatial aggregation of socio-economic survey data.
  * Choropleth mapping (e.g., color-coding districts by specific development indicators).

### 2. Spatial Statistics & Socio-Environmental Data (`msc_spatialStatsData/`)
A collection of spatial layers specifically structured for statistical analysis, correlation modeling, and planning.

* **Climate Measurement Points (`climate_points.shp`):**
  * **Geometry:** Point (District Centroids / Meteorological stations)
  * **CRS:** GCS WGS 1984 (EPSG:4326)
  * **Key Fields/Attributes:**
    * `COUNTRY`, `NAME_1` (Region Name), `NAME_2` (District Name)
    * `prec_jan`, `prec_feb`, ... (Precipitation data in millimeters for specific months)
    * `temp_jan`, `temp_feb`, ... (Temperature data in degrees Celsius for specific months)
  * **Common Use Cases:** Interpolation of climatic surfaces (Kriging, IDW), agro-ecological zoning, and correlation analysis between climate and vegetation/poverty indices.
* **Poverty Headcount 2014 (`povertyheadcount_2014.shp`):**
  * **Geometry:** Polygon
  * **Description:** Socioeconomic vector layer representing the spatial distribution of the poverty headcount index across Ghana districts based on the 2014 census/survey estimates.
  * **Common Use Cases:** Spatial autocorrelation (Moran's I) to identify poverty hotspots, policy targeting mapping, and socio-economic profiling.
* **SADA Health Facilities (`sada_Health_facilities.shp`):**
  * **Geometry:** Point
  * **Description:** Comprehensive geographic database of primary, secondary, and tertiary health facilities within the **Savannah Accelerated Development Authority (SADA)** zone of Northern/Central Ghana.
  * **Common Use Cases:** Healthcare accessibility analysis, service area buffering, nearest-neighbor analysis, and allocation optimization for new clinics.

### 3. Demographic & Population Data (`population/`)
* **Location:** `population/`
* **Format:** ESRI Shapefile (`Ghana-Population.shp`)
* **CRS:** WGS 84 / UTM Zone 30N (EPSG:32630)
* **Description:** Geo-referenced demographic layer mapping population counts and related indicators across statistical zones or administrative sub-divisions in Ghana.
* **Common Use Cases:** Population density calculation (using the projected UTM units for accurate land area calculation), choropleth mapping, and resource allocation modeling.

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
3. Choose the `.shp` file you wish to import.
4. The vector layer will appear in your **Layer Manager**. You can drag it on top of your multispectral imagery (e.g., Landsat, Sentinel-2, or radar data) to outline administrative areas or highlight specific coordinates (like SADA health facilities).

### 4. Using Python (Jupyter Notebook / VS Code)
For modern geospatial data science, Python provides lightweight and powerful tools. Ensure you have `geopandas` installed:
```bash
pip install geopandas matplotlib
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
ghana_districts <- st_read("Districts 170/Districts 170/Ghana_Districts_170.shp")

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
