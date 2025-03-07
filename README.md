# Bioinformatics_Final  

This project examines the validity of **Hammond et al.** by introducing a secondary dataset and applying alternative clustering methodologies. The study aims to determine whether the original clustering and conclusions remain consistent when tested on an independent dataset. See the write-up for full details on **methods, results, and discussion**.

## Overview  

Hammond et al. identified **nine distinct microglial states** using single-cell RNA sequencing (scRNA-seq) of mouse microglia. Their findings suggest that microglial heterogeneity is highest in younger samples, and inflammation increases with age. Our project introduces the **GLP-1RA dataset**, another microglial dataset, to validate their findings.  

The key objectives of this study are:  
- **Reproducing the clustering in Hammond et al.** with alternative clustering techniques.  
- **Assessing cluster consistency** across different datasets.  
- **Exploring potential novel findings** using different clustering methodologies.  

## Languages and Software  

### **R with RStudio**  
- **Seurat** – data processing and clustering  
- **ggplot2** – visualization  
- **qs** – handling high-dimensional data  
- **tidyverse** – data manipulation  
- **mclust** – Gaussian Mixture Models  

### **Python with Jupyter Notebooks**  
- **pandas** – data filtering and preprocessing  

## Data Processing  

- The **Hammond dataset** was preprocessed using `Seurat` in R.  
- The **GLP-1RA dataset** was provided in CSV format and filtered using `pandas` in Python.  
- Cells with fewer than **650 expressed genes** and genes expressed in fewer than **20 cells** were removed.  
- Data was **log-normalized**, and a **variance stabilizing transformation** was applied for feature selection.  
- **Principal Component Analysis (PCA)** was used for dimensionality reduction (50 PCs retained).  

## Clustering Methods  

We applied three clustering methods to both datasets:  

1. **K-Means Clustering**  
   - Determined optimal clusters using **elbow plots**.  
   - Implemented using `stats::kmeans` in R.  
   
2. **Agglomerative Hierarchical Clustering**  
   - Constructed a **shared nearest neighbor graph**.  
   - Applied the **Smart Local Moving (SLM) algorithm** for clustering.  
   - Merged clusters based on gene expression similarity.  

3. **Gaussian Mixture Models (GMM)**  
   - Implemented using the **mclust** package.  
   - Evaluated clusters based on **Bayesian Information Criterion (BIC)**.  
   - Used uncertainty metrics to assess **cluster stability**.  

## Key Findings  

- **Cluster structures remained largely consistent** across Hammond and GLP-1RA datasets, supporting the validity of the original findings.  
- **Two dominant clusters emerged**, aligning with **younger vs. older microglial states**.  
- **GLP-1RA dataset showed a "hook" structure** in UMAP plots, possibly reflecting treatment effects.  
- **Apoe expression was consistent across age groups**, suggesting that age alone does not induce Alzheimer’s-like microglial changes.  
- **Cst3 was significantly more expressed in GLP-1RA microglia**, indicating a potential **neuroprotective effect of GLP-1RA treatment**.  

## Data Accessibility  

- **Hammond et al. data**: Available via the original paper (see reference).  
- **GLP-1RA dataset**: Available from the **Broad Institute Single Cell Portal** ([SCP1182](https://singlecell.broadinstitute.org/single_cell/study/SCP1182/glp1ra-brain-aging-reversal)).  
- For full reference details, see the **project write-up**.  

## Main References  

- **Hammond, Timothy R. et al.** *Single-Cell RNA Sequencing of Microglia throughout the Mouse Lifespan and in the Injured Brain Reveals Complex Cell-State Changes.* Immunity, 50(1), 253-271.e6 (2019). DOI: [10.1016/j.immuni.2018.11.00](https://doi.org/10.1016/j.immuni.2018.11.00)  
- **Broad Institute Single Cell Portal.** *GLP-1R Brain Aging Reversal* (2024). [Study Access](https://singlecell.broadinstitute.org/single_cell/study/SCP1182/glp1ra-brain-aging-reversal).  

For additional references, refer to the **full project write-up**.  
