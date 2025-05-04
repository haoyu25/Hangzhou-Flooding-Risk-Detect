# 🌆 Assessing Urban Expansion and Inundation Risk in Hangzhou’s Central Districts
MUSA 6950: AI for Urban Sustainability -  Spring 2025 - Final Project

## 📖 Abstract
Urban flooding is an increasingly urgent challenge for rapidly urbanizing cities. This study proposes an integrated method that combines deep learning-based impervious surface extraction with terrain-based flood modeling to assess changes in inundation risk between 2018 and 2023 in Hangzhou’s core districts. Using Sentinel-2 imagery and a HAND (Height Above Nearest Drainage) model, we identified spatial-temporal patterns of expansion and risk to support sustainable urban planning.

## 🗺️ Study Area
This study focuses on Hangzhou’s central districts: Linping, Qiantang, Yuhang, Gongshu, Shangcheng, Xihu, Binjiang, and Xiaoshan.

![Study Area Map](figures/figure1_study_area.png)

## ⚙️ Methodology

### 1. Impervious Surface Extraction (UNet)
- Semantic segmentation with UNet model trained on SinoLC-1 dataset.
- Input bands: Sentinel-2 B03 (Green), B04 (Red), B08 (NIR), B11 (SWIR).
- Output classes: Impervious surface, pervious surface, nodata.

![UNet Prediction](figures/figure3_unet_results.png)

### 2. HAND-Based Inundation Mapping
- HAND derived from DEM using PySheds and Rasterio.
- Thresholds applied: 5m, 10m, 15m to simulate low to high flood risk areas.
- Adjusted using impervious surface and runoff coefficient assumptions.

![HAND Model](figures/figure6_hand_thresholds.png)

### 3. Hexagon-Based Spatial Aggregation
- Created 150 regular hexagons to summarize spatial indicators.
- Computed impervious surface %, mean/max HAND, and change rates.
- Classified risk into three levels: Extreme, Chronic, Low.

![Hex Grid Summary](figures/figure7_hex_overlay.png)

## 📊 Results

- **Urban Expansion**: Most significant in Yuhang and Xiaoshan.
- **Flood Risk Growth**: Areas with high impervious growth also show increased inundation exposure.
- **Hotspots**: Qiantang River corridor and western suburbs show clusters of "Extreme Risk".

![2018 vs 2023 Comparison](figures/figure8_risk_map_comparison.png)

## 💬 Discussion

- The approach demonstrates how remote sensing and DEM data can be integrated for urban flood risk mapping.
- Green infrastructure is urgently needed in fringe districts with low HAND and high impervious cover.
- Future applications may incorporate rainfall simulation and drainage capacity.

## ✅ Conclusion

> Land-use change is a significant flood risk driver.
> The integrated approach developed here enables scalable, data-driven planning support for risk-sensitive urban development.

## 🧰 Tools & Data Used

- **Satellite Imagery**: Sentinel-2 Level-2A
- **Elevation Data**: DEM from geospatial cloud platform
- **Deep Learning**: UNet (PyTorch)
- **Geospatial Libraries**: `rasterio`, `torch`, `geopandas`, `matplotlib`, `numpy`, `pandas`

## 📂 Folder Structure

