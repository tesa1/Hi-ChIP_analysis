# Analyze Hi-ChIP data

This is a manual of how to use publically available tools to analyze Hi-ChIP data

Steps for analysis of Hi-ChIP data using HiC Pro:
  - Align to genome (uses bowtie2, so first we need to index local hg19.fa file with bowtie2
  - HiC filtering (uses a file of in silico enzyme restricted genome)
  - Quality checks of the data by running R ot make plots
  - Make contact maps
  
 ## Installation and use  ##
Hi-C Pro can be installed here from https://github.com/nservant/HiC-Pro
 
 
Using singularity shell on darwin

 ```bash
 singularity shell hicpro_latest_ubuntu.img
 HiC-Pro -h
```
