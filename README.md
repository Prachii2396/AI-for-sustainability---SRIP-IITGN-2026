# AI-for-sustainability---SRIP-IITGN-2026
End-to-end Earth Observation pipeline built during SRIP at IIT Gandhinagar. Implements spatial gridding, satellite image filtering, land-cover label extraction from ESA WorldCover 2021, and CNN-based land-use classification over the Delhi Airshed using Sentinel-2 imagery.

📌 Project Overview

This project implements an end-to-end Earth Observation pipeline for AI-based auditing of the Delhi Airshed. The system integrates geospatial data processing, land-cover label extraction, and CNN-based supervised classification using Sentinel-2 imagery and ESA WorldCover 2021 data.

The objective is to identify land-use patterns relevant to environmental monitoring and pollution analysis.

🛰️ Datasets Used

Delhi-NCR Shapefile (EPSG:4326)

Delhi-Airshed Shapefile (EPSG:4326)

Sentinel-2 RGB patches (128×128 pixels, 10m resolution)

ESA WorldCover 2021 (land_cover.tif, 10m resolution)

Gridding CRS: EPSG:32644

🧠 Q1. Spatial Reasoning & Data Filtering (4 Marks)
🔹 Q1.1 Plot Delhi-NCR shapefile & overlay 60×60 km grid (2 Marks)

Approach:

Loaded shapefile using GeoPandas.

Reprojected data to EPSG:32644 (UTM) for accurate distance-based gridding.

Generated a uniform 60 km × 60 km grid using bounding box coordinates.

Overlaid grid on the region using Matplotlib for visualization.

🔹 Q1.2 Filter satellite images inside region (1 Mark)

Approach:

Extracted image center coordinates from filenames.

Converted coordinates to Point geometries.

Performed spatial containment check (within()) against Delhi-NCR polygon.

Filtered images whose centers fall inside the region.

🔹 Q1.3 Report image counts (1 Mark)

Approach:

Counted total images before filtering.

Counted valid images after spatial filtering.

Reported both numbers for comparison.

🧠 Q2. Label Construction & Dataset Preparation (6 Marks)
🔹 Q2.1 Extract 128×128 land-cover patch (2 Marks)

Approach:

Used Rasterio to read land_cover.tif.

Converted center coordinates to raster pixel indices.

Extracted corresponding 128×128 window.

Ensured alignment with Sentinel-2 resolution (10m/pixel).

🔹 Q2.2 Assign dominant land-cover class (1 Mark)

Approach:

Flattened extracted raster patch.

Computed statistical mode (most frequent pixel value).

Assigned image label based on dominant ESA class.

🔹 Q2.3 Map ESA classes to simplified categories (1 Mark)

Approach:
Created mapping dictionary:

ESA Code	Category
50	Built-up
10, 20	Vegetation
40	Cropland
80	Water
Others	Misc

Mapped raw class values to simplified land-use labels.

🔹 Q2.4 Train-Test Split & Class Distribution (2 Marks)

Approach:

Performed 60/40 random split using sklearn.

Visualized class distribution using bar plots.

Checked for class imbalance before model training.

🧠 Q3. Model Training & Evaluation (5 Marks)
🔹 Q3.1 CNN Training (2 Marks)

Approach:

Implemented CNN model (ResNet18 / Custom CNN).

Used RGB patches (128×128) as input.

Applied data normalization and batching.

Trained using cross-entropy loss.

Optimized using Adam optimizer.

🔹 Q3.2 Evaluation Metrics (2 Marks)

Approach:

Calculated Accuracy.

Computed weighted F1-score to handle class imbalance.

Evaluated performance on test dataset.

🔹 Q3.3 Confusion Matrix & Interpretation (1 Mark)

Approach:

Generated confusion matrix using sklearn.

Visualized using heatmap.

Interpreted class-wise misclassification patterns (e.g., vegetation vs cropland confusion).

🛠️ Tech Stack

Python

GeoPandas

Rasterio

Shapely

NumPy, Pandas

Matplotlib

PyTorch / TensorFlow

Scikit-learn

geemap

📊 Key Contributions

Designed full geospatial data processing pipeline

Implemented raster-vector spatial alignment

Automated label extraction using dominant class logic

Built supervised CNN land-use classifier

Evaluated model using standard ML metrics
