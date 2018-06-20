##2.3 C-Techs (chromosome conformation capture)-coupled 
1. [Introduction](#introduction)
2. [Overivew of 3C methods](#231)<br>
    2.1. [Specificity](#2311)<br>
    2.2. [Through-put and resolution](#2312)
3. [Hi-C](#233)

### 2.3.1 Introduction<a name="introduction"></a>

The foundamental object of 3C(Chromosome Conformation Capture) techniques and 3C-derived methods is to understand the physical wiring diagram of the genome by identifying the physical interaction between chromosomes. 

To capture the interaction (crosslink between strings), there are few steps in general:
- Take a snapshot of the flowing cells - **Crosslink** with fixative agent (formaldehyde)
- Zoom in on crosslinked part and exclude untangled parts - **Digested** with a restriction enzyme
- Analyze the components come from the same chromatin - **Reverse crosslink** and **sequence**
- Finish the jigsaw puzzle and get the results - **Align** the reads and **summarize** the contacts

> Based on these general ideas, then we'll dive deeper by walking through two of the most popular  techniques and then briefly introduce some other methods. 

### 2.3.2 Overivew of 3C methods<a name="231"></a>

![](/assets/3creview.png)
*Figure I. Schematic Representation of Chromosome Conformation Capture (3C) and 3C-Derived Methods. These methods help to elucidate nuclear organization by detecting physical interactions between genetic elements located throughout the genome. Abbreviations: IP, immunoprecipitation; RE, restriction enzyme.*

To better understand the difference between these methods, I'd like to distingush them between the following couple of aspects:

#### 1) Specificity - What does _one, all, many_ mean<a name="2311"></a>
‘1’, ‘Many’ and ‘All’ indicate how many loci are interrogated in a given experiment. For example, ‘1 versus All’ indicates that the experiment probes the interaction profile between 1 locus and all other potential loci in the genome. ‘All versus All’ means that one can detect the interaction profiles of all loci, genome-wide, and their interactions with all other genomic loci [1].

These kind of specificity is determined by the primer when people use **specific primers** before PCR. 

#### 2) Through-put and resolution<a name="2312"></a>
Hi-C techniques has the highest through-put (billion reads per sample) but suffering of a relative low resolution of 0.1-1Mb. However, the other methods usually have a higher resolution  around 1kb. For more details one can refer to table2 in [2].

### 2.3.3 Hi-C<a name="233"></a>
Hi-C is the highest through-put version of 3C-derived technologies. Due to the decreasing cost of 2nd generation sequencing, hi-c is widely used.

The principle of Hi-C can be illustrated as:
![](/assets/hic.gif)






### 2.2.1 One-to-one:
- 3C

### 2.2.2 One-to-all:
- Multiplexed 3C-seq
- Open-ended 3C
- 3C-DSL
- 4C
- 4C-seq
- TLA
- e4C
- ACT

### 2.2.3 Many-to-many:
- 5C
- ChIA-PET 

### 2.2.4 Many-to-all
- Capture-3C
- Capture-HiC
- PLAC-seq/HiChIP

### 2.2.5 All to all 
- GCC
- Hi-C
- ELP
- TCC

### Hi-C enrichment
- Single-cell
- In situ/DNase/Micro-HiC

## Another methods for classification:
### Locus-landmark: 
Measure interactions of genomic loci with relatively fixed nuclear ‘landmarks’
- Techniques: ChIP, DamID, TSA-seq

### Locus-locus: 
Measure interactions between genomic loci
- Techniques: 3C, Hi-C, ChIA-PET etc.



#Referrence
[1] Schmitt, Anthony D., Ming Hu, and Bing Ren. "Genome-wide mapping and analysis of chromosome architecture." Nature reviews Molecular cell biology 17.12 (2016): 743.
[2] Risca, Viviana I., and William J. Greenleaf. "Unraveling the 3D genome: genomics tools for multiscale exploration." Trends in Genetics 31.7 (2015): 357-372.

https://doi.org/10.1016/j.csbj.2018.02.003<br>
https://github.com/hms-dbmi/hic-data-analysis-bootcamp/blob/master/HiC-Protocol.pptx 


