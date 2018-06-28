# Hi-C pro pipeline
Thorough documentation can be found [here](https://nservant.github.io/HiC-Pro/).
> HiC-Pro was designed to process Hi-C data, from raw fastq files (paired-end Illumina data) to the normalized contact maps. It supports the main Hi-C protocols, including digestion protocols as well as protocols that do not require restriction enzyme such as DNase Hi-C. In practice, HiC-Pro can be used to process dilution Hi-C, in situ Hi-C, DNase Hi-C, Micro-C, capture-C, capture Hi-C or HiChip data. Each step of the workflow can be run independantly. HiC-Pro includes a fast implementatation of the iterative correction method (see the iced python library for more information). In addition, HiC-Pro can use phasing data to build [allele specific contact maps](https://nservant.github.io/HiC-Pro/AS.html#as).

## Overview of the workflow
![](/assets/hipro.png)

## Step by Step
### 1) Installation
To install this tool you should first check all the dependencies it relies on:
- The bowtie2 mapper
- Python (>2.7) with pysam (>=0.8.3), bx(>=0.5.0), numpy(>=1.8.2), and scipy(>=0.15.1) libraries
- R with the RColorBrewer and ggplot2 packages
- g++ compiler
- Samtools (>0.1.19)
- Unix sort (which support -V option) is required ! For Mac OS user, please install the GNU core utilities 
After set up the system [configuration](http://nservant.github.io/HiC-Pro/QUICKSTART.html#how-to-install-it). 

Install HiC-Pro (>=2.7.8), be sure to have the appropriate rights and run :

```
tar -zxvf HiC-Pro-master.tar.gz
cd HiC-Pro-master
## Edit config-install.txt file if necessary
make configure
make install
```


If you encounter any error you may luckily find some solution [here](http://nservant.github.io/HiC-Pro/FAQ.html) and [here](http://nservant.github.io/HiC-Pro/ERRORS.html).

### 2) Reads mapping
Pair-end sequencing is independantly aligned on the reference genome. The mapping is performed in two steps, more notes [here](http://nservant.github.io/HiC-Pro/MANUAL.html#how-does-hic-pro-work). 
- First, the reads are aligned using an end-to-end aligner. 
- Second, reads spanning the ligation junction are trimmmed from their 3’ end, and aligned back on the genome. 
#### Input file
```
.fastq(.gz) files
```

    #### Output file
```
 .bam files
```

Parameters for specific alignment is the same usage with **bowtie2**, like the min quality, index location, sequencing qualities encoding and so on.
### 3) Fragment assignment and filtering