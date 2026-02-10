L1 locus-specific expression analysis in melanoma under stress 

This repository contains the scripts, annotations, and analysis workflows used to study locus-specific LINE-1 (L1) retrotransposon expression in human melanocytes and melanoma (SK-MEL-28) cells under nutrient-deprivation stress. 

The analysis focuses on resolving multi-mapping RNA-seq reads and quantifying L1 expression at individual genomic loci using a probabilistic framework. 

 

Project overview 

Transposable elements, particularly LINE-1 (L1) retrotransposons, constitute a large fraction of the human genome and are normally epigenetically repressed. Cellular stress and malignant transformation can relieve this repression, leading to locus-specific retrotransposon activation. 

In this project, RNA-seq data from primary melanocytes and serum-starved melanoma cells were analysed to: 

    Quantify L1 expression at individual genomic loci 

    Identify differentially expressed L1 elements between conditions 

    Assess chromosomal distribution and enrichment of L1 loci 

    Visualise representative loci using IGV 

 

Software and environment 

Analyses were performed on Linux using the following tools: 

    Bowtie2 – read alignment 

    Samtools – alignment processing 

    Telescope – locus-specific retrotransposon quantification 

    DESeq2 – differential expression analysis 

    R – statistical analysis and plotting 

    IGV – visualisation of genomic loci 

 

Reference genome and annotations 

    Human reference genome: hg38 

    Retrotransposon annotations derived from RepeatMasker 

    Custom annotation file generated for this study: 

l1_only_with_coords_updated.gtf 

Contains curated full-length LINE-1 loci with updated genomic coordinates. 

 

Repository structure 

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
 
