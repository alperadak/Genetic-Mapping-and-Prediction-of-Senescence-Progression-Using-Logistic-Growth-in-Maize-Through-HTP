![image](https://github.com/user-attachments/assets/07ee8c7e-ef4c-4858-b7fb-bf2e4deb9f1f)

# A computational framework for modeling and predicting maize senescence

This repository contains data and analysis workflows associated with the study:

**Adak, A., DeSalvio, A. J., & Murray, S. C. (2025).**  
*A computational framework for modeling and predicting maize senescence: integrating UAV phenotyping, logistic growth, and genomics.*  
**Computers and Electronics in Agriculture**, 237, 110471.  
https://doi.org/10.1016/j.compag.2025.110471

---

## Overview

This repository provides a computational framework for modeling and predicting **temporal maize senescence** by integrating:

- UAV-based high-throughput phenotyping,
- logistic growth modeling of senescence trajectories,
- genomic and phenomic relationship matrices, and
- Bayesian genomic prediction.

Temporal senescence scores were collected across multiple days after planting (DAP). For each genotype, senescence progression was modeled using a logistic growth curve, and biologically meaningful parameters describing the **timing and rate of senescence** were extracted. These parameters were subsequently used as target traits in genomic and phenomic prediction models.

---

## Analysis workflow

The overall analysis consists of the following steps:

1. **UAV-based phenotyping**  
   Senescence was scored temporally using RGB imagery acquired by UAV platforms.

2. **Logistic growth modeling**  
   Genotype-specific senescence trajectories were modeled using a logistic growth function to estimate:
   - inflection point (timing of rapid senescence),
   - rate of senescence progression.

3. **Genomic and phenomic prediction**  
   Logistic growth parameters were predicted using Bayesian models based on:
   - genomic relationship matrices (GRM),
   - phenomic relationship matrices (PRM),
   - or their combination.

4. **Cross-validation**  
   Prediction accuracy was evaluated using repeated cross-validation under multiple scenarios, including tested and untested genotypes and environments.

---

## Input data files

### Phenotypic and GWAS data

- **`Senescence.csv`**  
  Plot-based senescence scores recorded at multiple time points (85, 91, 100, 111, and 128 DAP).  
  Used for modeling temporal senescence trajectories.

- **`out.csv`**  
  Output from the statistical model describing temporal senescence progression.  
  Genotypic effects from this file are used as target traits for genomic and phenomic prediction.

- **`GLM.out.zip`**  
  GWAS results generated using GAPIT GLM across multiple DAPs.  
  Used for FPCA-based modeling of temporal SNP effect trajectories.

### Genomic and phenomic data

- **`geno.numerical.csv`**  
  Numerical marker matrix for recombinant inbred lines (RILs), used to construct the genomic relationship matrix (GRM).

- **`Phenomic_ExR_NGRDI.csv`**  
  UAV-derived phenomic features (e.g., NGRDI and ExR vegetation indices) measured at early growth stages  
  (43, 57, 62, 65, 69, 72, 76, 79, and 83 DAP).  
  Used to construct the phenomic relationship matrix (PRM).

---

## Logistic growth modeling of senescence

Senescence progression for each genotype was modeled using a logistic growth function:

S(t) = 100 / (1 + exp(-(t - x_mid) / scal))

where:
- t is days after planting (DAP),
- x_mid is the inflection point,
- scal controls the rate of senescence progression.

Logistic models were fitted independently for each genotype using non-linear least squares. The estimated parameters were treated as quantitative traits in downstream prediction analyses.

---

## Genomic and phenomic prediction models

Bayesian prediction models were implemented using the **BGLR** framework under the following configurations:

- **M1 (Genomic model)**  
  Prediction using the genomic relationship matrix (GRM) only.

- **M2 (Genomic + phenomic model)**  
  Prediction using both GRM and PRM.

Predicted logistic parameters were used to reconstruct full senescence trajectories across time.

---

## Cross-validation strategy

Prediction performance was evaluated using 100 repeated cross-validation iterations under four scenarios:

- **CV1**: Tested genotypes in tested senescence time(s)  
- **CV2**: Untested genotypes in tested senescence time(s)  
- **CV0**: Tested genotypes in untested senescence time(s)  
- **CV00**: Untested genotypes in untested senescence time(s)  

Model performance was assessed using correlation and root mean square error (RMSE) between observed and predicted senescence values.

---

## Repository structure

### Data files
- **`GLM.out.zip`**  
  GWAS results from GAPIT GLM across multiple DAPs.

- **`Senescence.csv`**  
  Temporal senescence scores.

- **`out.csv`**  
  Genotypic effects from temporal senescence modeling.

- **`geno.numerical.csv`**  
  Marker matrix used to construct the GRM.

- **`Phenomic_ExR_NGRDI.csv`**  
  UAV-derived phenomic features used to construct the PRM.

### Analysis workflows
- **Logistic growth model–driven genomic prediction**  
  Scripts for fitting logistic growth curves and predicting senescence parameters using BGLR.

- **Temporal SNP effect trajectories using FPCA**  
  FPCA workflows for modeling time-dependent SNP effects derived from GWAS outputs.

- **Illustrating temporal senescence progression**  
  Visualization scripts for UAV-based senescence dynamics.

### Documentation
- **`README.md`**  
  Project overview, data description, and links to the associated publication.

---

## Citation

If you use this repository, data, or analysis workflows, please cite:

> **Adak, A., DeSalvio, A. J., & Murray, S. C. (2025).**  
> *A computational framework for modeling and predicting maize senescence: integrating UAV phenotyping, logistic growth, and genomics.*  
> **Computers and Electronics in Agriculture**, 237, 110471.  
> https://doi.org/10.1016/j.compag.2025.110471

### BibTeX

```bibtex
@article{Adak2025Senescence,
  author  = {Adak, Alper and DeSalvio, Aaron J. and Murray, Seth C.},
  title   = {A computational framework for modeling and predicting maize senescence:
             integrating UAV phenotyping, logistic growth, and genomics},
  journal = {Computers and Electronics in Agriculture},
  year    = {2025},
  volume  = {237},
  pages   = {110471},
  doi     = {10.1016/j.compag.2025.110471}
}
