# Single-Cell-Transcriptomes-Autoencoder
Autoencoder for Latent Representation of Single-Cell Transcriptomes

## Overview

This project applies an autoencoder neural network to compress high-dimensional single-cell RNA sequencing (scRNA-seq) data into a lower-dimensional latent space. The resulting embeddings capture key patterns in gene expression and can be used for downstream analyses such as PCA, UMAP visualization, or unsupervised clustering of cell types.

The autoencoder is implemented in PyTorch and trained to reconstruct normalized log gene expression profiles from a 765-gene panel across thousands of single cells.

---

## Data

- `processed_counts.csv`: Log-normalized RNA-seq read counts.
  - Rows: individual cells, each identified by a unique barcode (e.g., `AAAGCCTGGCTAAC-1`)
  - Columns: genes (e.g., `HES4`, `LYZ`, `IL7R`), totaling 765 genes

- `label.csv`: Contains ground-truth cell type annotations for each barcode (e.g., `CD14+ Monocyte`, `Naive CD4+ T`)

---

## Model Architecture

The autoencoder compresses the 765-dimensional gene expression vector into a 32-dimensional latent space and reconstructs it back. The architecture is:

Encoder:
Input (765)
→ Linear(128) → ReLU
→ Linear(32) → ReLU ← Latent space

Decoder:
→ Linear(128) → ReLU
→ Linear(765) → Sigmoid ← Reconstructed gene expression

The model is trained using **mean squared error (MSE)** between the input and reconstruction.

---

## Purpose

- Reduce dimensionality of scRNA-seq data while preserving important expression patterns
- Enable PCA, t-SNE, or UMAP visualization using compressed embeddings
- Serve as a feature extractor for downstream tasks such as clustering or classification

Author
Kate Barouch
MEng in Bioengineering, UC Berkeley
Specializing in Computational Biology & Machine Learning for Genomics
