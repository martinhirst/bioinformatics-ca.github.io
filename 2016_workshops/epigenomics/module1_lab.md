# Module 1: Introduction to ChIP sequencing & analysis 

## Important notes:
* Please refer to the following guide for instructions on how to connect to Guillimin and submit jobs: [using_the_guillimin_hpc.md](using_the_guillimin_hpc.md)
* The instructions in this tutorial will suppose you are in a Linux/Max environment. The equivalent tools in Windows are provided in the [Guillimin documentation](using_the_guillimin_hpc.md).
* The user **class99** is provided here as an example. You should replace it by the username that was assigned to you at the beginning of the workshop.


## Introduction

### Description of the lab
In this laboratory pratical you will learn how to use the command line to access the files on the server, run FASTQC on selected fastq files and copy the resulting output to your laptop for review. 

### Local software that we will use
* ssh
* Web browser to visualize FastQC output


## Tutorial

### Getting started
* Connect to the Guillimin HPC
```
ssh class99@guillimin.clumeq.ca
```

You will be in your home folder. At this step, before continuing, please make sure that you followed the instructions in the section **"The first time you log in"** of the [Guillimin guide](using_the_guillimin_hpc.md). If you don't, compute jobs will not execute normally.

### Assessing FASTQ file quality with FastQC
* Copy locally the FASTQ file that we will need for our FastQC analysis
```
cp /gs/project/mugqic/bioinformatics.ca/epigenomics/chip-seq/H1/data/H3K27ac/H3K27ac.H1.fastq.gz .
```

* Run the FastQC command on the scheduler
```
echo 'module load mugqic/fastqc/0.11.2 ; fastqc H3K27ac.H1.fastq' | qsub -l nodes=1:ppn=1 -d .
```

* Download the results to your local computer
```
scp class99@guillimin.clumeq.ca:/home/class99/H3K27ac.H1_fastqc.html .
```

* Open the downloaded file in a web browser, either by double-clicking the file, or from the command line using a command such as
```
firefox H3K27ac.H1_fastqc.html
```
