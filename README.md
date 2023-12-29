Analysis of 10x gene expression and BCR sequence data associated with Verma et al. 2023 (https://doi.org/10.1101/2023.10.13.562275)

Matt Dufort



This set of scripts performs the analyses and generates the visualizations presented in Verma et al. 2023, "Antigen-level resolution of commensal-specific B cell responses enabled by phage-display screening and B cell tetramers".

The scripts are numbered in the order that they need to be run. Adjustments to paths for files and executables may be necessary in order for the scripts to run to completion.  Dependencies are [R version 4.1 or higher](https://cran.r-project.org/) and [python 3](https://www.python.org/downloads/).  The analyses of BCR sequences use several modules from the [Immcantation toolkit](https://immcantation.readthedocs.io/en/stable/).  Necessary R packages are installed and loaded by the scripts.

The "aggregateMice" versions of the scripts identify BCR clones and compare BCR sequences across mice. This generates clones that are not strictly clonal in the sense of being derived from a single ancestral B cell, but is informative for identifying similarities in BCRs that arise in different mice, and detection of "public" clones.

The instructions for running the scripts are detailed below.



1. Download files and place them in folder accessible by all scripts
2. Run 1_load_QC_demultiplex_clean.Rmd
   1. This will generate a .RData file and a set of .fasta files

3. Run Immcantation / Change-O steps on sequences from each mouse
   1. Run 2_runChangeO.sh
      1. Process follows tutorial at https://changeo.readthedocs.io/en/stable/examples/10x.html, with separate steps for analysis of clones in each mouse

   2. If desired, run 2_runChangeO.sh on AggregateMice outputs
      1. This requires modifying the file locations within the script to point to the AggregateMice versions
      2. This generates a set of clones aggregated across mice, which doesn't make sense for lineage purposes but is informative for identification of public clones

4. Run 3_analyze_BCRs.Rmd
