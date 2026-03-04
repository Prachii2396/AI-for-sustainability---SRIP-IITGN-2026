# 🌍 AI for Sustainability — SRIP IITGN 2026

> End-to-end Earth Observation pipeline developed during SRIP at IIT Gandhinagar.  
Implements spatial gridding, satellite image filtering, land-cover label extraction from ESA WorldCover 2021, and CNN-based land-use classification over the Delhi Airshed using Sentinel-2 imagery.

---

## 📌 Project Overview

This project builds a complete geospatial AI pipeline for auditing the Delhi Airshed using satellite imagery and raster land-cover data. (THE PROJECT IS STILL IN PROGRESS AND  WILL BE COMPLETED BY 15 MARCH)

The system integrates:
- 🗺️ Geospatial processing  
- 🛰️ Satellite image filtering  
- 🏷️ Land-cover label extraction  
- 🧠 CNN-based supervised classification  

**Objective:** Identify land-use patterns relevant to environmental monitoring and pollution analysis.

---

## 🛰️ Datasets Used

- Delhi-NCR Shapefile (EPSG:4326)  
- Delhi-Airshed Shapefile (EPSG:4326)  
- Sentinel-2 RGB patches (128×128 pixels, 10m resolution)  
- ESA WorldCover 2021 (land_cover.tif, 10m resolution)  

**Gridding CRS:** EPSG:32644  

---

# 🧠 Q1. Spatial Reasoning & Data Filtering (4 Marks)

## 🔹 Q1.1 Plot Delhi-NCR & Overlay 60×60 km Grid (2 Marks)

**Approach:**
- Loaded shapefile using GeoPandas  
- Reprojected to EPSG:32644 for accurate distance-based gridding  
- Generated uniform 60 km × 60 km grid  
- Visualized overlay using Matplotlib  

## 🔹 Q1.2 Filter Satellite Images Inside Region (1 Mark)

**Approach:**
- Extracted center coordinates from filenames  
- Converted to Point geometries  
- Applied spatial containment check using `.within()`  
- Filtered valid images  

## 🔹 Q1.3 Report Image Counts (1 Mark)

**Approach:**
- Counted total images before filtering  
- Counted images after filtering  
- Reported comparison  

---

# 🧠 Q2. Label Construction & Dataset Preparation (6 Marks)

## 🔹 Q2.1 Extract 128×128 Land-Cover Patch (2 Marks)

**Approach:**
- Loaded land_cover.tif using Rasterio  
- Converted coordinates to raster indices  
- Extracted 128×128 window  
- Ensured 10m resolution alignment  

## 🔹 Q2.2 Assign Dominant Land-Cover Class (1 Mark)

**Approach:**
- Flattened raster patch  
- Computed statistical mode  
- Assigned dominant ESA class  

## 🔹 Q2.3 Map ESA Classes to Simplified Categories (1 Mark)

**Mapping:**

| ESA Code | Category   |
|----------|-----------|
| 50       | Built-up  |
| 10, 20   | Vegetation|
| 40       | Cropland  |
| 80       | Water     |
| Others   | Misc      |

## 🔹 Q2.4 Train-Test Split & Class Distribution (2 Marks)

**Approach:**
- 60/40 random split using sklearn  
- Visualized class distribution  
- Checked class imbalance  

---

# 🧠 Q3. Model Training & Evaluation (5 Marks)

## 🔹 Q3.1 CNN Training (2 Marks)

**Approach:**
- Implemented ResNet18 / Custom CNN  
- Input: 128×128 RGB patches  
- Cross-Entropy Loss  
- Adam Optimizer  

## 🔹 Q3.2 Evaluation Metrics (2 Marks)

**Approach:**
- Accuracy  
- Weighted F1-score  
- Test set evaluation  

## 🔹 Q3.3 Confusion Matrix & Interpretation (1 Mark)

**Approach:**
- Generated confusion matrix  
- Visualized via heatmap  
- Interpreted misclassification trends  

---

# 🛠️ Tech Stack

Python • GeoPandas • Rasterio • Shapely • NumPy • Pandas • Matplotlib • PyTorch / TensorFlow • Scikit-learn • geemap  

---

# 📊 Key Contributions

✔ Designed full geospatial processing pipeline  
✔ Implemented raster-vector alignment  
✔ Automated dominant-class label extraction  
✔ Built CNN land-use classifier  
✔ Evaluated using robust ML metrics  
