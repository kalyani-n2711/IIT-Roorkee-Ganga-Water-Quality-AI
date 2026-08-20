# IIT Roorkee Ganga Water Quality AI

## Multimodal Spatial AI Framework for Ganga River Water Quality Analysis and Prediction

This repository contains the work developed during my **IIT Roorkee internship**, focused on building an AI-driven framework for multimodal spatial analysis and prediction of **Ganga River water quality**.

The project integrates heterogeneous environmental and geospatial datasets with spatial interpolation and **Graph Convolutional Networks (GCNs)** to model relationships between water quality and surrounding environmental factors.

---

## Project Overview

Water quality varies spatially due to multiple interacting environmental and anthropogenic factors. Conventional tabular machine learning approaches often fail to explicitly model the spatial relationships between monitoring locations.

This project addresses the problem by constructing a **multimodal spatial dataset** and applying graph-based deep learning.

### Overall Pipeline

```text
Environmental Data Sources
        |
        v
Data Extraction & Preprocessing
        |
        +--> CWC Water Quality
        +--> CHIRPS Rainfall
        +--> GPW4 Population Density
        +--> LULC / Land Cover
        +--> GRDC River Discharge
        +--> GHSL Built-up / Settlement Information
        +--> Spatial / Geographic Features
        |
        v
Multimodal Data Integration
        |
        v
Spatial Interpolation
        |
        v
Graph Construction
        |
        v
Graph Convolutional Network
        |
        v
Water Quality Prediction
```

---

## Key Components

### 1. Water Quality Data Extraction

Water quality observations were collected and processed to create the base environmental dataset.

**Notebook:**

`01_CWC_Water_Quality_Extraction.ipynb`

---

### 2. Rainfall Data

CHIRPS rainfall information was incorporated as an environmental variable to capture the influence of precipitation on river water quality.

**Notebook:**

`02_CHIRPS_Rainfall_Data_Extraction.ipynb`

---

### 3. Population Density

GPW4 population density data was incorporated to represent anthropogenic pressure surrounding the river system.

**Notebook:**

`03_GPW4_Population_Density_Extraction.ipynb`

---

### 4. Land Use / Land Cover

LULC information was extracted to characterize the surrounding geographical environment.

**Notebook:**

`04_LULC_Land_Cover_Extraction.ipynb`

---

### 5. River Discharge

GRDC river discharge data was incorporated as a hydrological feature.

**Notebook:**

`05_GRDC_River_Discharge_Extraction.ipynb`

---

### 6. Built-up and Settlement Features

GHSL-based built-up and settlement information was used to represent urbanization and anthropogenic influence.

**Notebook:**

`06_GHSL_Built_Settlement_Distance_Extraction.ipynb`

---

### 7. Area of Interest Definition

Spatial boundaries covering the selected Ganga River study region were prepared for downstream geospatial processing.

**Notebook:**

`07_Kanpur_Varanasi_AOI_Boundary_Extraction.ipynb`

---

## Multimodal Dataset Integration

The extracted datasets were unified into a common spatial representation.

**Notebook:**

`08_Unified_Multimodal_CSV_Integration.ipynb`

The resulting dataset combines:

* Water quality measurements
* Rainfall
* Population density
* Land-use/land-cover information
* River discharge
* Built-up/settlement information
* Spatial coordinates and derived geographic features

A processed dataset is provided in:

```text
Ganga_Interpolated_Water_Quality.csv
```

and:

```text
final_day15aug_work/_final_dataset Ganga_Multimodal_Spatial_WQ.csv
```

---

## Spatial AI Model

The integrated multimodal dataset is used to construct a spatial graph representing relationships between locations.

Nodes represent spatial locations, while graph connectivity captures spatial relationships between observations.

A **Graph Convolutional Network (GCN)** is then used for spatial representation learning and water quality prediction.

**Main notebook:**

`09_Spatial_GNN_Water_Quality_Model.ipynb`

**Final modeling notebook:**

`final_last_Ganga_Spatial_AI_Water_Quality_Prediction.ipynb`

A trained model is also included:

```text
water_quality_gcn.pth
```

---

## Mathematical Foundation

For a graph

[
G=(V,E)
]

where (V) represents spatial nodes and (E) represents relationships between nodes, the GCN performs neighborhood-based feature aggregation.

A standard GCN layer can be expressed as:

[
H^{(l+1)}
=========

\sigma
\left(
\tilde{D}^{-\frac{1}{2}}
\tilde{A}
\tilde{D}^{-\frac{1}{2}}
H^{(l)}
W^{(l)}
\right)
]

where:

* (A) = adjacency matrix
* (\tilde{A}=A+I) = adjacency matrix with self-loops
* (\tilde{D}) = degree matrix of (\tilde{A})
* (H^{(l)}) = node representations at layer (l)
* (W^{(l)}) = trainable weight matrix
* (\sigma) = activation function

This allows the model to learn from both **local environmental features and spatial relationships**.

---

## Repository Structure

```text
IIT-Roorkee-Ganga-Water-Quality-AI/
│
├── final_day15aug_work/
│   ├── 01_CWC_Water_Quality_Extraction.ipynb
│   ├── 02_CHIRPS_Rainfall_Data_Extraction.ipynb
│   ├── 03_GPW4_Population_Density_Extraction.ipynb
│   ├── 04_LULC_Land_Cover_Extraction.ipynb
│   ├── 05_GRDC_River_Discharge_Extraction.ipynb
│   ├── 06_GHSL_Built_Settlement_Distance_Extraction.ipynb
│   ├── 07_Kanpur_Varanasi_AOI_Boundary_Extraction.ipynb
│   ├── 08_Unified_Multimodal_CSV_Integration.ipynb
│   ├── 09_Spatial_GNN_Water_Quality_Model.ipynb
│   ├── Ganga_Interpolated_Water_Quality.csv
│   ├── _final_dataset Ganga_Multimodal_Spatial_WQ.csv
│   └── final_last_Ganga_Spatial_AI_Water_Quality_Prediction.ipynb
│
├── Ganga_Interpolated_Water_Quality.csv
├── water_quality_gcn.pth
├── system_architecture.png
├── sys_final_architecture.png
├── IIT_Roorkee_Internship_Report_Kalyani_Agarwal.pdf
├── IIT_ROORKEE_REPORT_kalyani.pdf
└── .gitignore
```

---

## Technologies Used

* **Python**
* **Jupyter Notebook**
* **PyTorch**
* **Graph Convolutional Networks (GCN)**
* **Pandas**
* **NumPy**
* **Geospatial Data Processing**
* **Spatial Interpolation**
* **Environmental Data Analysis**
* **Graph-based Deep Learning**

---

## Data Sources

The project integrates multiple environmental and geospatial data sources, including:

| Dataset | Purpose                                 |
| ------- | --------------------------------------- |
| CWC     | River water quality observations        |
| CHIRPS  | Rainfall information                    |
| GPW4    | Population density                      |
| LULC    | Land-use / land-cover characteristics   |
| GRDC    | River discharge                         |
| GHSL    | Built-up and settlement characteristics |

---

## Research Workflow

The complete workflow consists of:

1. Environmental data collection
2. Data cleaning and preprocessing
3. Spatial alignment of heterogeneous datasets
4. Area-of-interest extraction
5. Multimodal feature integration
6. Spatial interpolation
7. Graph construction
8. GCN model development
9. Model training
10. Water quality prediction
11. Model evaluation and analysis

---

## Internship Context

**Institution:** IIT Roorkee

**Project Area:** Artificial Intelligence, Geospatial Data Science, Environmental Analytics and Graph Neural Networks

**Focus:** AI-driven multimodal spatial analysis for Ganga River water quality

This repository documents the computational workflow, datasets, notebooks, trained model, visualizations, and internship reports associated with the project.

---

## Future Work

Potential extensions include:

* Integration of real-time IoT water quality sensors
* Temporal Graph Neural Networks for dynamic water quality forecasting
* Satellite-based remote sensing features
* Graph Attention Networks (GAT)
* Spatiotemporal forecasting
* Explainable Graph Neural Networks
* Automated environmental risk mapping
* Real-time water quality monitoring dashboards

---

## Author

**Kalyani Agarwal**

B.Tech — Artificial Intelligence & Data Science

IIT Roorkee Internship Project

---

## Disclaimer

This repository contains academic and research work developed during an internship. The datasets, preprocessing procedures, model architecture, and results are intended for research and educational purposes.
