# Soil Moisture Reflectance Spectroscopy

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![Python](https://img.shields.io/badge/Python-3.12-blue.svg)

This repository contains the data and code for modeling the soil reflectance normalization factor (c-factor) using physical soil properties, as part of the study:  
**"Organic Carbon and Texture control Moisture Dependence of Soil Shortwave Infrared Reflectance"** *Accepted in the European Journal of Soil Science (2026).*

## Overview
This project investigates how soil moisture affects reflectance in the Shortwave Infrared (SWIR) domain. We found that the "darkening" of soil as moisture increases follows a wavelength-dependent exponential decay which varies based on selected soil properties. 

### Key Findings:
* The rate of reflectance decrease is controlled by **Organic Carbon (OC)** and **Soil Texture** (specifically Clay, Silt, and Sand).
* Our multiple linear regression model explains up to **67% of the variance** in the normalization factor (the "darkening rate").
* **OC and Clay content** account for **~70% of the relative feature importance** based on Dominance Analysis.

## Data
The dataset includes laboratory spectra for 28 European soil samples at varying moisture levels, alongside physical properties (OC, Clay, Silt, Sand content).

> [!IMPORTANT]
> **Reproducibility Note:** The dataset is provided in a fixed index order. Validation metrics (e.g., K-Fold $R^2$) may vary slightly with different data partitioning due to the small sample size ($n=28$). To replicate the specific results in the paper, ensure you use the fixed random seeds provided in the `soil_moisture_reflectance.ipynb`.

## Repository Structure
- `Data/`: Contains the spectral and attribute CSV files.
  - `sample_spectra.csv`: SWIR reflectance spectra for 28 soil samples
  - `samples_attributes.csv`: Physical properties (OC, Clay, Silt, Sand) per sample
  - `samples_cfactor.csv`: Samples' c-factors.
  - `samples_sfactor.csv`: Samples' degree of saturation normalised factors.
- `soil_moisture_reflectance.ipynb`: Main analysis script including example c-factor and normalisation factor determination, log normalisation, ANOVA, and Dominance Analysis.
- `requirements.txt`: List of necessary Python libraries.

## Setup & Installation

### Option 1: Conda (Recommended)
1. Clone the repository.
2. Create the environment from the `.yml` file:
   ```bash
   conda env create -f SM_environment.yml
   ```
3. Activate the environment
   ```bash
   conda activate soil_moisture_swir
   ```

### Option 2: Pip
   
1. Clone the repository.
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Explore and run the notebook!
   
## License
This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.


## Citation
If you use this data or code in your research, please cite the original paper:

> Hick, D., Chapman, P. J., Breure, T. S., & Ziv, G. (2026). Organic Carbon and Texture control Moisture Dependence of Soil Shortwave Infrared Reflectance. *European Journal of Soil Science*. https://doi.org/[DOI here]
