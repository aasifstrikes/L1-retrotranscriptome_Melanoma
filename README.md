**L1-retrotranscriptome_Melanoma**
![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Version](https://img.shields.io/badge/version-v1.0.0-brightgreen)
![Status](https://img.shields.io/badge/status-dissertation%20complete-success)
![DOI](https://img.shields.io/badge/DOI-pending-lightgrey)
Locus-specific LINE-1 expression analysis in melanoma under stress
**Overview**

This repository contains the computational workflow, annotation files, and statistical analyses used to investigate locus-specific LINE-1 (L1) retrotransposon expression in human melanocytes and SK-MEL-28 melanoma cells under nutrient-deprivation stress.

Transposable elements, particularly L1 retrotransposons, constitute a substantial fraction of the human genome and are typically epigenetically repressed. Cellular stress and malignant transformation can relieve this repression, resulting in locus-specific activation.

This project applies probabilistic multi-mapping resolution to quantify L1 expression at single-locus resolution and compare transcriptional patterns between normal and tumor-derived cells.

**Study Objectives**

Quantify expression of full-length L1 elements at individual genomic loci

Identify differentially expressed L1 loci between melanocytes and serum-starved melanoma cells

Assess chromosomal enrichment of L1 loci relative to genome size

Visualize representative loci to distinguish locus-specific transcription from host gene transcription

**Experimental Context**

RNA-seq data were generated from:

Primary human melanocytes (control condition)

SK-MEL-28 melanoma cells subjected to serum starvation (nutrient-deprivation stress)

All wet-lab procedures were performed externally; this repository contains only the bioinformatic analysis workflow.

**Computational Workflow**

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

**Software Environment**

Analysis performed on Linux using:

Bowtie2

Samtools

Telescope

Python 3

R (DESeq2, pvclust, ggplot2)

IGV
Reproducibility is supported through script-based automation of alignment, quantification, and statistical analysis.

**Reference Genome and Annotation**

Human reference genome: hg38

RepeatMasker-derived retrotransposon annotations

Custom curated annotation file:

annotations/l1_only_with_coords_updated.gtf


This file contains full-length L1 loci with updated genomic coordinates to ensure locus-specific quantification.

**Repository Structure**
.
├── annotations/
│   └── l1_only_with_coords_updated.gtf
├── scripts/
│   ├── tpm.py
│   ├── deseq2_analysis.R
│   └── chromosomal_enrichment.R
├── results/
│   ├── differential_expression_tables/
│   ├── chromosomal_analysis/
│   └── figures/
├── igv/
│   ├── igv_batch_files/
│   └── snapshots/
└── README.md

**Key Analytical Components**
Differential Expression

951 L1 loci were identified as differentially expressed under defined statistical thresholds (FDR < 0.05; |log₂FC| ≥ defined cutoff).

**Chromosomal Distribution**

Both total and differentially expressed L1 loci deviate significantly from genome-proportional expectations, indicating non-random chromosomal distribution patterns.
**
Locus-Specific Validation**

IGV inspection confirms that selected loci exhibit discrete transcriptional boundaries, supporting locus-specific expression rather than purely host gene-driven transcription.

**Reproducibility Notes**

Full reproduction of the alignment and quantification pipeline requires substantial storage capacity (≥1 TB recommended).

Raw FASTQ files are not included in this repository.

**Citation**

If using this workflow or annotation strategy, please cite:

Bendall ML et al. (2019). Telescope: Characterization of the retrotranscriptome by accurate estimation of transposable element expression. PLOS Computational Biology.
