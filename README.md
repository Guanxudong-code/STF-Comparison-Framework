# Spatio-Temporal Fusion (STF) Algorithms Collection

This repository provides a comprehensive and unified Python implementation of five state-of-the-art Spatio-Temporal Fusion (STF) algorithms for remote sensing imagery. It is designed to facilitate easy comparison, testing, and deployment of these models for blending high-spatial/low-temporal resolution data (e.g., Landsat) with low-spatial/high-temporal resolution data (e.g., MODIS).

## 🚀 Included Algorithms

1. **STARFM** (Spatial and Temporal Adaptive Reflectance Fusion Model)
2. **FSDAF** (Flexible Spatiotemporal DAta Fusion)
3. **Fit-FC** (Fitting-Filtering-Computing)
4. **RASTFM** (Robust Adaptive Spatial and Temporal Fusion Model)
5. **GAUSTF** (Gaussian-based Spatio-Temporal Fusion)

## 📁 Repository Structure & Test Data

A standardized benchmark dataset is provided in the `test/` directory to help you quickly verify the algorithms.

* **Location:** LGC site.
* **Extent:** A center-cropped sub-area of `400 x 600` pixels (at Landsat resolution).
* **Data Types Included:**
  * High-resolution imagery (Landsat) at $T_1$.
  * Coarse-resolution imagery (MODIS) at $T_1$ and $T_k$.
  * **Note on Coarse Resolution:** The `test/` folder includes both the **raw resolution MODIS** data and **resampled MODIS** data (resampled to match the fine resolution grid, e.g., 500m/30m). Different algorithms have different input requirements (some require the raw coarse pixels, while others require pre-resampled matrices). Please select the corresponding MODIS inputs based on the specific algorithm's requirement.

## 🛠️ Usage Instructions

Each algorithm is contained within its respective directory. Below are the specific instructions to configure and run each model.

### 1. STARFM
* **Execution:** Run the `compute.py` file inside the STARFM directory.
* **Configuration:** Input image paths, output directories, and algorithm parameters are modified directly within the `compute.py` script.

### 2. FSDAF
* **Execution:** Run the main FSDAF script.
* **Configuration:** FSDAF utilizes an interactive GUI (pop-up windows) for configuration. 
  * Upon running, you will be prompted to select the configuration parameters (you can modify or directly load the provided `parameters_fsdaf.yaml` file).
  * Subsequent pop-up windows will guide you to interactively select the input files: the High-Res image at $T_1$, the Low-Res image at $T_1$, and the Low-Res image at $T_k$.

### 3. Fit-FC
* **Execution:** Run the `fit_fc_main.py` script.
* **Configuration:** All input data paths and output directory configurations should be modified directly inside the `fit_fc_main.py` file before execution.

### 4. RASTFM
* **Execution:** Run the `main.py` script located in the RASTFM folder.
* **Configuration:** Input/output paths and parameters are modified directly within `main.py`.
* **🌟 Special Note on RASTFM:** The original official implementation of RASTFM was written in MATLAB, and some core functional files were encrypted. This repository provides a **fully translated Python version**. The three previously encrypted core modules have been reconstructed in Python based on an my understanding of the original paper. Furthermore, critical loops have been heavily optimized and accelerated using **Numba**.

### 5. GAUSTF
* **Execution:** Run the `GAUSTF.py` script (or `main.py` depending on the entry point).
* **Configuration:** Do NOT modify the main algorithmic script. All input paths, output paths, and threshold parameters must be configured centrally in the `src/parameters.py` file.

## 📦 Dependencies

To ensure all algorithms (especially the GUI and Numba-accelerated components) run smoothly, please ensure you have the following standard scientific packages installed:

```bash
pip install numpy scipy rasterio scikit-learn scikit-image matplotlib statsmodels numba pyyaml idlwrap tqdm progressbar2
