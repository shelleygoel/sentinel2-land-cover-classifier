# Objective
Develop a multi-class land classifier with 80% accuracy (balanced accuracy score).

- Research papers on land cover classification using sentinel-2 and Random forests reach 80-90% accuracy

# Data Wrangling
## Sentinel-2 
- All 12 Raw Bands (B0-B9, B11, B12, B8A)
- Composite mean during summer months obtained using Google Earth Engine Python API
- Vegetation and other auxilliary indices coming soon
- code in `download_sentinel_from_gee.ipynb`

## Land Cover Labels

[NRCAN 2015 dataset](https://open.canada.ca/data/en/dataset/4e615eae-b90c-420b-adee-2ca35896caf6)

To reduce the amount of training data:
- Few(10-12) locations according to land cover diversity are sampled in QGIS to create areas of interest(AOIs) (`data/geoms/lc_geo_coords.json` and `data/geoms/lc_sample_polygons.json`) using QGIS
- These geometries are further resampled using `rasterio` and `geopandas` to  512x512 pixel each. 
Because original AOIs were too big which resulted in huge sentinel-2 GeoTIFF size.
- sampling code is in `aoi_geoms.ipynb` 



# Modeling

## Baseline Model

