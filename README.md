# TME-Inferred Genotyping: Pan-Cancer Prediction of Driver Mutations from Tumor Microenvironment Composition

Companion code for:

> **Inference of cancer driver mutations from tumor microenvironment composition: a pan-cancer study with cross-platform external validation**
> Elizabeth Baker and Nathan Mehaffy
> *Submitted to Scientific Reports*

## Overview

This repository contains a single reproducible Jupyter notebook that trains machine learning models to predict cancer driver mutation status from tumor microenvironment (TME) cell-type composition signatures derived from bulk transcriptomes. Models are trained on TCGA and externally validated on independent cohorts spanning different sequencing platforms.

**Cancer types:** Glioblastoma (GBM), Breast cancer (BRCA), Lung adenocarcinoma (LUAD), Colorectal cancer (CRC)

**Key result:** 14 of 15 driver–cancer pairs achieved external validation AUC ≥ 0.65, with top performance for ERBB2 amplification in BRCA (AUC = 0.980).

## Datasets

All data are publicly available:

| Cohort | Source | Use |
|--------|--------|-----|
| TCGA GBM, BRCA, LUAD, CRC | [cBioPortal](https://www.cbioportal.org/) (Pan-Cancer Atlas) | Training |
| CPTAC GBM | [cBioPortal](https://www.cbioportal.org/) | Validation |
| METABRIC | [cBioPortal](https://www.cbioportal.org/) | Validation |
| GSE72094 | [GEO](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE72094) | Validation |
| GSE39582 | [GEO](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE39582) | Validation |

## Running the Notebook

The notebook is designed to run on [Kaggle](https://www.kaggle.com/):

1. Create a new Kaggle notebook
2. Import `TME_Genotyping_Pipeline.ipynb`
3. Add the datasets listed above via the Kaggle dataset interface
4. Update data paths in Cell 10 if needed
5. Run all cells (estimated runtime: 30–45 minutes, no GPU required)

### Dependencies

- Python 3.8+
- scikit-learn, pandas, numpy, matplotlib, seaborn
- lifelines (survival analysis)
- shap (feature attribution)
- GEOparse (GEO data handling)

All dependencies are pre-installed on Kaggle or installed in the first cell of the notebook.

## Analyses Included

- **Primary classification:** L2 logistic regression with 5-fold cross-validation and external validation for 15 driver–cancer pairs
- **Sensitivity analyses:** ssGSEA vs. mean z-score comparison, tumor purity correction, permutation testing
- **Survival analysis:** Univariate and multivariate Cox regression in METABRIC (ERBB2, TP53)
- **SHAP feature attribution** and feature reduction curves
- **KRAS co-mutation subgroup analysis** in LUAD (KRAS+STK11 vs. KRAS+TP53)
- **LM22 comparison:** Custom tissue-specific signatures vs. canonical immune reference
- **Clinical utility:** Sensitivity, specificity, PPV, NPV at optimal and conservative thresholds
- **Negative control:** Random-label null model validation

## License

MIT
