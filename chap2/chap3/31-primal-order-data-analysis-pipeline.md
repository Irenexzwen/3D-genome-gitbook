# 3.1 Assessment of Primary-order Chromatin
Genomic regions with dense nucleo- somes are more tightly packed (i.e., “closed”), whereas nucleosome- depleted regions are more accessible (i.e., “open”) for interactions with regulators and are therefore regarded as the primary locations ofregulatory elements. 

## 3.2.1 Features of data
![](/assets/prios.jpg)
**Figure1.Fragmentation methods and read out features comparison between four methods.**MNase is specially sensitive to open chromotin areas and it is exonucleas which maps regions that are protected by nucleosomes (large open regions are digested). DNase-seq and ATAC-seq are used to sequence and map exposed regions of DNA. 
## 3.2.2 Analytical pipeline:
### step1 Raw reads 
- Quality control
 - Composite plots to check experiment sucess: eg, TSSs shown t be open.----**ArchTEX[108], CEAS[110]**
 - ATAC-seq can be further: estimating the percentage of sequence reads that map to the mitochondrial genome(lower is better).
 - use genome browser to see raw tag density ---- **UCSC[121],IGV[122],GIVE**
 
### step2 Pre-processing & Alignment 
### step3 Peak calling 
 - For MNase-seq
 - For DNase-seq and FAIRE-seq
 - For ATAC-seq
- Chromatin Accessibility Analysis
 - Algorithms
- Analysis and Interpretation


## 3.2.3 Analytical Tools:
- Brief view of different tools 
- Give suggestions on how to choose proper tools 

**Referrence **
https://doi.org/10.1016/j.csbj.2018.02.003 *



