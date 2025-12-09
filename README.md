# Unsupervised Anomaly Detection in SEM Microstructures


## 📖 Overview
This project implements a deep learning-based framework for **unsupervised defect detection** in Scanning Electron Microscopy (SEM) images. 

Targeting the challenges of **data scarcity** and **subjective manual inspection** in materials science, this project utilizes a **Convolutional Autoencoder (CAE)** combined with **K-Means clustering** to identify microstructural anomalies (such as voids, inclusions, and scratches) without requiring pixel-level annotations.

##  Key Features
* **Automated Patching**: Handles high-resolution SEM micrographs via sliding-window slicing.
* **Microstructure Clustering**: Classifies grain textures using PCA and K-Means to understand morphological distributions.
* **Anomaly Detection**: Identifies defects based on reconstruction residual maps (MSE loss).
* **Visualization**: Generates intuitive heatmaps and binary masks for defect localization.

## ⚙️ Methodology

The pipeline follows a three-stage unsupervised approach:

1.  **Data Preprocessing**:
    * High-resolution images are sliced into `64x64` patches (stride=32).
    * Normalization to `[0, 1]` range.
2.  **Pattern Discovery**:
    * Feature extraction via Encoder / PCA.
    * Clustering normal grain structures to ensure dataset consistency.
3.  **Defect Detection (CAE)**:
    * **Training**: The Autoencoder learns to reconstruct healthy grain structures.
    * **Inference**: Defects are detected where the reconstruction error is high.
    * **Metric**: Anomaly Score = $| Input - Reconstruction |$

