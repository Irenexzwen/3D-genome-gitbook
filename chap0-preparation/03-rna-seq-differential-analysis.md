---
description: >-
  Assess different expression levels of genes between our samples at different
  timepoints, conditions, etc.
---

# 03 RNA-seq Differential Analysis

## Why?

Let's suppose we have a strain of E. coli that we want to optimize to produce ethanol.But we don't know what genes are involved. What do we do?

We perform differential expression analysis on our RNA-seq data. The expressionlevels have already been calculated using `cufflinks`.



## How? Cuffdiff!

#### Cuffdiff under the hood

A simple methodology for assessing differential expression levels isdifferences in transcript count between sample conditions, but this canbe erroneous due to alternative splicing and biases in sequencing.

A more robust method is to fit a **Poisson Distribution** given theexpectation that the odds of seeing a change in expression level are small.

**But Poisson doesn't account for count uncertainty and count dispersion!**

* **Count Uncertainty:** The fact that reads can be shared across multiple genesbecause of shared genetic data.
* **Count Dispersion:** The fact that the number of reads produced is highlyvariable between replicates.

From the [_Cuffdiff Paper_](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3869392/pdf/nihms439296.pdf):

> Our method addresses both of these issues by modeling how variability in measurements of a transcript's fragment count depends on both its expression and its splicing structure.

The way in which this happens is:

> The algorithm captures uncertainty in a transcript's fragment count as a beta distribution and the overdispersion in this count with a negative binomial, and mixes the distributions together. The resulting mixture is a beta negative binomial distribution that reflects both sources of variability in an isoform's measured expression level.

Summarized in this picture:

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3869392/bin/nihms439296f2.jpg)

**Pretty clever!**

## Using Cuffdiff

Thankfully using `cuffdiff` is super easy.

An example implementation is shown below:

First thing for ease of use is to generate a file called `diff.sh`. Thisis a simple bash file and all of this could be accomplished just usingthe command line but this is a little cleaner and allows foreasier code repeatability.

```text
  $ vi diff.sh
  genes=/home/linux/ieng6/be183f/public/bengTutorial/index_gtf/genes4.gtf
  C1_R1=../alignments/C1_R1/accepted_hits.bam
  C1_R2=../alignments/C1_R2/accepted_hits.bam
  C2_R1=../alignments/C2_R1/accepted_hits.bam
  C2_R2=../alignments/C2_R2/accepted_hits.bam
  ​
  cuffdiff -o diff_out ${genes} ${C1_R1},${C1_R2} ${C2_R2},${C2_R2}
```

Now we simply run: `bash diff.sh`Where the files noted in `C*_R*` are the expression files generated from`cufflinks`.

In bash scripting calling `${*}` denotes a variable defined earlier inthe script.

#### Cuffdiff Output

It will generate a CSV-like file in the `diff_out` directorycalled `gene_exp.diff`. It looks like:

```text
  
  test_id      gene_id gene    locus   sample_1        sample_2        status  value_1 value_2 log2(fold_change)       test_stat       p_value q_value significant
  FBgn0002521  FBgn0002521     pho     4:1193093-1202271       q1      q2      OK      1885.82 1597.12 -0.239721       -1.27565        0.07125 0.389135        no
  FBgn0004607  FBgn0004607     zfh2    4:524476-560418 q1      q2      NOTEST  6.72414 6.02587 -0.158181       0       1       1       no
  FBgn0004624  FBgn0004624     CaMKII  4:1056642-1074329       q1      q2      OK      6854.63 6821.34 -0.00702337     -0.0397619      0.9532  0.97767 no
  FBgn0004859  FBgn0004859     ci      4:68333-77667   q1      q2      NOTEST  33.6854 68.8131 1.03056 0       1       1       no
  FBgn0005558  FBgn0005558     ey      4:718314-741787 q1      q2      OK      339.474 313.086 -0.116739       -0.511244       0.46085 0.925195        no
  FBgn0005561  FBgn0005561     sv      4:1109443-1133943       q1      q2      OK      215.591 182.876 -0.237431       -0.810935       0.2223  0.819162        no
  FBgn0005666  FBgn0005666     bt      4:745029-796707 q1      q2      OK      337.666 352.068 0.0602593       0.312879        0.65755 0.925195        no
  FBgn0010217  FBgn0010217     ATPsyn-beta     4:1052439-1055175       q1      q2      OK      45751.2 45196.6 -0.0175982      -0.10918        0.8776  0.929994        no
  FBgn0011642  FBgn0011642     Zyx102EF        4:1077990-1081542       q1      q2      OK      4612.4  4319.09 -0.0947887      -0.486887       0.48765 0.925195        no
```

#### Accessing the data

Conveniently CSV files can be accessed with `R`, `Python`, or even `Excel`

Here's an example code snippet of accessing only statistically significantrows in `Bash`:

```text
  
  $ grep yes gene_exp.diff
```

Where this only selects rows where the last columns is `yes`. However ifthe substring `yes` is in a `locus`, `gene_id`, or any other field then this willreturn false positives.

By default this threshold is a value of 0.05 for the q-value field.**What is a q-value?**

In `Python`:

```text
  
  import pandas as pd
  # Tab delimited with a header at the zeroth row.
  df = pd.read_csv('gene_exp.diff', delimiter='\t', header=0)
  just_significant = df.loc[df.significant == 'yes']
```

Further analysis would be to get the count of significant differences bygene locus. Continuing:

```text
  
  counts_by_locus = just_significant.groupby(['locus']).count()
```

#### Example Figure

This is an example out put of how you could plot the results. Here the x-axisis the Log&lt;sub&gt;2&lt;/sub&gt;\(fold-change\) and the y-axis is the-log&lt;sub&gt;10&lt;/sub&gt;\(q-value\). Both of these values are accessible from thethe output of `cuffdiff` above.

![](https://media.nature.com/lw926/nature-assets/srep/2016/160915/srep33296/images_hires/srep33296-f3.jpg)

_Global analysis of differential gene expression related to long-term sperm storage in oviduct of Chinese Soft-Shelled Turtle Pelodiscus sinensis_ ****Liu, Tengfei, et al.

## Supplementary

#### What's a q-value?

When doing lots of statistical comparisons, the likelihood of gettinga statistically significant result \(p-value\) increases as more comparisonsare performed. This results in an increased `False Discovery Rate (FDR).`

**Bonferroni Correction**

To combat this issue of an increased FDR from multiple comparisons, we canadjust our threshold for statistical significance with the **Bonferroni Correction**.

Simply, if we have `m` comparisons being performed and some initial p-value, `a`,then our new threshold, `p` is: `p = a / m`

