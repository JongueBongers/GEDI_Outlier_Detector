# GEDI Lidar Waveform Outlier Detection Project

This repository contains the implementation of machine learning models and supporting analyses for detecting outliers in NASA’s **Global Ecosystem Dynamics Investigation (GEDI)** lidar waveform data. This work supports a global carbon quantification project, led by Prof. James Kellner’s lab, to provide reliable data for climate policy and ecological studies.

## Project Description

The objective of this project is to filter invalid and noisy lidar waveforms collected from orbit, ensuring data integrity for downstream carbon modeling. Using a combination of data preprocessing, exploratory visualization, and machine learning techniques, this project identifies outlier patterns caused by environmental and instrumental factors, such as:
- Low clouds and dense fog
- Steep ground slopes
- Instrumental errors in data acquisition

### Highlights
- **Preprocessing**: Cleaned and visualized waveform data, following NASA tutorials.
- **Machine Learning Models**: Implemented Gaussian Mixture Models, Isolation Forests, and **novel methods based on PCA and autoencoders** for unsupervised outlier detection.
- **Next Steps***: Currently designing **regression, random forest and deep learning models** to identify outlier covariates in 1 million labeled points (ALS crossover data), validate unsupervised models, and advise future waveform preprocessing strategies.

## Repository Contents

### 1. Notebooks
The repository contains various Jupyter notebooks for data preprocessing, visualization, and machine learning model implementation.

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
- `GEDI_ALSCROSSOVERS.csv`

You can also download these files directly from my Google Drive [here](https://drive.google.com/drive/folders/1H-NVGvDSt2nu4VFfeTGVTVHJTP_YgXJw?usp=sharing).
Be sure to create an `Input_files` folder and keep these files in there for the models to work correctly.

## Future Work
- Subset GEDI files for overlap with ground truth ALS crossover data.
- Implement automatic labeling algorithms for newly collected ground truth data.
- Explore semi-supervised learning techniques, Bayesian models, and neural networks for improved classification.

## Feb. 18, 2025 Notes
- For the next phase of the project, we want to **predict the difference in AGBD** between real GEDI and corresponding simulated waveforms at the same location using ancillary data from GEDI data products.
- **Approach**: There is a list of shot numbers and ALS data (these are the GEDI-ALS crossovers). Filtering has been applied to the current crossover data set, so that the crossovers are “good” matches. This might need to be revisited. A challenge is that GEDI and simulated waveforms can differ for two reasons: (1) an outlier or (2) geolocation error. Filtering using the correlation coefficient addresses both of these issues, but means that the crossover dataset does not contain extreme outliers. This might be fine, and seems better than the situation where we have differences in AGBD that are due to geolocation error, not outliers.
### Immediate Next Steps:
  - I will write scripts to read in a GEDI01_B files, GEDI02_A files and GEDI04_A files and determine whether they contain matches to any of the shot numbers inside the ALS crossover file.
  - If matches exist, the scripts will pull all data for that shot number from the matching file and write the output.
  - After this works on a single file, we will distribute the job on OSCAR.
  - We will need to avoid redundant output. Many of the variables are repeated among the files.
  - Fit models to predict the difference (AGBD_ALS – AGBD_GEDI) as a function of ancillary variables
### Things to watch out for:
Shot numbers must be read correctly. They sometimes contain leading zeros, so if they are read as numbers they will be incorrect. I read all of them as strings to handle them.
We will need to convert text variables into dummy variables or numbers. For example, beam and channel should be one hot encoded. Dates should be expressed as the number of days since the start of the mission.
