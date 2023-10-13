# Landscape Coffee Yield
Exploring the vast landscape of my PhD research journey, where the cultivation of knowledge meets the art of yielding impactful insights. Navigating the complexities with precision, much like the delicate process of growing the perfect blend. Join me in this academic odyssey where innovation and yield converge, shaping a landscape of discovery. 


![Coffee and Code](https://live.staticflickr.com/1025/4733927920_e4638cef18_4k.jpg)

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

The downloanding process was using Goolge Earth Engine with Sentinel-2 MSI: MultiSpectral Instrument, Level-2A.

| Band  | Description                       | Min  | Max  | Resolution | Units | Wavelength                                       | Scale  |
|-------|-----------------------------------|------|------|------------|-------|--------------------------------------------------|--------|
| B1    | Aerosols                          | -    | -    | 60 meters  | -     | 443.9nm (S2A) / 442.3nm (S2B)                   | 0.0001 |
| B2    | Blue                              | -    | -    | 10 meters  | -     | 496.6nm (S2A) / 492.1nm (S2B)                   | 0.0001 |
| B3    | Green                             | -    | -    | 10 meters  | -     | 560nm (S2A) / 559nm (S2B)                       | 0.0001 |
| B4    | Red                               | -    | -    | 10 meters  | -     | 664.5nm (S2A) / 665nm (S2B)                     | 0.0001 |
| B5    | Red Edge 1                        | -    | -    | 20 meters  | -     | 703.9nm (S2A) / 703.8nm (S2B)                   | 0.0001 |
| B6    | Red Edge 2                        | -    | -    | 20 meters  | -     | 740.2nm (S2A) / 739.1nm (S2B)                   | 0.0001 |
| B7    | Red Edge 3                        | -    | -    | 20 meters  | -     | 782.5nm (S2A) / 779.7nm (S2B)                   | 0.0001 |
| B8    | NIR                               | -    | -    | 10 meters  | -     | 835.1nm (S2A) / 833nm (S2B)                     | 0.0001 |
| B8A   | Red Edge 4                        | -    | -    | 20 meters  | -     | 864.8nm (S2A) / 864nm (S2B)                     | 0.0001 |
| B9    | Water Vapor                       | -    | -    | 60 meters  | -     | 945nm (S2A) / 943.2nm (S2B)                     | 0.0001 |
| B11   | SWIR 1                            | -    | -    | 20 meters  | -     | 1613.7nm (S2A) / 1610.4nm (S2B)                 | 0.0001 |
| B12   | SWIR 2                            | -    | -    | 20 meters  | -     | 2202.4nm (S2A) / 2185.7nm (S2B)                 | 0.0001 |
| AOT   | Aerosol Optical Thickness         | -    | -    | 10 meters  | -     | -                                                | 0.001  |
| WVP   | Water Vapor Pressure              | -    | -    | 10 meters  | cm    | -                                                | 0.001  |
| SCL   | Scene Classification Map          | 1    | 11   | 20 meters  | -     | -                                                | 0      |
| TCI_R | True Color Image, Red channel      | -    | -    | 10 meters  | -     | -                                                | 0      |
| TCI_G | True Color Image, Green channel    | -    | -    | 10 meters  | -     | -                                                | 0      |
| TCI_B | True Color Image, Blue channel     | -    | -    | 10 meters  | -     | -                                                | 0      |
| MSK_CLDPRB | Cloud Probability Map        | 0    | 100  | 20 meters  | -     | -                                                | 0      |
| MSK_SNWPRB | Snow Probability Map         | 0    | 100  | 10 meters  | -     | -                                                | 0      |
| QA10  | Always empty                      | -    | -    | 10 meters  | -     | -                                                | 0      |
| QA20  | Always empty                      | -    | -    | 20 meters  | -     | -                                                | 0      |
| QA60  | Cloud mask                        | -    | -    | 60 meters  | -     | -                                                | 0      |
| QA60 Bitmask | Bits 0-9: Unused           | -    | -    | -          | -     | -                                                | -      |
|              | Bit 10: Opaque clouds        | -    | -    | -          | -     | -                                                | -      |
|              | Bit 11: Cirrus clouds        | -    | -    | -          | -     | -                                                | -      |



| Value | Color   | Color Value | 
|-------|---------|-------------|
| 1     | Saturated or defective | <span style="background-color:#ff0000;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> |
| 2     | Dark Area Pixels | <span style="background-color:#404040;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> |
| 3     | Cloud Shadows | <span style="background-color:#8b4513;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> |
| 4     | Vegetation | <span style="background-color:#008000;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> |
| 5     | Bare Soils | <span style="background-color:#ffd700;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> |
| 6     | Water | <span style="background-color:#0000ff;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> |
| 7     | Clouds Low Probability / Unclassified | <span style="background-color:#808080;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> |
| 8     | Clouds Medium Probability | <span style="background-color:#a9a9a9;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> |
| 9     | Clouds High Probability | <span style="background-color:#d3d3d3;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> |
| 10    | Cirrus | <span style="background-color:#add8e6;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> |
| 11    | Snow / Ice | <span style="background-color:#87ceeb;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span> |



https://code.earthengine.google.com/b99f1904c7a5c5902fa17608e8a08e32

# References
https://www.youtube.com/watch?v=ReS6iN5alDE&ab_channel=StudyHacks-InstituteofGIS%26RemoteSensing




