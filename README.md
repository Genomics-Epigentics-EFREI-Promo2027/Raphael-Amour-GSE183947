# RNA-seq Differential Expression Analysis — Breast Cancer (GSE183947)

**Raphael Amour — 20220614**

## Overview

This project explores the transcriptomic differences between breast tumor tissue and adjacent non-tumor tissue using the public GEO dataset GSE183947. The central question is: which genes and biological pathways are differentially expressed in breast tumors compared to healthy adjacent tissue?

The dataset comes from a study identifying cytotoxicity-related genes involved in breast cancer progression (30 tumor vs. 30 adjacent samples, FPKM format).

## Workflow

1. Data import and preprocessing — FPKM to pseudo-counts conversion, low-expression filtering
2. DESeq2 differential expression analysis with apeglm LFC shrinkage
3. Quality control — PCA, sample distance heatmap, dispersion estimates
4. Visualization — volcano plot, MA plot, heatmap of top DE genes
5. GO Biological Process enrichment analysis (clusterProfiler)

## Main Results

643 upregulated and 2,271 downregulated genes were identified in tumor tissue (padj < 0.05, |LFC| > 1). The most significant genes included RNASE11, UGT2A1, CCDC177 and MFRP.

GO enrichment revealed activation of mitotic and chromosomal processes in upregulated genes (chromosome organization, nuclear division, mitotic cell cycle), consistent with uncontrolled tumor proliferation. Downregulated genes were enriched in tissue-specific functions such as circulatory and muscle system processes, reflecting tumor dedifferentiation.

## How to Run

```bash
git clone https://github.com/your-username/your-repository.git
```

Place `GSE183947_fpkm.csv` in the `data/` folder, open `analysis.Rmd` in RStudio and knit.

## Dependencies

```r
install.packages(c("tidyverse", "ggrepel", "RColorBrewer", "scales", "patchwork", "pheatmap"))
BiocManager::install(c("DESeq2", "apeglm", "clusterProfiler", "org.Hs.eg.db"))
```
