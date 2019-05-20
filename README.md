# Analyze Hi-ChIP data

This is a manual of how to use publically available tools to analyze Hi-ChIP data

Steps for analysis of Hi-ChIP data using HiC Pro:
  - Align to genome (uses bowtie2, so first we need to index local hg19.fa file with bowtie2)
  - HiC filtering (uses a file of in silico enzyme restricted genome)
  - Quality checks of the data by running R to make plots
  - Make contact maps
  
 ## Installation and use of HiC-Pro ##
Hi-C Pro can be installed here from https://github.com/nservant/HiC-Pro

On darwin, using downloaded version of HiC-Pro.2.11 from https://github.com/nservant/HiC-Pro/releases and installed in /home/t.severson/tools/HiC-Pro-2.11.1.install/bin/. Config file was changed to suit the necessary requirements (bowtie2 and samtools 1.9 locations).

Move fastq sample folders into folder h3k27ac_rawdata. 

 ```bash
/home/t.seversontools/HiC-Pro-2.11.1.install/bin/HiC-Pro -i h3k27ac_rawdata/ -o h3k27ac_outputs -c config-hicpro.txt
```

This will create h3k27ac_outputs folder with mapping and HiC analysis results
