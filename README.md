**L1-retrotranscriptome_Melanoma**
---

**Dissertation Project | Locus-Specific Retrotranscriptome Analysis | hg38**

---
![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Version](https://img.shields.io/badge/version-v1.0.0-brightgreen)
![Status](https://img.shields.io/badge/status-dissertation%20complete-success)
![DOI](https://img.shields.io/badge/DOI-pending-lightgrey)
Locus-specific LINE-1 expression analysis in melanoma under stress

## Overview

This repository contains the computational workflow, annotation files, and statistical analyses used to investigate locus-specific LINE-1 (L1) retrotransposon expression in human melanocytes and SK-MEL-28 melanoma cells under nutrient-deprivation stress.

Transposable elements, particularly L1 retrotransposons, constitute a substantial fraction of the human genome and are typically epigenetically repressed. Cellular stress and malignant transformation can relieve this repression, resulting in locus-specific activation.

This project applies probabilistic multi-mapping resolution to quantify L1 expression at single-locus resolution and compare transcriptional patterns between normal and tumor-derived cells.

## Study Objectives

Quantify expression of full-length L1 elements at individual genomic loci

Identify differentially expressed L1 loci between melanocytes and serum-starved melanoma cells

Assess chromosomal enrichment of L1 loci relative to genome size

Visualize representative loci to distinguish locus-specific transcription from host gene transcription

## Experimental Context

RNA-seq data were generated from:

Primary human melanocytes (control condition)

SK-MEL-28 melanoma cells subjected to serum starvation (nutrient-deprivation stress)

All wet-lab procedures were performed externally; this repository contains only the bioinformatic analysis workflow.

## Computational Workflow

The analysis pipeline consists of the following stages:

Read Alignment
Paired-end RNA-seq reads aligned to hg38 using Bowtie2 with multi-mapping retention enabled.

Alignment Processing
SAM/BAM processing using Samtools.

Locus-Specific Quantification
Telescope applied to probabilistically assign multi-mapping reads to their most likely genomic L1 locus using an Expectation–Maximization algorithm.

Normalization and Differential Expression

TPM calculation via custom Python script

Differential expression analysis using DESeq2

Multiple testing correction via Benjamini–Hochberg FDR

Chromosomal Enrichment Analysis
Observed L1 locus counts per chromosome compared against genome-proportional expectations using chi-squared tests.

IGV Visualization
Selected loci inspected to evaluate read coverage boundaries and distinguish autonomous L1 transcription from host gene co-transcription.

## Software Environment

Analysis performed on Linux using:

Bowtie2

Samtools

Telescope

Python 3

R (DESeq2, pvclust, ggplot2)

IGV
Reproducibility is supported through script-based automation of alignment, quantification, and statistical analysis.

## Reference Genome and Annotation

Human reference genome: hg38

RepeatMasker-derived retrotransposon annotations

Custom curated annotation file:

annotations/l1_only_with_coords_updated.gtf


This file contains full-length L1 loci with updated genomic coordinates to ensure locus-specific quantification.

## Repository Structure
.
├── annotations/
│   └── l1_only_with_coords_updated.gtf
├── scripts/
│   ├── tpm.py
│   ├── deseq2_analysis.R
│   └── chromosomal_enrichment.R
├── results/
│   ├── tables/
│   ├── figures/
│   └── chromosomal_analysis/
├── igv/
│   ├── igv_batch_files/
│   └── snapshots/
└── README.md
## File Descriptions

## Annotations
- `annotations/l1_only_with_coords_updated.gtf`  
  Curated full-length LINE-1 (L1) loci derived from RepeatMasker (hg38).  
  Used as input for Telescope to enable locus-specific retrotransposon quantification.

## Scripts
- `tpm.py` – Calculation of TPM-normalised expression values.
- `deseq2_analysis.R` – Differential expression analysis using DESeq2.
- `chromosomal_enrichment.R` – Statistical assessment of chromosomal distribution and enrichment of L1 loci.

## Results
- `results/tables/` – Processed differential expression tables and statistical test outputs.
- `results/figures/` – MA plots, clustering plots, enrichment plots, and other publication-ready figures.

### IGV Snapshots
- `igv/snapshots/` – Representative locus-level visual validation of selected L1 elements.

## Key Analytical Findings

### Differential Expression

A total of 951 L1 loci were identified as differentially expressed under defined statistical thresholds (FDR < 0.05 and specified |log₂FC| cutoff), indicating stress-associated locus-specific transcriptional reprogramming.

## Chromosomal Distribution

Both total and differentially expressed L1 loci deviate significantly from genome-proportional expectations (chi-squared test), indicating a non-random chromosomal distribution of stress-responsive L1 elements.

## Locus-Specific Validation

Manual inspection of representative loci using IGV confirmed discrete read coverage boundaries consistent with autonomous L1 transcription at selected loci.

## Reproducibility Notes

This repository contains all scripts, processed result tables, and representative visual outputs necessary to reproduce the statistical analyses presented in the associated dissertation.

Raw sequencing data (FASTQ/BAM files) are not included due to size constraints.

Full pipeline reproduction requires:
- Linux-based environment
- Bowtie2
- Samtools
- Telescope
- R (DESeq2 and required packages)
- Python 3

Full reproduction of the alignment and quantification pipeline requires substantial storage capacity (≥1 TB recommended).

## Citation

If using this workflow or annotation strategy, please cite:

Bendall ML et al. (2019). Telescope: Characterization of the retrotranscriptome by accurate estimation of transposable element expression. PLOS Computational Biology.
Love MI et al. (2014). Moderated estimation of fold change and dispersion for RNA-seq data with DESeq2. Genome Biology.
