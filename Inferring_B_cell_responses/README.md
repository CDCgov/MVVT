# Molecular Virology and Vaccines Team (MVVT) B Cell Receptor (BCR) Analysis Workflows

## Overview

This repository contains Jupyter notebook workflows developed by the Molecular Virology and Vaccines Team, Immunology and Pathogenesis Branch, Influenza Division, Centers for Disease Control and Prevention (CDC) for analyzing B cell receptor (BCR) repertoire sequencing data. The notebooks support BCR clonotype assignment and influenza-associated antibody motif identification using Adaptive Immune Receptor Repertoire ([AIRR-](https://docs.airr-community.org)) Community-compliant BCR annotation data.

The repository currently includes three workflows:

---

## 1. `MVVT_BCR_heavy_chain_clonotype_assignment.ipynb`

Assigns clonotypes from bulk BCR heavy-chain repertoire sequencing data using a network-based clustering approach.

### Method

- Groups sequences by:
  - Heavy-chain V gene
  - Heavy-chain J gene
  - CDR3 amino acid sequence length
- Constructs sequence similarity networks
- Assigns clonotypes to sequences sharing **≥80%** CDR3 amino acid sequence identity

### Input

A tab-delimited file containing Adaptive Immune Receptor Repertoire (AIRR) Community-compliant heavy-chain BCR annotations.

### Output

A tab-delimited file containing heavy-chain BCR sequences with clonotype assignments reported in the `clonotype_family` column.

---

## 2. `MVVT_singlecell_paired_BCR_clonotype_assignment.ipynb`

This notebook assigns clonotypes from single-cell B cell receptor (BCR) repertoire data using paired heavy- and light-chain sequences.

### Method

Cells are grouped according to:

- Heavy-chain V gene and J gene usage
- Light-chain V gene and J gene usage
- Heavy- and light-chain CDR3 amino acid sequence length

Within each group, clonotypes are inferred using a network-based clustering approach. Cells with paired BCR sequences sharing **≥80%** CDR3 amino acid sequence identity are assigned to the same clonotype.

### Input

A tab-delimited file containing paired heavy- and light-chain BCR annotations.

**Required column naming convention**

- Heavy-chain columns must be prefixed with `IGH_`
- Light-chain columns must be prefixed with `IGL_`

### Output

A tab-delimited file containing paired BCR sequences with assigned clonotype identifiers reported in the `clonotype_family` column.

---

## 3. `BCR_functional_motif_search.ipynb`

This notebook identifies BCR sequences containing previously published influenza-associated antibody sequence motifs.

### Method

The workflow compares BCR sequences against a curated collection of published influenza-associated antibody sequence motifs. Depending on the reported definition of each motif, the search may use one or more of the following features:

- Heavy- and/or light-chain V gene calls
- Heavy- and/or light-chain J gene calls
- CDR3 amino acid sequence motifs
- CDR2 amino acid sequence motifs
- Translated nucleotide sequences, where required

Different published motifs may require matching a subset or combination of these features.

### Input

A tab-delimited file containing Adaptive Immune Receptor Repertoire (AIRR) Community-compliant BCR annotations.

**Required column naming convention**

- Heavy-chain columns must be prefixed with `IGH_`
- Light-chain columns must be prefixed with `IGL_`

### Output

A tab-delimited file containing antibody sequences with at least one predicted influenza-associated motif assignment in the `motif_search_results` column.

---

## Repository Contents

```
notebooks/
    MVVT_BCR_heavy_chain_clonotype_assignment.ipynb
    MVVT_singlecell_paired_BCR_clonotype_assignment.ipynb
    BCR_functional_motif_search.ipynb
```

## Input Data

All workflows require tab-delimited BCR annotation files.

Input files should follow the AIRR Community data standard where applicable.

For paired-chain analyses:

- Heavy-chain columns must be prefixed with `IGH_`
- Light-chain columns must be prefixed with `IGL_`

Example input files are provided in the `input/` directory.

## Output

Each notebook generates tab-delimited output files containing workflow-specific results.

Typical outputs include:

- Assigned clonotype identifiers (reported in the `clonotype_family` column)
- Predicted influenza-associated motif assignments (reported in the `motif_search_results` column)

Example outputs are available in the `output/` directory.

## Getting Started

### Requirements

- Python 3.9.13 or later
- Jupyter Notebook or JupyterLab

### Running the notebooks

1. Clone this repository.
2. Launch Jupyter Notebook or JupyterLab.
3. Open the notebook of interest.
4. Update input and output file paths as needed.
5. Execute all notebook cells.

## Contacts

| Role | Contact |
|---|---|
| Team Lead | Dr. Ian York (ite1@cdc.gov) |
| Maintainer | Sujatha Seenu (iun1@cdc.gov) |
| Other Contacts | Dr. Jason Wilson (vhd7@cdc.gov); Dr. Jureka Alexander (smy6@cdc.gov) |
