# Soil Moisture Reflectance Spectroscopy

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![Python](https://img.shields.io/badge/Python-3.10-blue.svg)

This repository contains the data and code for modeling the soil reflectance normalisation factor (c-factor) using physical soil properties, as part of the study:  
**"Organic Carbon and Texture control Moisture Dependence of Soil Shortwave Infrared Reflectance"** *Accepted in the European Journal of Soil Science (2026).*

<img width="776" height="530" alt="Screenshot 2026-03-30 at 16 48 11" src="https://github.com/user-attachments/assets/05ad2658-2290-4d0b-aba3-1ee11b9051de" />


---
## Table of Contents
- [Overview](#overview)
- [Key Findings](#key-findings)
- [Data](#data)
- [Repository Structure](#repository-structure)
- [Setup & Installation](#setup--installation)
  - [Option 1: Conda (Recommended)](#option-1-conda-recommended)
  - [Option 2: Pip](#option-2-pip)
- [Quick Start](#quick-start)
- [License](#license)
- [Citation](#citation)

---

## Overview
This project investigates how soil moisture affects reflectance in the Shortwave Infrared (SWIR) domain. We found that the "darkening" of soil as moisture increases follows a wavelength-dependent exponential decay which varies based on selected soil properties. 

### Key Findings:
* The rate of reflectance decrease is controlled by **Organic Carbon (OC)** and **Soil Texture** (specifically Clay, Silt, and Sand).
* Our multiple linear regression model explains up to **67% of the variance** in the normalisation factor (the "darkening rate").
* **OC and Clay content** account for **~70% of the relative feature importance** based on Dominance Analysis.

## Data
The dataset includes laboratory spectra for 28 European soil samples at varying moisture levels, alongside physical properties (OC, Clay, Silt, Sand content).

> [!IMPORTANT]
> **Reproducibility Note:** The dataset is provided in a fixed index order. Validation metrics (e.g., K-Fold $R^2$) may vary slightly with different data partitioning due to the small sample size ($n=28$). To replicate the specific results in the paper, ensure you use the fixed random seeds provided in the `soil_moisture_reflectance_notebook.ipynb`.

## Repository Structure
- `Data/`: Contains the spectral and attribute CSV files.
  - `sample_spectra.csv`: VIS-NIR-SWIR reflectance spectra for 28 soil samples at different levels of volumetric water content (θ) 
  - `samples_attributes.csv`: Physical properties (OC, Clay, Silt, Sand, CaCO3, Ox_Fe, BD) per sample
  - `samples_LUCASID_lookuptable.csv`: Samples' LUCAS POINT IDs
  - `samples_cfactor.csv`: Samples' c-factors.
  - `samples_sfactor.csv`: Samples' degree of saturation factors. These are derived from volumetric water content (θ) using bulk density (BD) and an assumed particle density of 2.65 g cm⁻³, following S = θ / (1 − BD / 2.65). This transformation is applied to the column names so that reflectance can be expressed as a function of degree of saturation; the s-factor is then calculated in the same way as the c-factor.
- `soil_moisture_reflectance_notebook.ipynb`: Main analysis script including example c-factor and normalisation factor determination, log normalisation, ANOVA, and Dominance Analysis.
- `SM_environment.yml`: yml file for easy environment creation in Conda
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


 ## Quick start  
 Run the notebook to reproduce the main results and explore!
 
   ```bash
   jupyter notebook soil_moisture_reflectance_notebook.ipynb
   ```

<img width="992" height="535" alt="Screenshot 2026-03-30 at 16 50 13" src="https://github.com/user-attachments/assets/0c903243-6e83-4e50-958e-a5914f087b11" />


   
## License
This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.


## Citation
If you use this data or code in your research, please cite the original paper:

> Hick, D., Chapman, P. J., Breure, T. S., & Ziv, G. (2026). Organic Carbon and Texture control Moisture Dependence of Soil Shortwave Infrared Reflectance. *European Journal of Soil Science*. https://doi.org/[DOI here]
