# Process Hi-ChIP data using HiC-Pro

This is a manual of how to use publically available tools to analyze Hi-ChIP data

Steps for processing of Hi-ChIP data using HiC Pro:
  - Align to genome (uses bowtie2, so first we need to index local hg19.fa file with bowtie2)
  - HiC filtering (uses a file of in silico enzyme restricted genome)
  - Quality checks of the data by running R to make plots
  - Make contact maps
  
 ## Installation and use of HiC-Pro ##
Hi-C Pro can be installed here from https://github.com/nservant/HiC-Pro

On darwin, using downloaded version of HiC-Pro.2.11 from https://github.com/nservant/HiC-Pro/releases and installed in /home/t.severson/tools/HiC-Pro-2.11.1.install/bin/. Config file was changed to suit the necessary requirements (bowtie2 and samtools 1.9 locations).

Move fastq sample folders into folder h3k27ac_rawdata. 

 ```bash
/home/t.severson/tools/HiC-Pro-2.11.1.install/bin/HiC-Pro -i h3k27ac_rawdata/ -o h3k27ac_outputs -c config-hicpro.txt
```

This will create h3k27ac_outputs folder with mapping and HiC analysis results


## Installation and use of hichipper for HiC-Pro results ##

Steps for analyzing of Hi-ChIP data from HiC Pro using hichipper using a sample manifest file (.yaml).
Using called peaks and restriction fragment locations as input and the output from HiC-Pro output that can be used to:
  - Determine library quality
  - Visualize loops with strength andconfidence metrics

Install hichipper using instructions from: https://hichipper.readthedocs.io/en/latest/

```bash
virtualenv -p /usr/bin/python2.7 venv
source venv/bin/activate
pip install hichipper
hichipper --version
```

Run hichipper on the h3k27ac_outputs folder from HiC-Pro.
```bash
hichipper --out h3k27ac_hichipper --make-ucsc  hichipper.yaml
```


 ## Running a downsample experiment on the data ##
 
Need to use HTSeq to downsample the paired-end fastq files 

```bash
# install htseq with bioconda
conda create -c bioconda --name htseq htseq
conda activate htseq
```

For downsampling to 25% of reads
```bash
gunzip sample_R1.fastq.gz
gunzip sample_R1.fastq.gz
python subsample.py 0.25 sample_R1.fastq sample_R2.fastq sample_R1_ds25.fastq sample_R2_ds25.fastq
gzip -c sample_R1_ds25.fastq > sample_R1_ds25.fastq.gz
gzip -c sample_R2_ds25.fastq > sample_R2_ds25.fastq.gz
```


Run HiC-Pro on the downsampled samples

```bash
/home/t.severson/tools/HiC-Pro-2.11.1.install/bin/HiC-Pro -i ds_25/ -o ds_25_outputs -c config-hicpro.txt
````
