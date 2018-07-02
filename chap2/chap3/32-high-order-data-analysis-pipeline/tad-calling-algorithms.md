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
The algorithms also defined **unorganized chromatin** to be these regions that are > 400kb, and the **topological boundaries** to be less than 400kb.

## Arrowhead [(Rao et al.(‎2014))](https://www.ncbi.nlm.nih.gov/pubmed/25497547)
In order to call sub-TADs from ultra-high resolution Hi-C data sets, arrowhead has been proposed as a heuristic algorithm to detect the corners of the domains to locate the boundaries of TADs. The name was got from the transformed matrix:
![](/assets/arrow.png)
[Figure3](https://www.ncbi.nlm.nih.gov/pubmed/25497547).Transformation replaces domains with an arrowhead-shaped motif pointing toward the domain’s upper-left corner (example in yellow). Arrowheads  are then identified using dynamic programming.

The matrix transformation is defined as:
$$
 A_{i,i+d} = (M^*_{i,i-d} – M^*_{i,i+d})/(M^*_{i,i-d} + M^*_{i,i+d})
$$
where M* is the normalized contact matrix, A is arrowhead matrix.
## TADbit:
https://github.com/3DGenomes/TADbit
http://3dgenomes.github.io/TADbit/
https://github.com/3DGenomes/TADbit/blob/master/_pytadbit/tadbit.py
http://3dgenomes.github.io/TADbit/reference/reference_tadbit.html
http://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005665


## TADtree [(Weinreb et. al (2016))](https://www.ncbi.nlm.nih.gov/pubmed/26315910)
TADtree is the first published method that can detect TADs and sub-TADs simultaneously (subTADs have been thought to vary between cell types and change the gene regulation). TADtree can detect nested hierarchies of TADs based on the empirical observation that within TADs, the enrichment of contacts over background grows linearly with the distance between bins, but at a rate that depends on the TAD length. 

TADtree algorithm finding the *TAD forest* using a dynamic programming algorithm to maximize an objective function. Before we go through the framework and some details, few features of this method should be notice:
- The number of trees **N** in a forest is defined by users.
- The time complexity of this alg is $$O(S^5)$$ where $$S$$ is the maxium TAD size.
- The algorithm will return an approximate optimal fit but not necessarialy the right model.

### Model：
#### a) background contact frequency
Just as other methods, first we usually have a way to measure the background contact strength. Here the **background function** giving the mean contact frequency for bins at each distance **d**:
$$
B(d)=\frac{1}{J-d}\sum_{i=1}^{J-d}A_{i,i+d}
$$

#### b) modeling TADs and sub-TADs
Modeling TADs and subTADs, this model would be the core of this method which defines the features and criteria to distinguish TADs and it's hierarchical structure. For each TAD ***D***, it can be described with four parameters: $$D = (L_D,R_D,\delta_D, \beta_D)$$. Specifying an TAD in interval $$[L_D; R_D]$$. The expected contact frequency is:

$$\hat{A}_D(l,k)=((k-l)\delta_D+\beta_D)B(k-l),\quad for\quad L_D \le l \le k \le R_D$$.

This is a linear function about the variable $$(k-l)$$ with slope $$\delta_D$$ and intercept $$\beta_D$$.

The most distinguished feature that the paper found is that subTADs usually have a higher \delta. \delta is positive indicates the contact enrichment increases with increasing distance between bins, hence the subTADs is has a higher rate of increase in contact frequency with distance.

#### c) boundary index (BI)
Previous studies have illustrate that the boundaries mark a shift in interaction preference. 1D Test statistic called the BI that measures local shifts in interaction preference.
$$
B_{p,q}(i)= \sum_{l=i-q}^{i+q} |\sum_{k=1}^p A_{l,i+k}-A_{l,i-k}|.
$$
The BI measures the shift in contacts around an interval *i*. Moreover, this normalized BI is Z-score and a TAD forest has its own $$\hat{BI}$$, details can be refered in the original paper. Based on BI, TADtree defined what is **valid boundaries**.

### Obejections:
To generate an optimal result, the algorithm is trying to maximize the following objection function:
$$ 
\mathcal{O}_{\gamma}(F)=\gamma\overline{\mathcal{B}}_{p,q}(F)-\varepsilon(F) 
$$
such that $$|F|=N$$(TAD forest has N TADs), and each $$D\in F$$ is locally fitted and has **valid boundaries**.
