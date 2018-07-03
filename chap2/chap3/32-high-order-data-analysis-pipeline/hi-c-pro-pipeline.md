# Hi-C pro pipeline
1. [Comparison with other tools](#1)<br>
2. [Overview of the workflow](#2)<br>
3. [Step by Step](#3)<br>
4. [RUN HIC-PRO IN SEQUENTIAL MODE](#4)<br>
5. [ALLELE SPECIFIC ANALYSIS](#5)<br>
6. [COMPATIBILITY WITH OTHER SOFTWARE](#6)<br>



Thorough documentation can be found [here](https://nservant.github.io/HiC-Pro/).
> HiC-Pro was designed to process Hi-C data, from raw fastq files (paired-end Illumina data) to the normalized contact maps. It supports the main Hi-C protocols, including digestion protocols as well as protocols that do not require restriction enzyme such as DNase Hi-C. In practice, HiC-Pro can be used to process dilution Hi-C, in situ Hi-C, DNase Hi-C, Micro-C, capture-C, capture Hi-C or HiChip data. Each step of the workflow can be run independantly. HiC-Pro includes a fast implementatation of the iterative correction method (see the iced python library for more information). In addition, HiC-Pro can use phasing data to build [allele specific contact maps](https://nservant.github.io/HiC-Pro/AS.html#as).

## Comparison with other tools<a name="1"></a>
![](/assets/hicpcompars.jpg)
Table1: X stands for **has this feature**, $$X^a$$ indicates HiC-inpector, HiCdat and HiC-Box do not allow chimeric reads to be rescued during the mapping.

## Overview of the workflow<a name="2"></a>



![](/assets/hipro.png)
Fig. HiC-Pro workflow (http://nservant.github.io/HiC-Pro/MANUAL.html#how-does-hic-pro-work)
## Step by Step<a name="3"></a>




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
![](/assets/hicpro1.jpg)
### 3) Fragment assignment and filtering
Each aligned reads can be assigned to one restriction fragment according to the reference genome and the restriction enzyme.

![](/assets/hicpro2.jpg)

The next step is to separate the invalid ligation products from the valid pairs. Dangling end and self circles pairs are therefore excluded. See previous chapter **Read mapping considerations**.

In case of Hi-C protocols that do not require a restriction enzyme such as DNase Hi-C or micro Hi-C, the assignment to a restriction is not possible. If no GENOME_FRAGMENT file are specified, this step is ignored. Short range interactions can however still be discarded using the MIN_CIS_DIST parameter.

### 4) Quality Controls
There are multiple qualitity controls for each step.
**Mapping**: 
- Aligned reads in the first (end-to-end) step
- Alignment after trimming (in pratice, we ususally observed around 10-20% of trimmed reads. An abnormal level of trimmed reads can reflect a ligation issue). 
- The fraction of valid pairs for each type of ligation products.
- Invalid pairs: dangling and or self-circle, singleton, multiple hits or duplicates.
- Calculate distribution of fragment size.
- Fraction about intra/inter- chromosomal contacts. 
- Fraction about short range (<20kb)/long range (>20kb) contacts.

![](/assets/hicpro3.jpg)

### 5) Map builder
Intra et inter-chromosomal contact maps are build for all specified resolutions. The genome is splitted into bins of equal size. Each valid interaction is associated with the genomic bins to generate the raw maps.
![](/assets/hicpro4.jpg)

### 6) ICE normalization
Hi-C data can contain several sources of biases which has to be corrected. HiC-Pro proposes a fast implementation of the original ICE normalization algorithm [Imakaev et al. 2012](https://www.ncbi.nlm.nih.gov/pubmed/22941365), making the assumption of equal visibility of each fragment. The ICE normalization can be used as a standalone python package through the [iced python package](https://github.com/hiclib/).

![](/assets/hicpro6.jpg)

## RUN HIC-PRO IN SEQUENTIAL MODE<a name="4"></a>



HiC-Pro can be run in a step-by-step mode, users just have to set the <code>-s</code> parameter to specify one step. If you want to only want to only align the sequencing reads and run a quality control, use :
```
MY_INSTALL_PATH/bin/HiC-Pro -i FULL_PATH_TO_RAW_DATA -o FULL_PATH_TO_OUTPUTS -c MY_LOCAL_CONFIG_FILE -s mapping -s quality_checks
```
HiC-Pro --help

```
HiC-Pro --help
usage : HiC-Pro -i INPUT -o OUTPUT -c CONFIG [-s ANALYSIS_STEP] [-p] [-h] [-v]
Use option -h|--help for more information

HiC-Pro 2.7.0
---------------
OPTIONS

 -i|--input INPUT : input data folder; Must contains a folder per sample with input files
 -o|--output OUTPUT : output folder
 -c|--conf CONFIG : configuration file for Hi-C processing
 [-p|--parallel] : if specified run HiC-Pro on a cluster
 [-s|--step ANALYSIS_STEP] : run only a subset of the HiC-Pro workflow; if not specified the complete workflow is run
    mapping: perform reads alignment
    proc_hic: perform Hi-C filtering
    quality_checks: run Hi-C quality control plots
    build_contact_maps: build raw inter/intrachromosomal contact maps
    ice_norm: run ICE normalization on contact maps
 [-h|--help]: help
 [-v|--version]: version

  ```


## ALLELE SPECIFIC ANALYSIS <a name="5"></a>



From the discussion in Chap1.2 we know that there are differences in paternal and maternal X chromosome organization, with the presence of mega-domains on the inactive X chromosome, which are not seen in the active X chromosome. Like as we expected, the inactive X chromosome map is partitioned into two mega-domains. The boundary between the two mega-domains lies near the DXZ4 micro-satellite.

HiC-Pro is able to incorporate phased haplotype information in the Hi-C data processing in order to generate [allele-specific contact maps](http://nservant.github.io/HiC-Pro/AS.html).  
- First: HiC-Pro will mask the reference genome by replacing the SNP position by an ‘N’ using the BEDTools utilities.
- Then: Once aligned, HiC-Pro browses all reads spanning a polymorphic site, locates the nucleotide at the appropriate position, and assigns the read to either the maternal or paternal allele. 
- Next: classify as allele-specific all pairs for which both reads are assigned to the same parental allele or for which one read is assigned to one parental allele and the other is unassigned.
- Finally: These allele-specific read pairs are then used to generate a genome-wide contact map for each parental genome and two allele-specific genome-wide contact maps are independently normalized using the iterative correction algorithm. 

## COMPATIBILITY WITH OTHER SOFTWARE <a name="6"></a>

Reference [here](http://nservant.github.io/HiC-Pro/COMPATIBILITY.html#tads-calling-directionality-index).
- Visualization: JuiceBox and HiCPlotter.
- TADcalling: use **DIRECTIONALITY INDEX** first proposed by Dixon et al, or FIT-HI-C.
- R environment.


