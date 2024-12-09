# GEDI Lidar Waveform Outlier Detection Project

This repository contains the implementation of machine learning models and supporting analyses for detecting outliers in NASA’s **Global Ecosystem Dynamics Investigation (GEDI)** lidar waveform data. This work supports a global carbon quantification project, led by Prof. James Kellner’s lab, to provide reliable data for climate policy and ecological studies.

## Project Description

The objective of this project is to filter invalid and noisy lidar waveforms collected from orbit, ensuring data integrity for downstream carbon modeling. Using a combination of data preprocessing, exploratory visualization, and machine learning techniques, this project identifies outlier patterns caused by environmental and instrumental factors, such as:
- Low clouds and dense fog
- Steep ground slopes
- Instrumental errors in data acquisition

### Highlights
- **Preprocessing**: Cleaned and visualized waveform data using PCA and 3D clustering.
- **Machine Learning Models**: Implemented Gaussian Mixture Models, Isolation Forests, and DBSCAN for outlier detection.
- **Cross-validation**: Evaluated model accuracy, consistency, and sensitivity across a dataset of 400,000 points.
- **Collaboration**: Model outputs have been shared with University of Maryland collaborators for review and exploratory applications.

## Repository Contents

### 1. Notebooks
The repository contains Jupyter notebooks for data preprocessing, visualization, and machine learning model implementation:
- `Outlier_detector_vX.ipynb`: Files implementing different versions of the outlier detection models.

### 2. Visualizations and Outputs
All visualizations and processed model outputs are located in the `GEDI_outputs` folder.

### 3. Data Reference
The GEDI data files used for this project are not included in the repository due to size constraints but can be accessed via NASA's [Earthdata Cloud](https://www.earthdata.nasa.gov). Below is a list of the datasets used:
- `GEDI01_B_2022004042652_O17343_04_T10772_02_005_02_V002.h5`
- `GEDI01_B_2022207041426_O20491_04_T09293_02_005_03_V002.h5`
- `GEDI02_A_2021050140102_O12405_02_T10912_02_003_02_V002.h5`
- `GEDI02_A_2021086153349_O12964_03_T08275_02_003_02_V002.h5`
- `GEDI04_A_2021009022644_O11762_03_T01637_02_002_02_V002.h5`
- `GEDI04_A_2022106075705_O18927_04_T10647_02_003_01_V002.h5`

You can also download these files directly from my Google Drive [here](https://drive.google.com/drive/folders/1H-NVGvDSt2nu4VFfeTGVTVHJTP_YgXJw?usp=sharing).
Be sure to keep the files in the `GEDI_sample_files` folder for the models to work correctly.

## Future Work
- Implement automatic labeling algorithms for newly collected ground truth data.
- Explore semi-supervised learning techniques, Bayesian models, and neural networks for improved classification.
