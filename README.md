# Differential Expression Analysis (DESeq2) & RNA-seq Processing Pipeline Across Soft Tissue Sarcoma Groups

## Overview
This repo contains scripts for preprocessing and DESeq2 analysis of sarcoma RNA-seq data.  
Core flow: **raw counts → filtered counts → DESeq2 inputs → analysis outputs**.

## Organization
- **data/** → input and output files  
  - `counts_filtered.csv` → gene x sample matrix after QC filtering  
  - `sarcoma_counts.rds` → DESeq2-ready `DESeqDataSet` object  
  - `sarcoma_colData.csv` → sample metadata (design/condition/type)  
  - `sarcoma_rowData.csv` → gene annotations  
- **scripts/** → R scripts for filtering, sanity matrices, DESeq2 setup, analysis  
- **results/** → DESeq2 outputs, plots, differential expression tables  
- **renv/** → environment snapshot for reproducibility  

## Key Artifacts
- `counts_filtered.csv` → raw count matrix (genes x samples) after QC filtering.  
- `sarcoma_counts.rds` → DESeq2-ready `DESeqDataSet` object.  
- `sarcoma_colData.csv` → sample metadata (design, condition, type).  
- `sarcoma_rowData.csv` → gene annotations linked to counts.  

## Workflow
1. **Filtering**: remove low-expression genes, save `counts_filtered.csv`.  
2. **Alignment sanity checks**: verify count matrix integrity.  
3. **DESeq2 Prep**: build `sarcoma_counts.rds` with matching `colData` + `rowData`.  
4. **Analysis**: run DESeq2 differential expression, diagnostics, downstream plots.  

## Environment
Use `renv` to restore exact R package versions:  
```r
renv::restore()
