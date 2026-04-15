# Section 3: AnnData

## Objective

To understand and demonstrate the use of the AnnData data structure, which is the standard format for storing single-cell RNA-seq data in the Python ecosystem.

## Tools Used

| Tool | Purpose |
|------|---------|
| Python 3.10 | Programming language |
| AnnData | Core data structure for scRNA-seq |
| Jupyter Notebook | Interactive computing environment |
| NumPy / pandas | Numerical computation and data frames |

## What is AnnData?

AnnData (Annotated Data) is a Python package providing a data structure designed specifically for single-cell data. It stores:
- **X**: the main data matrix (cells × genes)
- **obs**: per-cell metadata (e.g., cell type, quality metrics)
- **var**: per-gene metadata (e.g., gene names, chromosome)
- **obsm / varm**: dimensionality reductions (PCA, UMAP)
- **uns**: unstructured metadata (e.g., color palettes, parameters)

## Step-by-Step Summary

**1. Creating an AnnData Object**
An AnnData object was created from a NumPy array representing a small example count matrix.

**2. Adding Metadata**
Cell-level (`.obs`) and gene-level (`.var`) metadata were attached as pandas DataFrames.

**3. Subsetting Data**
Data was subset by selecting specific cells and genes using standard indexing syntax.

**4. Saving and Loading**
The AnnData object was saved to disk in `.h5ad` format (HDF5-based), which is the standard file format for scRNA-seq data.

**5. Tutorial 2 (scverse)**
The scverse AnnData tutorial was followed, reinforcing the same concepts with additional examples of views, concatenation, and working with large datasets.

## Output 

Notebooks: Saved with all executed outputs (.ipynb). 


## images

| images| Description |
|------------|-------------|
| `images/01_anndata_created.png` | AnnData object created and printed |
| `images/02_metadata_added.png` | `.obs` and `.var` DataFrames displayed |
| `images/03_data_sliced.png` | Subset of AnnData shown |

## Tutorial References

- Tutorial 1: https://anndata.readthedocs.io/en/latest/tutorials/notebooks/getting-started.html
- Tutorial 2: https://scverse-tutorials.readthedocs.io/en/latest/notebooks/anndata_getting_started.html
