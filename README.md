# Landscape Coffee Yield
Exploring the vast landscape of my PhD research journey, where the cultivation of knowledge meets the art of yielding impactful insights. Navigating the complexities with precision, much like the delicate process of growing the perfect blend. Join me in this academic odyssey where innovation and yield converge, shaping a landscape of discovery. 


![Coffee and Code](https://live.staticflickr.com/65535/50982571191_602f5b148c_k.jpg)

# Description 

This repository contains all scripts and workflows for the analysis landscape.

Here is the workflow for analysis:

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

Based on the plot analysis, the MODIS is suitable for this case. For this we have the following options:


1. **LC_Type1 (Annual IGBP classification):**
   - Classes include various types of forests, shrublands, grasslands, wetlands, croplands, urban areas, and more.
   - Each class has a specific color, and you can choose the one that aligns with the land cover type you are interested in.

2. **LC_Type2 (Annual UMD classification):**
   - Similar to LC_Type1, but with different class definitions and colors.

3. **LC_Type3 (Annual Leaf Area Index classification):**
   - Includes grasslands, shrublands, croplands, forests, wetlands, and urban areas.

4. **LC_Type4 (Annual BIOME-BGC classification):**
   - Differentiates between vegetation types, croplands, and non-vegetated lands.

5. **LC_Type5 (Annual Plant Functional Types classification):**
   - Represents different types of vegetation, including trees, shrubs, grasses, and croplands.


Ahi que quitar esto:

| Value | Color   | Color Value | 
|-------|---------|-------------|
| 1     | Saturated or defective | ![#ff0000](https://via.placeholder.com/15/ff0000/000000?text=+) |
| 2     | Dark Area Pixels | ![#404040](https://via.placeholder.com/15/404040/000000?text=+) |
| 3     | Cloud Shadows | ![#8b4513](https://via.placeholder.com/15/8b4513/000000?text=+) |
| 4     | Vegetation | ![#008000](https://via.placeholder.com/15/008000/000000?text=+) |
| 5     | Bare Soils | ![#ffd700](https://via.placeholder.com/15/ffd700/000000?text=+) |
| 6     | Water | ![#0000ff](https://via.placeholder.com/15/0000ff/000000?text=+) |
| 7     | Clouds Low Probability / Unclassified | ![#808080](https://via.placeholder.com/15/808080/000000?text=+) |
| 8     | Clouds Medium Probability | ![#a9a9a9](https://via.placeholder.com/15/a9a9a9/000000?text=+) |
| 9     | Clouds High Probability | ![#d3d3d3](https://via.placeholder.com/15/d3d3d3/000000?text=+) |
| 10    | Cirrus | ![#add8e6](https://via.placeholder.com/15/add8e6/000000?text=+) |
| 11    | Snow / Ice | ![#87ceeb](https://via.placeholder.com/15/87ceeb/000000?text=+) |

There is a parameter to measure the amount of clouds,CLOUDY_PIXEL_PERCENTAGE = 10% (only 2 images for Quindio that meet with this condition and 16 min for downloading), in the zone. In this case, the umbral is 100%, which means that the zone is basically covered by clouds. In Quindio department, they surveys were collected between July and November 2022. 

The bands are ['B4', 'B3', 'B2']. According to chatGPT,  Land Use and Land Cover (LULC) classification often involves using different combinations of spectral bands to distinguish between different land cover types. While true-color RGB imagery is useful for visualization, for LULC classification, you typically use bands that are sensitive to different land cover characteristics. 

For Sentinel-2, common band combinations used for LULC classification include:

Natural Color (RGB): Bands 4 (Red), 3 (Green), and 2 (Blue).
False Color Infrared (FCIR): Bands 8 (NIR), 4 (Red), and 3 (Green).
Normalized Difference Vegetation Index (NDVI): Bands 8 (NIR) and 4 (Red).




# References
https://www.youtube.com/watch?v=ReS6iN5alDE&ab_channel=StudyHacks-InstituteofGIS%26RemoteSensing

https://geoportal.dane.gov.co/servicios/descarga-y-metadatos/datos-geoestadisticos/

https://www.youtube.com/watch?v=K0DVIyLOlzI&ab_channel=MasterGIS

https://www.youtube.com/channel/UCqOIlsepzeVXdnndB6xtbWQ

https://www.flickr.com/photos/ciat/50982571191/in/album-72157718443664588/

https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_HARMONIZED

https://developers.google.com/earth-engine/datasets/catalog/MODIS_061_MCD12Q1





