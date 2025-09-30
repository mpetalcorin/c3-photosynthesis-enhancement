# c3-photosynthesis-enhancement
Simulation framework and benchmark datasets for evaluating fast-impact genetic strategies that enhance C3 photosynthesis, water use efficiency, and nitrogen efficiency as a bridge toward C4-like crops

# Bridging the Gap to C4: Fast-Impact Genetic Strategies for C3 Crops  

This repository contains code, datasets, and analysis notebooks supporting the manuscript:  
**"Bridging the Gap to C4: Fast-Impact Genetic Strategies to Enhance C3 Photosynthesis, Water, and Nitrogen Efficiency Under Climate Stress."**

# Bridging the Gap to C4: Simulation and Analysis Notebook

## Objectives
- Simulate environmental conditions for C3 crops under diverse stress regimes.
- Apply three interventions: photorespiration bypass, Rubisco optimisation, and stomatal tuning.
- Benchmark effects on assimilation (ΔA), biomass (ΔBiomass), water-use efficiency (ΔWUE), and nitrogen-use efficiency (ΔNUE).
- Slice results by environment (temperature, light, soil nitrogen, vapor pressure deficit).
- Train predictive models to identify key predictors of biomass gains.
- Generate publication-quality figures for manuscript use.

We simulate the effects of three genetic interventions:  
- **Photorespiration bypass**  
- **Rubisco optimisation**  
- **Stomatal tuning**  

By benchmarking against published effect sizes, we explore their impacts on photosynthesis, biomass, water-use efficiency (WUE), and nitrogen-use efficiency (NUE) across 4,000 diverse environmental conditions.  

## Repository Structure  

- `notebooks/` – Jupyter notebooks for simulations, analysis, and figure generation  
- `data/` – Input assumptions (e.g., `benchmark_assumptions.json`) and generated datasets  
- `figures/` – Publication-quality plots (PNG/PDF)  
- `models/` – Trained gradient boosting models for biomass prediction  
- `docs/` – Datasheet and model card  

# Datasheet for Dataset  

# Datasheet for C3 Crop Intervention Simulation Dataset  

## Motivation  
The dataset was generated to benchmark the impacts of three genetic interventions (photorespiration bypass, Rubisco optimisation, stomatal tuning) on C3 crop physiology across a wide range of simulated environmental conditions.  

## Composition  
- **Number of samples:** 4,000 simulated plant environments  
- **Features:**  
  - Temperature (°C)  
  - Photosynthetically Active Radiation (μmol m⁻² s⁻¹)  
  - CO₂ concentration (ppm)  
  - Vapor Pressure Deficit (kPa)  
  - Soil nitrogen (ppm)  
  - Leaf nitrogen content (%)  
  - Leaf Area Index (LAI)  
  - Intervention flags (binary)  
- **Targets:**  
  - Δ Net Assimilation (ΔA)  
  - Δ Biomass Index  
  - Δ Water Use Efficiency (ΔWUE)  
  - Δ Nitrogen Use Efficiency (ΔNUE)  

## Collection Process  
Data were simulated using physiologically grounded equations and benchmarked against effect sizes from peer-reviewed literature (South et al., 2019; Scafaro et al., 2018; Dunn et al., 2019). Random noise was added to mimic biological variability.  

## Recommended Uses  
- Testing predictive models of crop physiology  
- Exploring trait-environment interactions  
- Benchmarking trait stacking strategies  
- Educational use in plant physiology and crop modeling courses  

## Limitations  
- Data are synthetic and not derived from real field trials  
- Parameter ranges are based on literature benchmarks and may not capture full variability across genotypes or environments  
- Results should be validated with experimental data before application in breeding or policy  

# Model Card: Gradient Boosting Biomass Prediction Model  

## Model Details  
- **Model type:** Gradient Boosting Regressor (scikit-learn v1.2)  
- **Objective:** Predict ΔBiomass from environmental and intervention variables  
- **Authors:** Mark Ihrwell R. Petalcorin et al.  
- **Date:** 2025  

## Intended Use  
The model is intended for:  
- Exploring the relative influence of environmental and genetic intervention variables on biomass outcomes  
- Generating empirical design rules for where interventions provide the greatest benefit  

## Training Data  
- **Size:** 3,000 simulated plant environments  
- **Features:** Temperature, PAR, CO₂, VPD, Soil N, Leaf N, LAI, intervention flags  
- **Target:** ΔBiomass  

## Evaluation Data  
- **Size:** 1,000 simulated environments (held-out test set)  
- **Metrics:**  
  - R² = 0.75  
  - RMSE = 0.08 (relative biomass units)  

## Ethical Considerations  
- Model is trained entirely on simulated data, not empirical field data  
- Predictions should not be used for direct agricultural decision-making without experimental validation  

## Limitations  
- Synthetic data may not capture genotype-specific variability  
- Model performance is bounded by the assumptions encoded in the dataset  
- Environmental interactions beyond the sampled ranges are not represented  

## Repository Structure
<img width="922" height="665" alt="Screenshot 2025-09-30 at 15 07 14" src="https://github.com/user-attachments/assets/ab9b2da6-c58f-4278-9f4b-12ffc97275c2" />

## Requirements
numpy>=1.25\
pandas>=2.0\
matplotlib>=3.7\
seaborn>=0.12\
scikit-learn>=1.2\
jupyter
