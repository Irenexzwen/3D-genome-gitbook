# TAD calling algorithms
In the 2014 distinguished paper ***A 3D Map of the Human Genome at Kilobase Resolution Reveals Principles of Chromatin Looping***, the author has explained why finding TAD segmentation from the contact map is a tricky work:

> This is due to experimental factors:such as noise and inadequate coverage. It is also because of the intrinsic difficulty of the problem: **the decline in contact frequency at domain edges can be subtle**, and the **very rapid decline** in contact probability observed as one **moves away from the diagonal** of a contact map is a major confound for most approaches. 

In this chapter, we'll especially focus on the domain and boundary calling methods described in previous work.

![](/assets/tadcalling.jpg)
[Figure1](http://dx.doi.org/10.1038/nmeth.4325).  Heat map of the contact matrix of Rao et al.9 GM12878 replicate H (chr1:153,000,000–155,500,000) at 40-kb resolution. Identified TADs are framed in different colors for the various methods. Obs, observed counts.

## Directionality Index [(Dixon et al. (2012))](https://media.nature.com/original/nature-assets/nature/journal/v485/n7398/extref/nature11082-s1.pdf)
### Observation and assumption:
The regions at the periphery of the topological domains are highly biased in their interaction frequencies. In other words, the most upstream portion of a topological domain is highly biased towards interacting downstream, and the downstream portion of a topological domain is highly biased towards interacting upstream. DI measures the tendency of a locus to interact with upstream vs. downstream sites. This is useful for identifying domains because the upstream boundary of a domain should prefer to interact with downstream loci, and vice-versa.

### Directionality Index (DI) 
The directionality index is calculated in equation 1, where A is the number of reads that map from a given 40kb bin to the upstream 2Mb, B is the number of reads that map from the same 40kb bin to the downstream 2Mb **notice that these parameters are choose arbitrarily, lack a principled strategy of choosing algorithmic parameters.**, and E, the expected number of reads under the null hypothesis, is equal to (A + B)/2.
$$
DI=(\frac{B-A}{|B-A|})(\frac{(A-E)^2}{E}+\frac{(B-E)^2}{E})
$$
This is consistent with [Chi-sqaure nul hypothesis](https://en.wikipedia.org/wiki/Chi-squared_test).
### HMM estimate states 
This method considers the directionality index as an observation and believe that the “true”
hidden directionality bias (DB) can be determined using a [hidden Markov model (HMM)](https://en.wikipedia.org/wiki/Hidden_Markov_model). 
![](/assets/HMM.jpg)
[Figure2](https://media.nature.com/original/nature-assets/nature/journal/v485/n7398/extref/nature11082-s1.pdf).  Observations: DI, hidden state: 3 states as **“Upstream Bias”, “Downstream Bias” or “NoBias”**. <br>
The probability of observing DI as **Y’s [Y1,Y2..Yn]**, is conditioned on the hidden **true**
directionality biases as Q’s [Q1,Q2..Qn] and the [**mixtures of gaussians**](https://en.wikipedia.org/wiki/Mixture_model#Gaussian_mixture_model) as M’s [M1,M2..Mn]：
$$
P(Y_t
 = y_t
|Q_t
 = i,M_t
 = m) = N(y_t
;µ_{i,m},Σ_{i,m})\\
P(M_t
 =m|Q_t
 =i) = C(i,m), \text{where C encodes the mixture weights for each state i}. 
 $$
Then [**EM**](https://en.wikipedia.org/wiki/Expectation%E2%80%93maximization_algorithm) algorithms was applied to compute maximum likelihood estimates and the parameter estimates of transition and emission (characterized by mean, covariance and weights). The posterior marginals were then estimated using the Forward-backward algorithm ( for each chr, 1 to 20 mixtures and chose the mixture with
best goodness of fit using the AIC criterion).<br>
Domains and boundaries are then inferred from the results of the **HMM state** calls throughout the genome. A domain is **initiated** at the beginning of a single **downstream** biased state(it do nothave upstream information) and **end** at a **upstream biased** state.<br>
The alg also defined **unorganized chromatin** to be these regions that are > 400kb, and the **topological boundaries** to be less than 400kb.

## Arrowhead [(Rao et al.(‎2014))](https://www.ncbi.nlm.nih.gov/pubmed/25497547)
In order to call sub-TADs from ultra-high resolution Hi-C data sets, arrowhead has been proposed as a heuristic algorithm to detect the corners of the domains to locate the boundaries of TADs. The name was got from the transformed matrix:
![](/assets/arrow.png)
[Figure3](https://www.ncbi.nlm.nih.gov/pubmed/25497547).Transformation replaces domains with an arrowhead-shaped motif pointing toward the domain’s upper-left corner (example in yellow). Arrowheads  are then identified using dynamic programming.

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