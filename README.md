# Droso_sex_glands_FM_single_C

# FlyCellAtlas Reproductive Organs Sexual Dimorphism Single-Cell Analysis
## Overview

This repository provides a reproducible single-cell RNA-seq analysis framework for studying sexual dimorphism in reproductive organ development using SMART-seq2 datasets from FlyCellAtlas.

The workflow detects:

- sex-biased cell types
- accessory gland vs ovary lineage divergence
- sexual conflict gene enrichment
- reproductive protein expression
- developmental pseudotime divergence
- GO biological processes
- KEGG reproductive pathways

This framework is designed for studying:

- sexual selection
- sexual conflict
- reproductive protein evolution
- germline vs somatic dimorphism
- male accessory gland specialization

## Workflow schema

INPUT: male_SMARTseq2.h5ad, ovary.h5ad

│

QC

│

└── filtered.h5ad

│

Normalization

│

└── normalized.h5ad

│

PCA / UMAP

│

└── dimensionality.h5ad

│

Clustering

│

└── clusters.h5ad

│

Cell type annotation

│

└── annotated.h5ad

│

Differential expression

│

└── DE_genes.csv

│

Sexual conflict enrichment

│

└── conflict_score.csv

│

GO enrichment 

│

└── GO_results/ 

│

KEGG pathway

│

└── KEGG_results/

│

Pseudotime

│

└── pseudotime.h5ad

│

OUTPUT: plots (UMAP_sex.pdf, UMAP_celltype.pdf, GO_barplot.pdf, KEGG_barplot.pdf, pseudotime.pdf)



## Analysis steps
### 1 Quality control
Remove low quality SMART-seq2 cells

Based on:

Lun et al. 2016 Genome Biology
Hagemann-Jensen et al. 2020 Nature Biotechnology

### 2 Normalization

Library size normalization

Method:

Scanpy log normalization

Reference:

Wolf et al. 2018 Genome Biology

### 3 PCA dimensionality reduction

Detect major transcriptional axes

Reference:

Butler et al. 2018 Nature Biotechnology

### 4 UMAP embedding

Nonlinear manifold

Reference:

McInnes et al. 2018 arXiv

### 5 Leiden clustering

Graph community detection

Reference:

Traag et al. 2019 Scientific Reports

### 6 Cell type annotation

Marker genes:

Accessory gland:

Acp36DE
Acp26Aa
Acp62F

Reference:

Chapman et al. 2003 Nature

Germline:

vasa
nanos

Reference:

Lasko & Ashburner 1988 Nature

### 7 Differential expression

Wilcoxon rank test

Reference:

Soneson & Robinson 2018 Nature Methods

### 8 Sexual conflict enrichment

Genes:

Acp
sex peptide
doublesex

Reference:

Chapman et al. 2003 Nature
Arnqvist & Rowe 2005 Sexual Conflict

### 9 GO enrichment

Biological process enrichment

Reference:

Ashburner et al. 2000 Nature Genetics

### 10 KEGG pathway enrichment

Reproductive signaling

Reference:

Kanehisa et al. 2017 Nucleic Acids Research

### 11 Pseudotime

Developmental trajectory

Reference:

Trapnell et al. 2014 Nature Biotechnology 

## How to read results

UMAP:

- clusters = cell types
- separation = dimorphism

Sexual conflict score:

- high male = accessory gland
- high female = ovary

GO enrichment:

- spermatogenesis enrichment = male lineage
- oogenesis enrichment = female lineage

Pseudotime:

- gradient = differentiation
- branch = dimorphism

## Biological interpretation
This analysis identifies:

- male accessory gland lineage
- ovary follicle lineage
- sexual conflict gene expression
- divergence timing
- reproductive protein specialization

## Conclusion

This framework enables evolutionary developmental analysis of sexual dimorphism at single-cell resolution, identifying lineage divergence, reproductive gene expression, and sexual conflict signatures.

## References

Chapman, Tracey, et al. 2003. “The Sex Peptide of Drosophila.” Nature.
https://doi.org/10.1038/nature01656

Wolf, F. Alexander, et al. 2018. “SCANPY.” Genome Biology.
https://doi.org/10.1186/s13059-017-1382-0

Trapnell, Cole, et al. 2014. “Pseudotime Analysis.” Nature Biotechnology.
https://doi.org/10.1038/nbt.2859

Traag, Vincent A., et al. 2019. “Leiden Algorithm.” Scientific Reports.
https://doi.org/10.1038/s41598-019-41695-z

Ashburner, Michael, et al. 2000. “Gene Ontology.” Nature Genetics.
https://doi.org/10.1038/75556

Kanehisa, Minoru, et al. 2017. “KEGG.” Nucleic Acids Research.
https://doi.org/10.1093/nar/gkw1092

Arnqvist, Göran, and Locke Rowe. 2005. Sexual Conflict. Princeton University Press.



