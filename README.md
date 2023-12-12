# Glioblastoma Transcriptomic Analysis

## Project Overview
This project analyzes the transcriptomics of glioblastoma patients using the REMBRANDT dataset. It focuses on identifying potential biomarkers and therapeutic targets for glioblastoma, a highly aggressive and lethal form of brain cancer. The key methods used include Differential Expression Gene (DEG) analysis, Principal Component Analysis (PCA), and Weighted Gene Co-expression Network Analysis (WGCNA).

## Research Question
The aim is to leverage various bioinformatics tools to identify genes as predictors or biomarkers for distinguishing between tumor and normal tissues and to explore their correlations with clinical outcomes such as survival time and tumor grading.

## Data Analysis
The analysis comprises several stages:

1. **Data Preparation**: 
   - Initial preprocessing of the REMBRANDT dataset to format and normalize the data for analysis.
   - Data cleaning and quality control checks to ensure accurate and reliable inputs for subsequent analyses.

2. **Differential Expression Gene (DEG) Analysis with Limma**:
   - Utilizing the Limma package to perform DEG analysis.
   - Identifying genes with significant expression differences between glioblastoma tumor samples and normal brain tissues.

3. **Principal Component Analysis (PCA) with `prcomp`**:
   - Conducting PCA using the `prcomp` function to reduce the dimensionality of the gene expression data.
   - Focusing on the top 1000 genes based on their loadings on the principal components to identify key genes differentiating between tumor and normal samples.

4. **Weighted Gene Co-expression Network Analysis (WGCNA)**:
   - Employing `blockwiseModules` function from the WGCNA package, tailored for personal computers with limited RAM.
   - Using `pickSoftThreshold` to determine the appropriate power for network construction, ensuring a balance between sensitivity and module size.
   - Correlating gene modules with clinical traits (disease status, survival time, tumor grade).

5. **Gene Ontology (GO) Annotation**:
   - Extracting gene ontology annotations from the dataset to understand the biological processes, cellular components, and molecular functions associated with the identified genes.

6. **Survival Analysis**:
   - Comparing Cox Proportional Hazards model and Random Forest Survival Analysis to explore the relationship between gene expression and patient survival time.
   - Identifying the most influential genes based on their hazard ratios in the Cox model and importance scores in the Random Forest model.

7. **Analysis of Top Biomarkers**:
   - Selecting top biomarkers based on their performance in the survival analysis.
   - Detailed examination of these biomarkers to understand their roles and implications in glioblastoma pathology.

Each of these steps contributes to a comprehensive understanding of the genetic underpinnings of glioblastoma, aiding in the identification of potential biomarkers for diagnosis and treatment.


## Repository Structure
- `Initial Analysis/`: Contains all R code used for the analysis.
- `Files/`: Data files used in the analysis.
- `.gitignore`: Specifies intentionally untracked files to ignore.
- `README.md`: This file, providing an overview of the project.

## Code Overview
- `Initial Analysis.Rmd`: R Markdown file containing the detailed analysis script.
- Additional R scripts and utility functions are located in the `Initial Analysis/` directory.

- ## Required Libraries

To run the scripts and analyses in this project, the following R packages are required. These packages can be installed from CRAN using the `install.packages()` function in R.

```R
# General data manipulation and visualization libraries
library(tidyverse)      # For data manipulation and ggplot2 for plotting
library(readr)          # For reading in data
library(dplyr)          # For data manipulation
library(tidyr)          # For data tidying
library(knitr)          # For dynamic report generation
library(pheatmap)       # For generating heatmaps
library(ggpubr)         # For ggplot2-based publication ready plots
library(ggsignif)       # For adding significance bars to ggplot figures
library(gridExtra)      # For arranging multiple grid-based plots
library(viridis)        # For colorblind-friendly palettes
library(ggVennDiagram)  # For generating Venn diagrams

# Bioinformatics and statistical analysis libraries
library(limma)          # For linear models for microarray data
library(GEOquery)       # For downloading data from GEO
library(sva)            # For Surrogate Variable Analysis
library(biomaRt)        # For accessing BioMart databases
library(hgu133plus2.db) # For annotations specific to the hgu133plus2 platform
library(AnnotationDbi)  # For accessing annotation databases
library(preprocessCore) # For microarray data preprocessing
library(WGCNA)          # For weighted gene co-expression network analysis
library(randomForestSRC)# For Random Forest Survival Analysis
library(survival)       # For survival analysis
library(survminer)      # For visualizing survival analysis results

# Parallel processing and data restructuring libraries
library(parallel)       # For parallel computing capabilities
library(reshape2)       # For reshaping data

# Load the stringdist package for string distance calculations
library(stringdist)
```


## Results 

### Dataset Description
- **Title**: REMBRANDT Brain Cancer Dataset
- **Accession Number**: GSE108476
- **Study Type**: Genomic and Transcriptomic Analysis of Brain Cancer
- **Organism**: Homo sapiens
- **Sample Size**: 671 brain cancer patients
- **Data Composition**: Transcription profiling assays and copy number variation.
- **Technologies Used**: Microarray, DNA Microarray
- **Key Factors Analyzed**: Age, biological sex, diagnosis, tumor grading.

...

### Data Analysis
- **Differential Expression Gene (DEG) Analysis**: ...
- **Principal Component Analysis (PCA)**: ...
  - *Figure 2: PCA Scatter Plot (PC1 vs. PC2)* 
    ![PCA Scatter Plot](/Plots/Figure2.png)
- **Weighted Gene Co-expression Network Analysis (WGCNA)**: ...
  - *Figure 3: WGCNA Module-Trait Relationship Heatmap* 
    ![WGCNA Heatmap](/Plots/Figure3.png)
- **Gene Ontology (GO) Analysis**: ...
  - *Figure 4: Top GO Terms Bar Plot* 
    ![GO Terms Bar Plot](/Plots/Figure4.png)
- **Survival Analysis**: ...
  - *Figure 5: Kaplan-Meier Survival Curves for Selected Genes* 
    ![Survival Curves](/Plots/Figure5.png)

### Insights on Identified Biomarkers
- **AVPR1A1**: ...
- ...
  - *Figure 6: Expression Levels Comparison of Biomarkers* 
    ![Biomarker Expression Levels](/Plots/Figure6.png)

### Limitations and Technical Concerns
The analysis of the glioblastoma dataset, while providing some interesting biomarkers, is subject to several limitations. The reliance on a single dataset may not fully represent genetic diversity, and the imbalance in the number of normal versus tumor samples could skew results, particularly in differential expression analysis. Censoring in survival analysis due to the lack of a binary survival event marker introduces uncertainty, particularly in the interpretation of late-stage survival data. Additionally, challenges in gene annotation, as seen with LOC100293704_MIR8072, raise concerns about the accuracy of gene identification and function.

### Conclusion
The project identified five potential biomarkers (AVPR1A1, NFE4, CCL15, KRT18, UGGT1) in glioblastoma, each with unique implications in cancer biology. These findings, particularly regarding their roles in tumor-immune interactions, cell proliferation, and genetic mutations, contribute novel insights into glioblastoma's molecular mechanisms. While some connections are established in other cancers, their specific roles in glioblastoma could provide a new perspective on the disease's complexity.

  - *Figure 7: Significance of Selected Genes in Survival Analysis* 
    ![Significance Plot](/Plots/Figure7.png)



## How to Run
- Clone the repository and navigate to the `Initial Analysis/` directory.
- Run the R Markdown or R scripts in RStudio or a similar R environment.
- Ensure all required packages listed in the scripts are installed.



## References
1.	 Gusev Y, Bhuvaneshwar K, Song L, Zenklusen JC, Fine H, Madhavan S. The REMBRANDT study, a large collection of genomic data from brain cancer patients. Sci Data. 2018 Aug 14;5:180158. doi: 10.1038/sdata.2018.158. PMID: 30106394; PMCID: PMC6091243.
2.	Wang M, Lindberg J, Klevebring D, Nilsson C, Mer AS, Rantalainen M, Lehmann S, Grönberg H. Validation of risk stratification models in acute myeloid leukemia using sequencing-based molecular profiling. Leukemia. 2017 Oct;31(10):2029-2036. doi: 10.1038/leu.2017.48. Epub 2017 Feb 7. PMID: 28167833; PMCID: PMC5629364.
3.	Ceccarelli M, Barthel FP, Malta TM, Sabedot TS, Salama SR, Murray BA, Morozova O, Newton Y, Radenbaugh A, Pagnotta SM, Anjum S, Wang J, Manyam G, Zoppoli P, Ling S, Rao AA, Grifford M, Cherniack AD, Zhang H, Poisson L, Carlotti CG Jr, Tirapelli DP, Rao A, Mikkelsen T, Lau CC, Yung WK, Rabadan R, Huse J, Brat DJ, Lehman NL, Barnholtz-Sloan JS, Zheng S, Hess K, Rao G, Meyerson M, Beroukhim R, Cooper L, Akbani R, Wrensch M, Haussler D, Aldape KD, Laird PW, Gutmann DH; TCGA Research Network; Noushmehr H, Iavarone A, Verhaak RG. Molecular Profiling Reveals Biologically Discrete Subsets and Pathways of Progression in Diffuse Glioma. Cell. 2016 Jan 28;164(3):550-63. doi: 10.1016/j.cell.2015.12.028. PMID: 26824661; PMCID: PMC4754110.
4.	Larionova, Irina, and Liubov Tashireva. “Immune gene signatures as prognostic criteria for cancer patients.” Therapeutic advances in medical oncology vol. 15 17588359231189436. 2 Aug. 2023, doi:10.1177/17588359231189436
5.	Fenner, Annette. “AVPR1A: a target in CRPC?.” Nature reviews. Urology vol. 16,9 (2019): 508. doi:10.1038/s41585-019-0218-y
6.	Pan, Qiufeng et al. “Identification of a 5-Gene Signature Predicting Progression and Prognosis of Clear Cell Renal Cell Carcinoma.” Medical science monitor : international medical journal of experimental and clinical research vol. 25 4401-4413. 13 Jun. 2019, doi:10.12659/MSM.917399
7.	Schwartzbaum, Judith A et al. “Inherited variation in immune genes and pathways and glioblastoma risk.” Carcinogenesis vol. 31,10 (2010): 1770-7. doi:10.1093/carcin/bgq152
8.	Li, Zhiyong et al. “Integrated genomic and transcriptomic analysis suggests KRT18 mutation and MTAP are key genetic alterations related to the prognosis between astrocytoma and glioblastoma.” Annals of translational medicine vol. 9,8 (2021): 713. doi:10.21037/atm-21-1317
9.	Zhang, Chunyu, and Wei Zhou. “Machine learning-based identification of glycosyltransferase-related mRNAs for improving outcomes and the anti-tumor therapeutic response of gliomas.” Frontiers in pharmacology vol. 14 1200795. 16 Aug. 2023, doi:10.3389/fphar.2023.1200795


