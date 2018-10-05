---
description: 'GITAR website: https://www.genomegitar.org'
---

# GITAR Pipeline

## Introduction

> GITAR \(Genome Interaction Tools and Resources\), is a software to perform a comprehensive Hi-C data analysis, including data preprocessing, normalization, visualization and topologically associated domains \(TADs\) analysis. GITAR is composed of two main modules: 1\) HiCtool, a Python library to process and visualize Hi-C data, including TADs analysis and 2\) Processed data library, a large collection of human and mouse datasets processed using HiCtool.

## **HiCtool**

HiCtool is like a one-stop analysis tool which integrates all parts of hic analysis. It's aim is to enable users without any programming or bioinformatic expertise to work with Hi-C data and compare different datasets in a consistent way. 

HiCtool is a pipeline divided into three main sections:

* Data preprocessing
* Data analysis and visualization
* Topological domain analysis

![Figure1 HiCtool workflow schema HiCtool figure by Calandrelli R et al ](../../../.gitbook/assets/hictool.jpg)

### Installation

{% hint style="info" %}
HiCtool is in a pipeline format to allow extreme flexibility and easy usage. **You do not need to install anything** besides the following [Python libraries](https://doc.genomegitar.org/overview.html#installation), packages and software. Everything is open source.
{% endhint %}

### Data preprocessing

* **1.** Downloading the source data from GEO.
* **2.** Pre-truncation of the reads that contain potential ligation junctions.
* **3.** Mapping read pairs to the reference genome.
* **4.** Filtering reads and selecting reads that are paired.
* **5.** Creating the fragment-end \(FEND\) bed file.

{% tabs %}
{% tab title="Downloading data from GEO" %}
#### Downloading the source data from GEO

Full list of instructions [here](https://doc.genomegitar.org/preprocessing_data.html), key steps are captured below for your better understanding.

* The source data in sra format are downloaded via GEO accession number using the command **fastq-dump** of [SRA Toolkit](http://www.ncbi.nlm.nih.gov/Traces/sra/sra.cgi?view=toolkit_doc&f=fastq-dump).
* Split paired-reads SRA data into _SRRXXXXXXX\_1.fastq_ and _SRRXXXXXXX\_2.fastq_, and _SRRXXXXXXX.fastq_ \(if present\) contains reads with no mates.
{% endtab %}

{% tab title="Pre-truncation reads" %}
#### Pre-truncation of the reads that contain potential ligation junctions

This step mainly pre-truncating ithe reads that contain potential ligation junctions to keep the longest piece without a junction sequence \([Ay et al., 2015](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-015-0745-7)\). To do so download the code in [`pre_truncation.py`](https://doc.genomegitar.org/_downloads/pre_truncation.py) \(see [API Documentation](https://doc.genomegitar.org/preprocessing_data.html#api-documentation-preprocessing)\) to carry on. 

Full list of instructions [here](https://doc.genomegitar.org/preprocessing_data.html), key steps are captured below for your better understanding.

* pre\_truncate a .fastq file with different restriction enzyme \(**HindIII, MboI, NcoI and DpnII** sites were built in, while you can still add your own restriction sites file look up [here](https://doc.genomegitar.org/preprocessing_data.html). 
* Output with **.trunc.fastq** file as well as a log file contains the truncation information. 
{% endtab %}

{% tab title="Mapping reads" %}
#### Mapping read pairs to the reference genome

Full list of instructions [here](https://doc.genomegitar.org/preprocessing_data.html), key steps are captured below for your better understanding.

* Mapping software:  [Bowtie 2](http://bowtie-bio.sourceforge.net/bowtie2/index.shtml) —— reads are mapped independently. index is built with reference  **hg38.fa.**
* **HiCfile1\_log.txt** and **HiCfile2\_log.txt** are log files containing the statistics of the alignment.
{% endtab %}

{% tab title="Filtering reads" %}
 **Filtering reads and selecting reads that are paired**

Full list of instructions [here](https://doc.genomegitar.org/preprocessing_data.html), key steps are captured below for your better understanding.

* [SAMtools](http://samtools.sourceforge.net/) is used to extract the headers and perform filtering on the mapped reads \(quality\).
* Output paired SAM files \(HiCfile1\_hq.sam and HiCfile2\_hq.sam\) in **BAM format.**
{% endtab %}

{% tab title="Creating FEND file" %}
#### Creating the fragment-end \(FEND\) bed file

The fragment-end \(FEND\) bed file is used to normalize the data and it contains restriction site coordinates and additional information related to fragment properties \(GC content and mappability score\). These properties will later be used in the normalization pipeline to remove biases.

*  GC content of 200 bp upstream and downstream to the restriction site is computed.
* The common RE sites were already precomputed:
  * [HindIII-hg38](http://data.genomegitar.org/HindIII_hg38_gc_map_valid.zip)
  * [MboI-hg38](http://data.genomegitar.org/MboI_hg38_gc_map_valid.zip) 
  * [NcoI-hg38](http://data.genomegitar.org/NcoI_hg38_gc_map_valid.zip)
  * [HindIII-mm10](http://data.genomegitar.org/HindIII_mm10_gc_map_valid.zip)
  * [MboI-mm10](http://data.genomegitar.org/MboI_mm10_gc_map_valid.zip)
{% endtab %}
{% endtabs %}

### Data analysis and visualization

* **1.** Before normalization: HiFIVE:
  * Creating the Fend object.
  * Creating the HiCData object.
  * Creating the HiC project object.
  * Filtering HiC fends.
  * Estimating the HiC distance function.
  * Learning the correction model.
* **2.** Normalizing the data.
* **3.** Visualizing the data.

{% tabs %}
{% tab title="Before normalization" %}
Before we do normalization, there are many unwanted effects people would like to exclude: Such as _PCR duplicates and non-informative reads, produced by the possibility of incomplete restriction enzyme digestion and fragment circularization._ 

Below we have a functional summary for each step,  details should refer to [here](https://doc.genomegitar.org/data_analysis_and_visualization.html). 

| Steps | Functions |
| :--- | :--- |
| 1.Creating the Fend object | Fend object Transform bed file to `FEND object` \(which containing RE information like coordinates, GC content and mappability score\). |
| 2.Creating the HiCData object             | Removing unwanted paired-reads \(like total distance to their respective restriction sites exceeds threshold, PCR duplicates, incomplete restriction enzyme digestion and fragment circularization\) |
| 3.Creating the HiC project object             | The `HiC project object` \(hdf5 format\) links the `HiCData object` with information about which fends to include in the analysis |
| 4.Filtering HiC fends |  Take into account of TSSs and CTCF-bound sites influence |
| 5.Estimating the HiC distance function                                      | Estimation of the **distance-dependence relationship** from the data prior to normalization.  Due to unevenly distributed restriction sites,  fragments surrounded by shorter ones will show higher nearby interactions than those with longer adjacent fragments |
| 6.Learning the correction model | Take into account of fragments length, inter-fragment distance, GC content and mappability score biases information to learn the correction model for Hi-C data. \([Yaffe E. and Tanay A., 2011](http://www.ncbi.nlm.nih.gov/pubmed/22001755)\) |



The script [`HiCtool_hifive.py`](https://doc.genomegitar.org/_downloads/HiCtool_hifive.py) can be used to run all the HiFive steps \(1-6\), whose outputs are **hdf5 files**. For more information about these functions, please see [HiFive’s API documentation](http://bxlab-hifive.readthedocs.org/en/latest/api.html). To run together steps 1-6, open the script [`HiCtool_hifive.py`](https://doc.genomegitar.org/_downloads/HiCtool_hifive.py), **update the parameters on the top and save**. Then just execute the script:
{% endtab %}

{% tab title="Normalization" %}
Biases are to remove at this step,  the observed contact matrix and the fend expected contact matrix are calculated. For each chromosome you can but not restricted to get these 6 files \([docs](https://doc.genomegitar.org/data_analysis_and_visualization.html)\): 

* The **observed data** contain the observed reads count for each bin.
* The **fend expected data** contain the learned correction value to remove biases related to fends for each bin.
* The **enrichment expected data** contain the expected reads count for each bin, considering the linear distance between read pairs and the learned correction parameters.
* The **normalized fend data** contain the corrected reads count for each bin.
* The **normalized enrichment data** \(“observed over expected” matrix\) contain the enrichment value \(O/E\) for each bin.
{% endtab %}

{% tab title="Visualization" %}
 This part is to plot the heatmap and histogram for the **normalized contact data** and **enrichment normalized contact matrix:**

![Normalized contact matrix](../../../.gitbook/assets/hictool-count.jpg)

![enrichment normalized contact matrix](../../../.gitbook/assets/hictool-expected.jpg)
{% endtab %}
{% endtabs %}

### Topological domain analysis

A description can be found [here](https://doc.genomegitar.org/DI_calculation.html#), in this book we will talk about it in 3.2.3 TAD calling algorithms \(Combined DI\).

## Processed Data 

The processed data library is a collection of standardized [processed datasets](http://data.genomegitar.org) using **HiCtool**. There are 19 datasets of human \(hg38\), taken from the library on the [4D Nucleome \(4DN\) Web Portal](https://4dnucleome.org), and 2 datasets of mouse \(mm10\). Specifically, for GITAR we referred only to Hi-C derived datasets.

 **The results stored into zip files include:**

* Intrachromosomal contact matrices \(40 kb\)
* Directionality Index
* HMM states
* Topological domain coordinates
* HDF5 files

The downstream analysis can be carried out directly from these intermediate step like [here](https://www.genomegitar.org/processed-data.html). 

## Reference:

R Calandrelli et, al. [GITAR: An open source tool for analysis and visualization of Hi-C data ](https://www.biorxiv.org/content/early/2018/05/08/259515.)





