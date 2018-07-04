# 3.2 Computational Approaches for Assessing Higher-order Chromatin
1. [Analytical pipeline](#1)<br>
    1.1. [Alignment](#11)<br>
    1.2. [Binning and Generating Contact Matrices](#12)<br>
    1.3. [Normalization (Balancing)](#13)<br>
    1.4. [Identification of interactions](#14)<br>
    1.5. [Visualization](#15)<br>
2. [Analytical tools](#2)<br>
3. [TAD calling tools and algorithms](#3)<br>


## 3.2.1 Analytical pipeline:<a name="1"></a>

- Raw reads 
- Pre-processing 
- Alignment (Full read or chimeric alignment)
- Binning & contact matrixing
- Normalization
- Detection (Intra/Inter-chr interactions)
- Visualization
- Analysis and Interpretation

### 3.2.1.1 Alignment<a name="11"></a>

Hi-C data produced by deep sequencing is no different than other genome-wide deep sequencing datasets. The data starts out as genomic reads in the traditional FASTQ file format.<br> 
Reads are filtered to remove duplicates, PCR artifact. Sequencing adaptors can also be removed prior to alignment.<br>
The goal is to simply find a unique alignment for each read. The insert size of the Hi-C ligation product can vary between 1bp to hundreds of megabases (in terms of linear genome distance), it is difficult to use most paired-end alignment modes as is. One straightforward solution is to map each side of the paired end read separately/independently using a standard alignment procedure.
- Full-read alignment first ---- Bowtie2, BWA
- Unmapped reads: chimeric alignment ---- read splitting [[1]](https://doi.org/10.1101/gr.161620.113), iterative mapping [[2]](https://doi.org/10.1038/nmeth.2148)
- Average sufficient reads depth, sufficient mappable reads:4C (1– 2 million), 5C (25 million) and Hi-C (8.4 to 100 million) [[3]](https://doi.org/10.1038/nrg3642)

A detailed description of mapping analysis is covered in **Read mapping consideration** chapter.


### 3.2.1.2 Binning and Generating Contact Matrices<a name="12"></a>

#### what is bin?
A bin is a ﬁxed, non-overlapping geno-mic span into which reads are grouped to increase the signal of the interaction frequency. The interactions between bins are simply summed up to aggre-gate the signals.

#### why we use bin?
- Using a 6-bp cutting restriction enzyme, there are almost $$10^6$$ restriction fragments, leading to an interaction space on the order of $$10^{12}$$ possible pairwise interactions. Thus, achieving sufficient coverage to support maximal resolution is a significant challenge. **It's critical to set goals (what resolution you desire) to choose the proper bin size**.
- To overcome the limitations that the signal-to-noise ratio decreases with increased distance between two target loci.

#### when we use bin?
If the goal is to measure large scale structures, such as genomic compartments, then a lower resolution will often suffice (1MB-10MB), then we'll choose a proper bin size. However if the goal is to measure specific interactions of a small region, e.g. promoter-enhancer looping, then one should choose to use a restriction enzyme that cuts more frequently (e.g. 4bp) and a method that does not measure the entire genome, but instead focuses on exploring only a subset of the genome (i.e. 3C/4C/5C).

#### how to choose bin size 
Smaller bins usually are used for more frequentintra-chromosomal interactions, and larger bins are for less frequentinter-chromosomal interactions. selected binsize should be inversely proportional to the expected number of interac-tions in a region. 

#### what decide the Hi-C resolution
- Sequencing coverage, more reads will cover more of the interaction space and thus imporve the resolution.
- Library complexity -- the total number of unique chimeric molecules that exist in a Hi-C library, a librarywith a low complexity level will saturate quickly with increasing sequencing depth

#### bin-level filtering
Prior to matrix balancing, it is advised to remove any bins (rows/columns) from the dataset that have either very noisy or too low of a signal. These bins are normally found in genomic regions with low mappability or high repeat content, such as around telomeres and centromeres.

### 3.2.1.3 Normalization (Balancing)<a name="13"></a>

The goal of normalization is to reduce biases during the experiment as well as a better comparison between different experiment results (reduce batch effect).

#### Two types of normalization 

- Explicit normalization: 
 - known bias factors [[4]](https://www.ncbi.nlm.nih.gov/pubmed/22001755)
   - Distance between restriction enzyme cut sites (eg, for hi-c)
   - GC content of trimmed ligation junction
   - uniqueness ofsequence reads
  - correction: intergrate prior problistic model. <br>

- Implicit normalization:
 - Iterative correction [[5]](https://doi.org/10.1038/nmeth.2148) based on the assumption that all loci should have equal visibility since we are detecting the entire genome in an unbiased manner (By equalizing the sum of every row/column in the matrix). Faster and preferred. 
 
### 3.2.1.4 Identification of interactions<a name="14"></a>


- TAD calling (Details see 3.2.3)
 - Tools for calling TADs 
 - algorithms and principle 
 - GPU accelerating 
- Separating active/repressive compartments A/B 
- Identifying chromatin loops
 
### 3.2.1.5 Visualization<a name="15"></a>

- See Chapter4 



## 3.2.2 Analytical tools:<a name="2"></a>


<table>
 <tr><th>Techniques</th><th>Tools</th><th>Description</th></tr>
 <tbody>
  <tr><th>4C</th><td><a href="http://refhub.elsevier.com/S2001-0370(17)30093-4/rf9035">FourCSeq </a></td><td>Uses R to detect speciﬁc interactions between DNA elements and identify differential</td></tr>
 <tr><th>5C</th><td><a href="https://genomebiology.biomedcentral.com/articles/10.1186/s13059-015-0806-y">HiFive</a> </td><td>Python package for normalization and analysis of chromatin structural data produced using either</td></tr>
 <tr>
  <th>Hi-C</th>
  <td><a href="https://genome.cshlp.org/content/24/6/999">Fit-Hi-C</a></td>
  <td>Assigns statistical confidence to mid-range cis-chromosomal contacts</td>
  </tr>
 <tr>
  <th></th>
  <td><a href="http://homer.ucsd.edu/homer/">HOMER</a></td>
  <td>Designed for high-resolution Hi-C data</td>
 </tr>
 <tr>
  <th></th>
  <td><a href="https://www.nature.com/articles/ng.947">HIPPIE</a></td>
  <td>Identiﬁes chromatin interactions in a genome</td>
  </tr>
  <tr>
   <th></th>
   <td><a href="https://www.sciencedirect.com/science/article/pii/S0092867414014974?via%3Dihub">HiCCUPS</a></td>
   <td>Detect sub-TAD chromatin interactions (cis)</td>
   </tr>
  <tr>
   <th></th>
   <td><a href="https://www.sciencedirect.com/science/article/pii/S2405471216302198?via%3Dihub">Juicer</a></td>
   <td>Aligns, ﬁlters and normalizes, identiﬁes and compares TADs, loops and compartments and display using Juicebox</td>
   </tr>
   <tr>
    <th></th>
    <td><a href="https://www.sciencedirect.com/science/article/pii/S2405471216302198?via%3Dihub">HiC-Pro</a></td>
    <td>Aligns, quality control, inter-intra contact maps, fast iterative correction, allele specific contact maps</td>
    </tr>
</table>
Comprehensive tools list for hi-c data analysis can be found [here](https://omictools.com/3c-4c-5c-hi-c-chia-pet-category). Next we'll use Hi-C pro as a showcase to see hi-c data analysis workflow (See **Hi-C Pro Pipeline** chapter).



## 3.2.3 TAD calling tools and algorithms <a name="3"></a>

Brief view of different tools.
<table>
 <tr><th>Tools</th><th>Description</th><th>Language</th></tr>
 <tbody>
  <tr><th><a href="http://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005665">TADbit</a></th><td>TADbit includes quality control module, and aligns reads to the reference</td><td>Python</td></tr>
 <tr><th><a href="compbio.cs.brown.edu/projects/tadtree/">TADtree</a></th><td>Identifies hierarchical topological domains</td><td>Python</td></tr>
 <tr>
  <th><a href="https://github.com/kingsfordgroup/armatus">Armatus</th>
  <td>Uses dynamic programming to call TADs in different resolutions</a></td>
  <td>C++</td>
  </tr>
  <tr>
   <th><a href="https://github.com/theaidenlab/juicer/wiki/Arrowhead">Arrowhead</th>
   <td>Arrowhead is an algorithm for finding contact domains</a></td>
   <td>Java</td>
   </tr>
</table>

Performances comparison for different tools are surveyed [here](http://dx.doi.org/10.1038/nmeth.4325).

<br><br>
#Referrence 
[1] V.C. Seitan, A.J. Faure, Y. Zhan, R.P. McCord, B.R. Lajoie, E. Ing-Simmons, et al.
Cohesin-based chromatin interactions enable regulated gene expression within preexisting architectural compartments Genome Res, 23 (12) (2013), pp. 2066-2077.<br>
[2] M. Imakaev, G. Fudenberg, R.P. McCord, N. Naumova, A. Goloborodko, B.R. Lajoie, et al.Iterative correction of Hi-C data reveals hallmarks of chromosome organization Nat Methods, 9 (10) (2012), pp. 999-1003<br>
[3] D. Sims, I. Sudbery, N.E. Ilott, A. Heger, C.P. Ponting Sequencing depth and coverage: key considerations in genomic analyses Nat Rev Genet, 15 (2) (2014), pp. 121-132.<br>
[4] E. Yaffe, A. Tanay Probabilistic modeling of Hi-C contact maps eliminates systematic biases to characterize global chromosomal architecture Nat Genet, 43 (11) (2011), pp. 1059-1065<br>
[5] M. Imakaev, G. Fudenberg, R.P. McCord, N. Naumova, A. Goloborodko, B.R. Lajoie, et al. Iterative correction of Hi-C data reveals hallmarks of chromosome organization
Nat Methods, 9 (10) (2012), pp. 999-1003<br>

## Primary referrence of this part:
[6] Computational Methods for Assessing Chromatin Hierarchy<br>
[7] The Hitchhiker's Guide to Hi-C Analysis: Practical guidelines<br>
[8] Comparison of computational methods for Hi-C data analysis<br>















