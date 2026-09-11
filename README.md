# Australian White Sheep Muscle Study

Analysis code for the Australian White sheep muscle multi-omics study.

## Download and use

Download [australian-white-sheep-muscle-study.zip](./australian-white-sheep-muscle-study.zip) and extract it locally. The archive contains all 53 original files from the manuscript package's `04_Code` directory, preserving the full directory structure, including `scripts/Figure1` through `scripts/Figure5`, environment specifications, and the script manifest.

This repository contains the specified analysis-code bundle. Figure source data and supplementary tables stored outside `04_Code` are not included.

## Original project instructions
# Australian White sheep multi-omics analysis code

This directory contains the figure-generating and statistical-analysis scripts used for Figures 1–5 and Supplementary Figures S1–S4.
Scripts are grouped by figure and retain their original run order. Generated tables and figures are not duplicated here; the manuscript package contains them in `02_Source_Data`, `03_Supplementary_Tables`, and `01_Final_figures`.

## Configure paths

The deposited scripts use `__PROJECT_ROOT__` and, where needed, `__HMDB_ROOT__` placeholders. Configure a working copy with:

```bash
python scripts/configure_paths.py --root /path/to/aozhoubai --hmdb-root /path/to/HMDB
```

## Environment

```bash
mamba env create -f environment.yml
conda activate australian-white-sheep-multiomics
```

Run scripts in numerical order within each figure directory. Some downstream scripts consume tables produced by earlier scripts. The exact script inventory and original project-relative locations are listed in `analysis_script_manifest.tsv`.

## Statistical conventions

Paired anatomical sites are modeled with animal blocking. Transcriptome analyses use DESeq2; proteome analyses use limma after half-minimum imputation where specified; untargeted metabolite selection uses OPLS-DA VIP > 1 and paired Wilcoxon P < 0.05; targeted fatty acids use paired ANOVA with BH correction. KEGG human-disease and drug-development pathways are removed before BH adjustment where stated in the scripts.

