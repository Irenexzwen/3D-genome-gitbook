# 3.2 Computational Approaches for Assessing Higher-order Chromatin
## 3.2.1 Analytical pipeline:
- Raw reads 
- Pre-processing 
- Alignment (Full read or chimeric alignment)
- Binning & contact matrixing
- Normalization
- Detection (Intra/Inter-chr interactions)
- Visualization
- Analysis and Interpretation

### 3.2.1.1 Alignment
Reads are filtered to remove duplicates, PCR artifact. Sequencing adaptors can also be removed prior to alignment.
- Full-read alignment first ---- Bowtie2, BWA
- Unmapped reads: chimeric alignment ---- read splitting[[1]](https://doi.org/10.1101/gr.161620.113), iterative mapping[[2]](https://doi.org/10.1038/nmeth.2148)
- Average sufficient reads depth, sufficient mappable reads:4C (1– 2 million), 5C (25 million) and Hi-C (8.4 to 100 million)[[3]](https://doi.org/10.1038/nrg3642)

### 3.2.1.2 Binning and Generating Contact Matrices
- why bin 
- how to choose bin size 

### 3.2.1.3 Normalization
- Where bias comes from
- Explicit normalization
- Implicit normalization

### 3.2.1.4 Detection
- TAD calling
 - callers 
 - algorithms and principle 
 - GPU accelerating 
- Separating active/repressive compartments A/B 
- Identifying chromatin loops
 
### 3.2.1.5 Visualization
- See Chapter4 
- integration analysis 


## 3.2.1 Analytical Tools:
- Brief view of different tools 
- Give suggestions on how to choose proper tools 

<br><br>
**Referrence **
[1] V.C. Seitan, A.J. Faure, Y. Zhan, R.P. McCord, B.R. Lajoie, E. Ing-Simmons, et al.
Cohesin-based chromatin interactions enable regulated gene expression within preexisting architectural compartments Genome Res, 23 (12) (2013), pp. 2066-2077.<br>
[2] M. Imakaev, G. Fudenberg, R.P. McCord, N. Naumova, A. Goloborodko, B.R. Lajoie, et al.Iterative correction of Hi-C data reveals hallmarks of chromosome organization Nat Methods, 9 (10) (2012), pp. 999-1003<br>
[3] D. Sims, I. Sudbery, N.E. Ilott, A. Heger, C.P. Ponting Sequencing depth and coverage: key considerations in genomic analyses Nat Rev Genet, 15 (2) (2014), pp. 121-132.<br>
https://doi.org/10.1016/j.csbj.2018.02.003  \*<br>
https://doi.org/10.1007/s40484-017-0113-6 \*<br>
http://dx.doi.org/10.1038/nrm.2016.104 3.2.1.3 / 3.2.1.4













