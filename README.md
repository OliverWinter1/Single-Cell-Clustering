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

## Workflow:
#### -Load the libraries and Anndata object
#### -Inspect the obs (cell metadata)
#### -Inspect the var (gene metadata)
#### -Assign normalised matrix to adata.X
#### -Undergo quality control
#### -Select HVG (Highly Variables Genes)
- We used the top 1000 genes that varied the most between cells
- This provided us with smaller dimensionality whilst allowing for the most influencial genes to be used in neighboring/clustering
#### -Undergo feature selection and PCA
- PCA was used to further reduce dimensionality
- 50 PCA components capture major patterns in variation
#### -Construct nearest neighbor plots
- Built using the PCA representation of the data
- It connects cells with similar gene expression profiles and maps them close together
#### -Generate UMAP plot
#### -Perform clustering
- We used Leiden clustering to group transcriptionaly similar cells
#### -Reasses quality control and remove error cells
- Quality control metrics were reassessed after clustering to identify possible error clusters.
- Clusters 2 and 9 were removed because they showed unusually high n_counts in comparison, suggesting they may represent error cells or possible doublets (where 2 cells have grouped together)
#### -Rerun PCA, neighbours, UMAP, and clustering
#### -Perform marker gene analysis and annotate clusters
- The most common genes found in each cluster were identified 
- Known PBMC marker genes found in the dictionary were used to label cell clusters with a tentative cell type

- The dictionary used is shown below:
- Monocytes: `LYZ`, `S100A8`, `S100A9`, `FCN1`, `CD14`, `FCGR3A`
- B cells: `MS4A1`, `CD79A`, `CD79B`, `IGHD`, `IGHM`
- T cells: `CD3D`, `CD3E`, `TRAC`, `IL7R`
- CD8/NK cells: `NKG7`, `GNLY`, `GZMA`, `GZMB`, `CCL5`
- pDCs: `IL3RA`, `TCF4`, `PLD4`

## Figures
### Figure 1
The violin plot on the left shows the distribution of how many genes were detected in each cell. The plot on the right shows the total counts of each cell, higher values would potentially mean the cell was analysed to a higher quality (unless it was a doublet).
### Figure 2
The plot shows the contribution of each PC towards the overall variation. The y axis is log10 of variation
### Figure 3
Nearest neighbor graph using PC1 and PC2. This connect each cell to its most similar 15 using its gene expression profile and maps them in a 2D plane
### Figure 4
UMAP plot showing 3 distinct populations of cells and a few smaller populations
### Figure 5
Leiden clustering plot with standard resolution showing 15 clusters
### Figure 6
Leiden clustering plot with 0.3 resolution showing 10 clusters
### Figure 7
Uses quality control metrics to assess the n_counts, total_counts and n_genes_by_counts of each cluster to see if any error cells persist
### Figure 8
A violin plot of each cluster comparing the n_counts and n_genes_by_counts
### Figure 9
A new Leiden clustering profile with the new filtered cells
### Figure 10
The plots show the top 5 genes and their contribution towards each clusters variance profile
### Figure 11
The dotplot uses a PBMC marker gene dictionary to allow interpretation of which genes correlate to which cell type
### Figure 12
The Leiden Clusters at 0.3 resolution fully labelled with the cell types the cluster represents
### Figure
### Figure
### Figure

## Results

