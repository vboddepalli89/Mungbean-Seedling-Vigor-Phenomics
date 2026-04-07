**"UAV-based high-throughput phenotyping enables genetic dissection and genomic prediction of early seedling vigor in mungbean (Vigna radiata L.)"**

## Project Overview

Successful mungbean establishment depends on early seedling vigor (SVG). This project integrates UAV-RGB imagery, spatial modeling (SpATS), multi-model GWAS (BLINK, FarmCPU, SVEN), and genomic prediction to dissect the genetic architecture of SVG in the Iowa Mungbean Diversity (IMD) panel.

## Repository Structure & Workflow

The analysis follows a four-stage pipeline:

1. **Trait Extraction** (`Vegetation Index, Canopy Height, Canopy Area Extraction.ipynb`)
    * Python/OpenCV script for ExG-based canopy masking ($ExG \ge 0.1$).
    * Derivation of morphological traits (CHT, CC, CVI) and spectral indices (ExGR, NGRDI).

2. **Spatial Modeling** (`spatial_analysis_vigor.Rmd`)
    * Two-stage spatial analysis using the **SpATS** R package.
    * Accounting for field heterogeneity (up to 77.8% phenotypic variance) to estimate BLUEs.

3. **Genome-Wide Association Studies (GWAS)**
    * `gwas_inti_GAPIT pipeine.Rmd`: Implementation of BLINK and FarmCPU models.
    * `SVEN_GWAS.txt`: Selection of Variable Ensemble (SVEN) for ultra-high dimensional mapping.

4. **Genomic Prediction** (`Genomic_prediction_analysis.txt`)
    * 10-fold cross-validation for standard gBLUP.
    * Augmented WGP+SNP models utilizing significant GWAS hits as fixed effects.

## Key Methodology

* **Canopy Masking**: $ExG = 2G - (R + B)$. Pixels $\ge 0.1$ classified as vegetation.
* **Height Estimation**: Calculated as the difference between the 90th percentile DSM (canopy) and 10th percentile DSM (soil).
* **Significance Threshold**: Calibrated using $M_{eff} = 2,513$ independent tests.

## Requirements

* **Python 3.x**: `arcpy`, `OpenCV`, `pandas`, `numpy`
* **R 4.4.2**: `SpATS`, `GAPIT`, `rrBLUP`, `emmeans`, `moments`

## Data Availability

* **Phenotypic Data**: Final BLUEs and prediction results are provided in the journal's Supplementary Material.
* **Sample Data**: A subset of raw data is provided in the `/data` folder for pipeline validation.
* **Genotypic Data**: Publicly accessible via the [Legume Information System](https://data.legumeinfo.org/Vigna/radiata/genomes/Weilv-9.gnm1.5TZZ/).

## Citation

Boddepalli, V.N., Shen, Y., Dutta, S., & Singh, A. (2026). UAV-based high-throughput phenotyping enables genetic dissection and genomic prediction of early seedling vigor in mungbean (*Vigna radiata* L.). 

## Contact

**Venkata Naresh Boddepalli** Ph.D. Candidate, Department of Agronomy  
Iowa State University, Ames, IA, USA  
[Your Email Here]
