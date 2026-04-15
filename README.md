# scRNA-seq Analysis Pipeline: End-to-End Computational Workflow

## Overview

This repository contains a modular computational pipeline for the analysis of single-cell RNA sequencing (scRNA-seq) data. The workflow encompasses the entire primary and secondary analysis lifecycle, transitioning from raw sequencing reads to the identification of transcriptionally distinct biological cell populations.

The project is structured into three distinct phases:

1. **Upstream Processing** — Sequence alignment and count matrix generation.
2. **Downstream Analysis** — Statistical quality control, dimensionality reduction, and unsupervised clustering.
3. **Data Management** — Implementation of the AnnData object standard for scalable bioinformatics.

---

## Repository Architecture

```
.
├── 01_scrna-preprocessing-10x/    # STARsolo configuration and DropletUtils scripts
├── 02_basic-scrna-tutorial/      # Scanpy-based exploratory data analysis and clustering
├── 03_anndata-tutorial/           # Notebooks detailing data structure manipulation
└── README.md
```

---

## Technical Methodology

### Phase 1: Count Matrix Generation

The initial phase focuses on transforming raw FASTQ files into a digital expression matrix using the 1k PBMC (10x Genomics v3) dataset.

- **Alignment** — Implementation of STARsolo for high-throughput read mapping.
- **Quality Control** — Utilization of MultiQC for aggregate sequencing metrics.
- **Ambient RNA Filtering** — Application of the EmptyDrops algorithm via DropletUtils to statistically differentiate valid cell-containing droplets from ambient RNA background.

### Phase 2: Secondary Analysis with Scanpy

This phase leverages the Scanpy ecosystem to perform biological interpretation and feature extraction.

- **Normalization** — Log-transformation and scaling of raw counts.
- **Feature Selection** — Identification of Highly Variable Genes (HVGs) to reduce noise.
- **Dimensionality Reduction** — Execution of Principal Component Analysis (PCA) followed by Uniform Manifold Approximation and Projection (UMAP) for visualization.
- **Clustering** — Application of the Leiden community detection algorithm to define cell identities.

### Phase 3: AnnData Architecture

A focused study on the AnnData (Annotated Data) format, ensuring data integrity and reproducibility.

- **Metadata Integration** — Mapping cell-level observations (`obs`) and gene-level variables (`var`).
- **Efficiency** — Implementation of sparse matrix storage and on-disk data management for large-scale datasets.

---

## Results and Findings

### Quality Control Metrics

The filtering process successfully identified **74 high-quality cells** from the initial subset. The distribution of mitochondrial read fractions and unique molecular identifier (UMI) counts were within expected parameters for peripheral blood mononuclear cells, ensuring the exclusion of apoptotic or damaged cells.

### Dimensionality Reduction and Clustering

The UMAP projection revealed distinct topological groupings of cells. Using the Leiden algorithm, the pipeline identified major immune subpopulations.

**Biological Identity Mapping:**

| Cell Type | Marker Genes |
|-----------|--------------|
| T Cells | `CD3D`, `CD3E` |
| B Cells | `CD79A`, `MS4A1` |
| Monocytes | `LYZ`, `CD14` |

<!-- Insert UMAP_clustering_plot.png -->

### Marker Gene Identification

Rank-sum testing (Wilcoxon) was utilized to identify the top differentially expressed genes for each cluster, providing statistical validation for the assigned cell identities.

<!-- Insert dotplot_marker_genes.png -->

---

## Implementation and Dependencies

### Core Technologies

| Component | Tool / Version |
|-----------|---------------|
| Language | Python 3.10 |
| Analysis Framework | Scanpy, AnnData |
| Bioinformatics Tools | STARsolo, MultiQC, DropletUtils |
| Data Handling | Pandas, NumPy, SciPy |

### Environment Setup

To ensure reproducibility, use the following commands to initialize the computational environment:

```bash
# Environment initialization
conda create -n scrna_pipeline python=3.10 -y
conda activate scrna_pipeline

# Dependency installation
pip install scanpy anndata matplotlib seaborn pandas jupyter
```

---

## Conclusion

This workflow demonstrates a rigorous approach to scRNA-seq analysis, prioritizing statistical accuracy and structured data management. The modular nature of the pipeline allows for easy adaptation to larger datasets or more complex multi-sample integrations, such as batch correction or trajectory inference.
