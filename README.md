The following input files were used in the study "A computational framework for modeling and predicting maize senescence: integrating UAV phenotyping, logistic growth, and genomics":

Senescence.csv contains plot-based senescence scores recorded at multiple time points — specifically at 85, 91, 100, 111, and 128 days after planting (DAP). These scores were used as input for statistical modeling to estimate genotypic effects associated with temporal senescence progression (see Section 2.3: Statistical analysis of temporal senescence progression to obtain genotypic effects for details).

out.csv includes outputs from the statistical model describing temporal senescence progression. The genotypic effect estimated from this model was used as the target trait in the genomic and/or phenomic prediction framework (see Section 2.5: Logistic growth model-driven genomic and phenomic prediction for temporal senescence for details).

geno.numerical.csv contains the numerical genomic information of the recombinant inbred lines (RILs), used to compute the genomic relationship matrix (GRM) for prediction models (see Section 2.5: Logistic growth model-driven genomic and phenomic prediction for temporal senescence for details).

Phenomic_ExR_NGRDI.csv contains NGRDI and ExR vegetation indices measured at earlier time points — 43, 57, 62, 65, 69, 72, 76, 79, and 83 days after planting (DAP) — prior to the onset of senescence. These phenomic features were used to construct the phenomic relationship matrix (PRM) for prediction models (see Section 2.5: Logistic growth model-driven genomic and phenomic prediction for temporal senescence for details).
