# Landscape Coffee Yield
Exploring the vast landscape of my PhD research journey, where the cultivation of knowledge meets the art of yielding impactful insights. Navigating the complexities with precision, much like the delicate process of growing the perfect blend. Join me in this academic odyssey where innovation and yield converge, shaping a landscape of discovery. 


![Coffee and Code](https://live.staticflickr.com/65535/50982571191_602f5b148c_k.jpg)

# Description 

This repository contains all scripts and workflows for the analysis landscape.

Here is the workflow for analysis:
## Data
1.  Download land use and land cover (LULC) https://code.earthengine.google.com/b99f1904c7a5c5902fa17608e8a08e32 analysis data with Google Earth. Options for downloading this information:

| Satellite        | Spatial Resolution | Revisit Time  | General Description |
|------------------|--------------------|---------------|----------------------|
| Landsat 8        | 30m (visible and IR), 15m (panchromatic) | 16 days | Free (USGS), operated by NASA/USGS |
| Sentinel-2       | 10m (visible and NIR), 20m (red-edge), 60m (SWIR) | 5 days | Free (ESA), operated by ESA |
| MODIS            | 250m (bands 1-2), 500m (bands 3-7), 1km (bands 8-36) | Daily (Terra and Aqua) | Free (NASA), operated by NASA |
| WorldView-2      | 46cm (panchromatic), 1.8m (multispectral) | Varies, typically several days | Commercial (DigitalGlobe), operated by Maxar Technologies |
| WorldView-3      | 31cm (panchromatic), 1.24m (multispectral) | Varies, typically several days | Commercial (DigitalGlobe), operated by Maxar Technologies |

For (LULC), we have

| Dataset               | Satellite             | Resolution | Description |
|-----------------------|-----------------------|------------|-------------|
| Dynamic World         | Sentinel-2            | 10m        | Near-real-time (NRT) Land Use/Land Cover (LULC) dataset. Includes class probabilities and label information for nine classes. |
| MCD12Q1.061           | MODIS Terra and Aqua  | 500m       | MODIS Land Cover Type Yearly Global dataset at 500m resolution. |

Based on the plot analysis, the **MODIS** is suitable for this case. For this we have the following options:


 **LC_Type1 (Annual IGBP classification):**
   - Classes include various types of forests, shrublands, grasslands, wetlands, croplands, urban areas, and more.
   - Each class has a specific color, and you can choose the one that aligns with the land cover type you are interested in.

 **LC_Type2 (Annual UMD classification):**
   - Similar to LC_Type1, but with different class definitions and colors.

 **LC_Type3 (Annual Leaf Area Index classification):**
   - Includes grasslands, shrublands, croplands, forests, wetlands, and urban areas.

 **LC_Type4 (Annual BIOME-BGC classification):**
   - Differentiates between vegetation types, croplands, and non-vegetated lands.

 **LC_Type5 (Annual Plant Functional Types classification):**
   - Represents different types of vegetation, including trees, shrubs, grasses, and croplands.

The IGBP (International Geosphere-Biosphere Programme) classification is a system used to categorize land cover types based on their characteristics. It was developed by the IGBP, an international scientific research program that aimed to study global-scale interactions between Earth's biological, chemical, and physical processes.

The IGBP land cover classification system categorizes different types of land cover, including natural vegetation, agricultural areas, urban areas, and more. Each land cover type is assigned a specific class code and label. This classification system has been widely used in remote sensing and environmental research to characterize and analyze the Earth's surface.

The classes in the IGBP classification system cover a broad range of land cover types, providing a comprehensive framework for understanding the distribution of different ecosystems and land uses on a global scale. For example, classes may include evergreen forests, deciduous forests, shrublands, grasslands, croplands, wetlands, and urban areas.

Researchers and scientists use the IGBP classification to interpret satellite imagery, conduct land cover change analysis, and understand the distribution of different land cover types across regions and continents. The classification system is a valuable tool for studying and monitoring the dynamics of the Earth's surface and its changes over time.



| Value | Color | Description |
|-------|-------|-------------|
| 1     | ![#05450a](https://via.placeholder.com/15/05450a/000000?text=+) | Evergreen Needleleaf Forests: dominated by evergreen conifer trees (canopy >2m). Tree cover >60%. |
| 2     | ![#086a10](https://via.placeholder.com/15/086a10/000000?text=+) | Evergreen Broadleaf Forests: dominated by evergreen broadleaf and palmate trees (canopy >2m). Tree cover >60%. |
| 3     | ![#54a708](https://via.placeholder.com/15/54a708/000000?text=+) | Deciduous Needleleaf Forests: dominated by deciduous needleleaf (larch) trees (canopy >2m). Tree cover >60%. |
| 4     | ![#78d203](https://via.placeholder.com/15/78d203/000000?text=+) | Deciduous Broadleaf Forests: dominated by deciduous broadleaf trees (canopy >2m). Tree cover >60%. |
| 5     | ![#009900](https://via.placeholder.com/15/009900/000000?text=+) | Mixed Forests: dominated by neither deciduous nor evergreen (40-60% of each) tree type (canopy >2m). Tree cover >60%. |
| 6     | ![#c6b044](https://via.placeholder.com/15/c6b044/000000?text=+) | Closed Shrublands: dominated by woody perennials (1-2m height) >60% cover. |
| 7     | ![#dcd159](https://via.placeholder.com/15/dcd159/000000?text=+) | Open Shrublands: dominated by woody perennials (1-2m height) 10-60% cover. |
| 8     | ![#dade48](https://via.placeholder.com/15/dade48/000000?text=+) | Woody Savannas: tree cover 30-60% (canopy >2m). |
| 9     | ![#fbff13](https://via.placeholder.com/15/fbff13/000000?text=+) | Savannas: tree cover 10-30% (canopy >2m). |
| 10    | ![#b6ff05](https://via.placeholder.com/15/b6ff05/000000?text=+) | Grasslands: dominated by herbaceous annuals (<2m). |
| 11    | ![#27ff87](https://via.placeholder.com/15/27ff87/000000?text=+) | Permanent Wetlands: permanently inundated lands with 30-60% water cover and >10% vegetated cover. |
| 12    | ![#c24f44](https://via.placeholder.com/15/c24f44/000000?text=+) | Croplands: at least 60% of area is cultivated cropland. |
| 13    | ![#a5a5a5](https://via.placeholder.com/15/a5a5a5/000000?text=+) | Urban and Built-up Lands: at least 30% impervious surface area including building materials, asphalt and vehicles. |
| 14    | ![#ff6d4c](https://via.placeholder.com/15/ff6d4c/000000?text=+) | Cropland/Natural Vegetation Mosaics: mosaics of small-scale cultivation 40-60% with natural tree, shrub, or herbaceous vegetation. |
| 15    | ![#69fff8](https://via.placeholder.com/15/69fff8/000000?text=+) | Permanent Snow and Ice: at least 60% of area is covered by snow and ice for at least 10 months of the year. |
| 16    | ![#f9ffa4](https://via.placeholder.com/15/f9ffa4/000000?text=+) | Barren: at least 60% of area is non-vegetated barren (sand, rock, soil) areas with less than 10% vegetation. |
| 17    | ![#1c0dff](https://via.placeholder.com/15/1c0dff/000000?text=+) | Water Bodies: at least 60% of area is covered by permanent water bodies. |





There is a parameter to measure the amount of clouds,CLOUDY_PIXEL_PERCENTAGE = 10% (only 2 images for Quindio that meet with this condition and 16 min for downloading), in the zone. In this case, the umbral is 100%, which means that the zone is basically covered by clouds. In Quindio department, they surveys were collected between July and November 2022. 

The bands are ['B4', 'B3', 'B2']. According to chatGPT,  Land Use and Land Cover (LULC) classification often involves using different combinations of spectral bands to distinguish between different land cover types. While true-color RGB imagery is useful for visualization, for LULC classification, you typically use bands that are sensitive to different land cover characteristics. 

For Sentinel-2, common band combinations used for LULC classification include:

Natural Color (RGB): Bands 4 (Red), 3 (Green), and 2 (Blue).
False Color Infrared (FCIR): Bands 8 (NIR), 4 (Red), and 3 (Green).
Normalized Difference Vegetation Index (NDVI): Bands 8 (NIR) and 4 (Red).



I apologize for any confusion in my previous messages. It seems there might have been some misunderstanding. The "Reproject layer" tool is not available directly in the Processing Toolbox by default. Instead, you can use the "Reproject" tool from the main QGIS menu. Here's how you can access it:


###  Create Buffers Around Points:
Use the "Buffer" Tool:

Go to the "Vector" menu.
Select "Geoprocessing Tools" > "Buffer."
Configure Buffer Parameters:

In the Buffer dialog:
Select your points layer as the "Input layer."
Specify the buffer distance (e.g., 500 meters).
Choose an appropriate buffer unit (e.g., meters or kilometers).
Specify an output location and file name for the new buffer layer.
Click "Run" to create the buffers.
Adjust Buffer Settings (Optional):


### Reprojecting Data to a Projected CRS:

1. **Identify Current CRS:**
   - Right-click on your layer in the Layers Panel.
   - Select "Properties."
   - Go to the "Source" tab to see the current CRS.

2. **Access the "Reproject" Tool:**
   - In the main QGIS menu, go to "Vector."
   - Select "Data Management Tools" > "Reproject Layer."

3. **Configure Reprojection Settings:**
   - Select your layer as the "Input layer."
   - Choose the target CRS that uses meters EPSG Code: EPSG:32618
   - Specify an output location and file name for the reprojected layer geopackage.

4. **Run the Tool:**
   - Click "Run" to execute the tool.

5. **Check the Result:**
   - Once the tool completes, add the reprojected layer to your map and check its properties to ensure it now uses a projected CRS.

### Hansen Global Forest Change v1.10 (2000-2022)

Results from time-series analysis of Landsat images in characterizing global forest extent and change.
The 'first' and 'last' bands are reference multispectral imagery from the first and last available years for Landsat spectral bands corresponding to red, NIR, SWIR1, and SWIR2. Reference composite imagery represents median observations from a set of quality-assessed growing-season observations for each of these bands.

Please see the User Notes for this Version 1.10 update, as well as the associated journal article: Hansen, Potapov, Moore, Hancher et al. "High-resolution global maps of 21st-century forest cover change." Science 342.6160 (2013): 850-853.

| Name          | Units | Min | Max | Wavelength | Description                                                                                               |
|---------------|-------|-----|-----|------------|-----------------------------------------------------------------------------------------------------------|
| treecover2000 | %     | 0   | 100 | -          | Tree canopy cover for the year 2000, defined as canopy closure for all vegetation taller than 5m in height. |
| loss          | -     | -   | -   | -          | Forest loss during the study period, defined as a stand-replacement disturbance.                            |




## Methods

Once we have the data and area, we proceed with metrics for landscape. We are using the package in R landscapemetrics. 

# References

https://www.gis-blog.com/increasing-the-speed-of-raster-processing-with-r-part-23-parallelisation/

https://developers.google.com/earth-engine/datasets/catalog/UMD_hansen_global_forest_change_2022_v1_10

https://developers.google.com/earth-engine/guides/exporting_images#setting_scale

https://datacarpentry.org/semester-biology/materials/spatial-data-cropping-R/

https://r-spatialecology.github.io/landscapemetrics/

https://geoportal.dane.gov.co/servicios/descarga-y-metadatos/datos-geoestadisticos/

https://www.youtube.com/watch?v=K0DVIyLOlzI&ab_channel=MasterGIS

https://www.youtube.com/channel/UCqOIlsepzeVXdnndB6xtbWQ

https://www.flickr.com/photos/ciat/50982571191/in/album-72157718443664588/

https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_HARMONIZED

https://developers.google.com/earth-engine/datasets/catalog/MODIS_061_MCD12Q1





