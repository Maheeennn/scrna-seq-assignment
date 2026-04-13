
# Section 2 — Basic scRNA-seq Analysis with Scanpy

This repository presents a complete workflow for single-cell RNA sequencing (scRNA-seq) data analysis using the **Scanpy** library in Python. The analysis is performed on a Peripheral Blood Mononuclear Cells (PBMC) dataset and follows standard preprocessing, dimensionality reduction, clustering, and marker gene identification steps.

---

##  Tutorial References

* **Original Tutorial:** [Scanpy Basic Tutorial (GitHub)](https://github.com/scverse/scanpy-tutorials/blob/main/basic-scrna-tutorial.ipynb)
* **Updated Tutorial:** [Refined Version (GitHub)](https://github.com/tahashmi/algos/blob/main/basic-scrna-tutorial_updated.ipynb)

---

##  Dataset Description

The dataset consists of **Peripheral Blood Mononuclear Cells (PBMCs)**, which include essential immune cells such as T cells, B cells, and monocytes. 

Single-cell RNA sequencing enables analysis of gene expression at the individual cell level, allowing:
* **Identification** of different cell types.
* **Understanding** of cellular heterogeneity.
* **Detection** of rare cell populations.

---

## Environment Setup

### 1. Install Anaconda
* Download from: [Anaconda.com](https://www.anaconda.com/download)
* Install using default settings and launch **Anaconda Navigator**.

### 2. Create and Activate Environment
Run the following commands in your terminal or Anaconda Prompt:

```bash
# Create the environment
conda create -n scrna python=3.10

# Activate the environment
conda activate scrna

# Install dependencies
pip install scanpy jupyter matplotlib seaborn pandas
```

### 3. Running the Notebook
```bash
cd scrna-work
jupyter notebook
```
* Open the notebook in your browser.
* Run each cell using **Shift + Enter**.
* Ensure each cell completes execution before proceeding.

---

##  Analysis Workflow

### Data Loading
The dataset is loaded into an **AnnData** object, which stores gene expression data (`X`) along with cell metadata (`obs`) and gene metadata (`var`).

### Quality Control (QC)
Cells and genes are filtered based on:
* Number of genes per cell.
* Total counts per cell.
* Mitochondrial gene percentage.
* *Low-quality cells are removed to improve analysis accuracy.*

### Normalization
Gene expression values are normalized to remove technical variation and ensure cells are statistically comparable.

### Highly Variable Genes (HVG)
Genes with high variability across cells are selected for downstream analysis, as they capture the most meaningful biological differences.

### Dimensionality Reduction
* **PCA:** Reduces high-dimensional data while preserving the most important variance.
* **UMAP:** Projects data into 2D space for visualization. Cells that cluster together represent similar cell types.

### Clustering
Cells are grouped into clusters based on gene expression similarity. Each cluster represents a potential cell type.

### Marker Gene Identification
Marker genes are identified for each cluster to assign biological meaning and distinguish between different cell populations.

---

## Repository Contents

### Notebooks (`scrna-work/`)
The following notebooks with complete outputs are stored in the `scrna-work/` directory:
* `basic-scrna-tutorial_completed.ipynb`
* `basic-scrna-tutorial_updated_completed.ipynb`

### Screenshots (`images/`)
Key steps of the analysis are documented with screenshots:

| Step | File Name | Description |
| :--- | :--- | :--- |
| 01 | `01_data_loaded.png` | Dataset loaded into AnnData object |
| 02 | `02_qc_violin_plot.png` | Quality control violin plots |
| 03 | `03_highly_variable_genes.png` | Highly variable genes plot |
| 04 | `04_pca_variance.png` | PCA variance ratio plot |
| 05 | `05_umap_clusters.png` | UMAP cluster visualization |
| 06 | `06_marker_genes.png` | Marker gene visualization |

---

## Challenges and Observations

* **Environment Setup:** Required proper installation of specific dependencies (e.g., leidenalg).
* **Performance:** Some steps were computationally intensive and required significant processing time.
* **Visualization:** Understanding PCA and UMAP plots required conceptual learning of dimensionality reduction.
* **Organization:** Maintaining a clear directory structure was vital for reproducibility.

---

## Repository Structure

```text
basic-scrna-tutorial/
├── images/
│   ├── 01_data_loaded.png
│   ├── 02_qc_violin_plot.png
│   ├── 03_highly_variable_genes.png
│   ├── 04_pca_variance.png
│   ├── 05_umap_clusters.png
│   └── 06_marker_genes.png
├── scrna-work/
│   ├── basic-scrna-tutorial_completed.ipynb
│   ├── basic-scrna-tutorial_updated_completed.ipynb
└── README.md
```

---

## Conclusion

This section demonstrates a complete scRNA-seq analysis workflow using Scanpy. The pipeline shows how raw gene expression data can be processed and interpreted to identify meaningful biological patterns, such as distinct cell populations and their specific marker genes.
```
