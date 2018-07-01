# TAD calling algorithms
In the 2014 distinguished paper ***A 3D Map of the Human Genome at Kilobase Resolution Reveals Principles of Chromatin Looping***, the author has explained why finding TAD segmentation from the contact map is a tricky work:

> This is due to experimental factors:such as noise and inadequate coverage. It is also because of the intrinsic difficulty of the problem: **the decline in contact frequency at domain edges can be subtle**, and the **very rapid decline** in contact probability observed as one **moves away from the diagonal** of a contact map is a major confound for most approaches. 

In this chapter, we'll especially focus on the domain and boundary calling methods described in previous work.

![](/assets/tadcalling.jpg)
[Figure1](http://dx.doi.org/10.1038/nmeth.4325).  Heat map of the contact matrix of Rao et al.9 GM12878 replicate H (chr1:153,000,000–155,500,000) at 40-kb resolution. Identified TADs are framed in different colors for the various methods. Obs, observed counts.
## TADbit:
https://github.com/3DGenomes/TADbit
http://3dgenomes.github.io/TADbit/
https://github.com/3DGenomes/TADbit/blob/master/_pytadbit/tadbit.py
http://3dgenomes.github.io/TADbit/reference/reference_tadbit.html
http://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005665

TADbit analyzes the contact distribution along the genome and subsequently segments
it into its constitutive TADs, with each TAD border corresponding to a vertical slice of the
Hi-C interaction matrix. TADbit employs a breakpoint detection algorithm that returns the
optimal segmentation of the chromosome under BIC-penalized likelihood. Briefly, The
number of interactions between loci i and j separated by D nucleotides is assumed to
have a Poisson distribution with parameter wij exp(a + b D), where a and b are TADdependent
constants and wij is the normalization factor for the cell at coordinates (i,j) of
the Hi-C contact matrix. Breakpoint detection methods were developed to segment time
series in uniform blocks. In the case of Hi-C data, the correspondence with times series
is not straightforward because the measured signal is two-dimensional. This issue is
resolved by considering that a single observation is the vector of interactions of a locus
with all other loci, in other words, an observation is a column of the Hi-C matrix. In this
view, a TAD defines a vertical slice of the Hi-C matrix. Each cell of this slice belongs to
one of three categories: the contacts between the TAD and all upstream loci, the intraTAD
contacts, and the contacts between the TAD and all downstream loci. From there,
the algorithm proceeds in two phases. In the first, the log-likelihood of every slice (defined
by a start and end position) is computed. If the slice does not cover exactly one TAD, at
least one of the three categories described above will be composite, which will cause a
misfit. As a result, the total log-likelihood of this slice will be low. If the slice covers exactly
one TAD, all three categories will be uniform and the log-likelihood of the slice will be
high. The search for the optimal decomposition of the Hi-C matrix is carried out by a
dynamic programming algorithm based on the following property: if Lk(s,e) denotes the
log-likelihood of the optimal segmentation of the slice (s,e) into k sub-slices, then
�"(1, �) = min (�"-. 1, ℎ + �. ℎ + 1, �
where the minimum is taken over all the values of h. This formula allows computing the
optimal segmentation recursively.
To assign a border score or strength value, the likelihood of each TAD border in the
optimal segmentation is penalized by a value equal to the expected gain in log-likelihood
for adding a TAD border after the optimum is reached, and the dynamic programming
segmentation is restarted. The whole process is carried out 10 times, and each time a
border is on the optimal segmentation, it is penalized by this constant. The strength of a 
TAD border is the number of times it was included in the optimal segmentation, and it
thus ranges from 1 to 10. TAD borders with a score greater than 5 will be considered
“robust”, meaning that they are reproducible among different runs; conversely, TAD
borders with a score lower than 5 will be considered “weak”, and are likely to be
undetectable in replicates or at other resolutions.