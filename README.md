# Single Cell Clustering Project

## Project overview
This project is a single-cell RNA-seq analysis workflow using Scanpy and Anndata

The aim of this project is to analyse a 1k PBMC single-cell dataset, assign the cells into similar groups and then assign cell-type labels using marker genes

The stages of the workflow include: Preprocessing; Quality Control; Feature Selection and PCA; Nearest Neighboring; Clustering; Cell Filtering; Marker Gene Annotation

### Biological Aim
The bioligcal aim is to provide a workflow that can be used to analyse changes to the makeup of PMBC cells.

PBMC cells are blood cells that usually consist of immune cells (such as monocytes, T and B cells and dendritic cells).

## Dataset
The dataset used in this project is a PBMC single-cell RNA-seq dataset stored in `.h5ad` AnnData format.

The loaded dataset contained:

- 1,087 cells
- 15,099 genes
- raw counts stored in adata.layers["counts"]
- normalised expression values stored in adata.layers["normalized"]

The normalised expression layer was assigned to adata.X for downstream Scanpy analysis.

## Workflow

The scanpy workflow went as followed

-Load the libraries and Anndata object
-Inspect the obs (cell metadata)
-Inspect the var (gene metadata)
-Assign normalised matrix to adata.X
-Undergo quality control
-Select HVG (Highly Variables Genes)
-Undergo feature selection and PCA
-Construct nearest neighbor plots
-Generate UMAP plot
-Perform clustering
-Reasses quality control and remove error cells
-Rerun PCA, neighbours, UMAP, and clustering
-Perform marker gene analysis and annotate clusters
