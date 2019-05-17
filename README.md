# Analyze Hi-ChIP data

This is a manual of how to use publically available tools to analyze Hi-ChIP data

Steps for analysis of Hi-ChIP data using HiC Pro:
  - Align to genome (uses bowtie2, so first we need to index local hg19.fa file with bowtie2)
  - HiC filtering (uses a file of in silico enzyme restricted genome)
  - Quality checks of the data by running R to make plots
  - Make contact maps
  
 ## Installation and use  ##
Hi-C Pro can be installed here from https://github.com/nservant/HiC-Pro

 
Download the singularity image file: https://zerkalo.curie.fr/partage/HiC-Pro/singularity_images/hicpro_latest_ubuntu.img
Move fastq sample folders into folder h3k27ac_rawdata. Change config file to suit the necessary requirements.

Using singularity shell to run image file on darwin

 ```bash
 singularity shell hicpro_latest_ubuntu.img
 HiC-Pro -i h3k27ac_rawdata/ -o h3k27ac_outputs -c config-hicpro.txt
```


