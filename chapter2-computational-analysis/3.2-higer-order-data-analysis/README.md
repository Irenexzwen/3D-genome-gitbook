# 3.2 Higer order data analysis

## Computational Approaches for Assessing Higher-order Chromatin

1. Analytical pipeline  


    1.1. Alignment  


    1.2. Binning and Generating Contact Matrices  


    1.3. Normalization \(Balancing\)  


    1.4. Identification of interactions  


    1.5. Visualization  

2. Analytical tools 
3. TAD calling tools and algorithms 

### 3.2.1 Analytical pipeline:

* Raw reads 
* Pre-processing 
* Alignment \(Full read or chimeric alignment\)
* Binning & contact matrixing
* Normalization
* Detection \(Intra/Inter-chr interactions\)
* Visualization
* Analysis and Interpretation

#### 3.2.1.1 Alignment

Hi-C data produced by deep sequencing is no different than other genome-wide deep sequencing datasets. The data starts out as genomic reads in the traditional FASTQ file format.

  
Reads are filtered to remove duplicates, PCR artifact. Sequencing adaptors can also be removed prior to alignment.

  
The goal is to simply find a unique alignment for each read. The insert size of the Hi-C ligation product can vary between 1bp to hundreds of megabases \(in terms of linear genome distance\), it is difficult to use most paired-end alignment modes as is. One straightforward solution is to map each side of the paired end read separately/independently using a standard alignment procedure.

* Full-read alignment first ---- Bowtie2, BWA
* Unmapped reads: chimeric alignment ---- read splitting [\[1\]](https://doi.org/10.1101/gr.161620.113), iterative mapping [\[2\]](https://doi.org/10.1038/nmeth.2148)
* Average sufficient reads depth, sufficient mappable reads:4C \(1– 2 million\), 5C \(25 million\) and Hi-C \(8.4 to 100 million\) [\[3\]](https://doi.org/10.1038/nrg3642)

A detailed description of mapping analysis is covered in **Read mapping consideration** chapter.

#### 3.2.1.2 Binning and Generating Contact Matrices

**what is bin?**

A bin is a ﬁxed, non-overlapping geno-mic span into which reads are grouped to increase the signal of the interaction frequency. The interactions between bins are simply summed up to aggregate the signals.

**why we use bin?**

* Using a 6-bp cutting restriction enzyme, there are almost $$10^6$$ restriction fragments, leading to an interaction space on the order of $$10^{12}$$ possible pairwise interactions. Thus, achieving sufficient coverage to support maximal resolution is a significant challenge. **It's critical to set goals \(what resolution you desire\) to choose the proper bin size**.
* To overcome the limitations that the signal-to-noise ratio decreases with increased distance between two target loci.

**when we use bin?**

If the goal is to measure large scale structures, such as genomic compartments, then a lower resolution will often suffice \(1MB-10MB\), then we'll choose a proper bin size. However if the goal is to measure specific interactions of a small region, e.g. promoter-enhancer looping, then one should choose to use a restriction enzyme that cuts more frequently \(e.g. 4bp\) and a method that does not measure the entire genome, but instead focuses on exploring only a subset of the genome \(i.e. 3C/4C/5C\).

**how to choose bin size**

Smaller bins usually are used for more frequent intra-chromosomal interactions, and larger bins are for less frequent inter-chromosomal interactions. selected bin size should be inversely proportional to the expected number of interactions in a region.

**what decide the Hi-C resolution**

* Sequencing coverage, more reads will cover more of the interaction space and thus improve the resolution.
* Library complexity -- the total number of unique chimeric molecules that exist in a Hi-C library, a library with a low complexity level will saturate quickly with increasing sequencing depth

**bin-level filtering**

Prior to matrix balancing, it is advised to remove any bins \(rows/columns\) from the dataset that have either very noisy or too low of a signal. These bins are normally found in genomic regions with low mappability or high repeat content, such as around telomeres and centromeres.

#### 3.2.1.3 Normalization \(Balancing\)

The goal of normalization is to reduce biases during the experiment as well as a better comparison between different experiment results \(reduce batch effect\).

**Two types of normalization**

* Explicit normalization:
  * known bias factors [\[4\]](https://www.ncbi.nlm.nih.gov/pubmed/22001755)
    * Distance between restriction enzyme cut sites \(eg, for hi-c\)
    * GC content of trimmed ligation junction
    * uniqueness of sequence reads
  * correction: integrate prior probabilistic model.  
* Implicit normalization:
  * Iterative correction [\[5\]](https://doi.org/10.1038/nmeth.2148) based on the assumption that all loci should have equal visibility since we are detecting the entire genome in an unbiased manner \(By equalizing the sum of every row/column in the matrix\). Faster and preferred. 

#### 3.2.1.4 Identification of interactions

* TAD calling \(Details see 3.2.3\)
  * Tools for calling TADs 
  * algorithms and principle 
  * GPU accelerating 
* Separating active/repressive compartments A/B 
* Identifying chromatin loops

#### 3.2.1.5 Visualization

* See Chapter4 

### 3.2.2 Analytical tools:

| Techniques | Tools | Description |
| :--- | :--- | :--- |
| 4C | [FourCSeq](http://refhub.elsevier.com/S2001-0370%2817%2930093-4/rf9035) | Uses R to detect speciﬁc interactions between DNA elements and identify differential |
| 5C | [HiFive](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-015-0806-y) | Python package for normalization and analysis of chromatin structural data produced using either |
| Hi-C | [Fit-Hi-C](https://genome.cshlp.org/content/24/6/999) | Assigns statistical confidence to mid-range cis-chromosomal contacts |
|  | [HOMER](http://homer.ucsd.edu/homer/) | Designed for high-resolution Hi-C data |
|  | [HIPPIE](https://www.nature.com/articles/ng.947) | Identiﬁes chromatin interactions in a genome |
|  | [HiCCUPS](https://www.sciencedirect.com/science/article/pii/S0092867414014974?via%3Dihub) | Detect sub-TAD chromatin interactions \(cis\) |
|  | [Juicer](https://www.sciencedirect.com/science/article/pii/S2405471216302198?via%3Dihub) | Aligns, ﬁlters and normalizes, identiﬁes and compares TADs, loops and compartments and display using Juicebox |
|  | [HiC-Pro](https://www.sciencedirect.com/science/article/pii/S2405471216302198?via%3Dihub) | Aligns, quality control, inter-intra contact maps, fast iterative correction, allele specific contact maps |

 Comprehensive tools list for hi-c data analysis can be found [here](https://omictools.com/3c-4c-5c-hi-c-chia-pet-category). Next we'll use Hi-C pro as a showcase to see hi-c data analysis workflow \(See **Hi-C Pro Pipeline** chapter\). 

### 3.2.3 TAD calling tools and algorithms Brief view of different tools.

| Tools | Description | Language |
| :--- | :--- | :--- |
| [TADbit](http://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005665) | TADbit includes quality control module, and aligns reads to the reference | Python |
| [TADtree](compbio.cs.brown.edu/projects/tadtree/) | Identifies hierarchical topological domains | Python |
| [Armatus](https://github.com/kingsfordgroup/armatus) | Uses dynamic programming to call TADs in different resolutions | C++ |
| [Arrowhead](https://github.com/theaidenlab/juicer/wiki/Arrowhead) | Arrowhead is an algorithm for finding contact domains | Java |

Performances comparison for different tools are surveyed [here](http://dx.doi.org/10.1038/nmeth.4325).



### Reference:

\[1\] Computational Methods for Assessing Chromatin Hierarchy  
\[2\] The Hitchhiker's Guide to Hi-C Analysis: Practical guidelines  
\[3\] Comparison of computational methods for Hi-C data analysis  


