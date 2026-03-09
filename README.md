# Reliability Modeling

This repository contains MATLAB scripts used to perform probabilistic reliability modeling for a water treatment system.  
The methodology combines statistical analysis, probability distribution fitting, and Monte Carlo sampling to construct a Bayesian Network for reliability assessment.

The scripts were developed in **MATLAB R2019b** using the **Statistics and Machine Learning Toolbox**, while the Bayesian Network was implemented using **GeNIe Modeler 2.4**.

The overall workflow of the methodology is illustrated in:

**docs/reliability-modeling-architecture.pdf**

---

# Methodology Overview

The modeling workflow includes the following steps:

1. Compute statistical parameters of the observed variables
2. Analyze correlations between variables
3. Fit probability distributions to the data
4. Generate correlated random samples using the **Nataf transformation**
5. Build and analyze a **Bayesian Network** using the generated samples

---

# Technologies

- MATLAB
- Statistical Modeling
- Probability Distributions
- Monte Carlo Simulation
- Bayesian Networks
- GeNIe Modeler

---

# Project Structure

## Statistical analysis

### `statistical_parameters_eff_sand.m`
Computes the **mean, standard deviation, and coefficient of variation** for the input dataset (`eff_sand.mat`).  
The results are exported to:

`matlab_statistical_parameters.xlsx`

---

### `correlations_ant_sand.m`
Computes **correlation coefficients** between the datasets:

- `eff_ant.mat`
- `eff_sand.mat`
- `do_consump.mat`

The script also generates **scatter plots** and exports the results to:

`matlab_correlations_ant_sand.xlsx`

---

### `distribution_fittings_eff_sand.m`
Fits multiple **probability distributions** to the dataset `eff_sand.mat` using **Maximum Likelihood Estimation (MLE)**.

The results are exported to:

`matlab_distribution_fittings_eff_sand.xlsx`

---

## Sample generation

### `gen_samples_sand.m`
Generates correlated random samples using the selected probability distributions.  
The correlation structure is modeled using the **Nataf transformation with a Gaussian copula**.

Generated samples are stored in:

`samples_sand.xlsx`

---

## Bayesian Network

### `bn_final.xdsl`
Bayesian Network model implemented in **GeNIe Modeler**.

The network uses the generated samples (`samples_sand.xlsx`) to compute the **Conditional Probability Tables (CPTs)** using the **Expectation–Maximization algorithm**.

Further analysis of the system reliability can be performed using this model in GeNIe.
