#1 General features of 3D genome organization 

## 1.1 2D *cis* elements in the genome 
### Biochemically active regulatory elements (bound by sequence-specific regulatory TFs) :
- **Promoter**: The promoter is a region around the TSS (+1) of a gene, which contains several DNA elements that facilitate the binding of regulatory proteins. It provide a secure initial binding site for RNA polymerase and for proteins called transcription factors that recruit RNA polymerase to make transcription take place [[1]](https://en.wikipedia.org/wiki/Promoter_\(genetics\)).
- **Enhancer**: Enhancers are CRE(cis-regulatory elements which means they are non-coding DNA that does not code for transcription fation). They can be located up to 1 Mbp (1,000,000 bp) away from the gene, upstream or downstream from the start site [[2]](https://en.wikipedia.org/wiki/Enhancer_\(genetics\)).
- **Insulator**: An insulator is a genetic boundary element that blocks the interaction between enhancers and promoters. It has been found to cluster at the boundaries of topological association domains (TADs) and may have a role in partitioning the genome into "chromosome neighborhoods" - genomic regions within which regulation occurs [[3]](https://ipfs.io/ipfs/QmXoypizjW3WknFiJnKLwHCnL72vedxjQkDDP1mXWo6uco/wiki/Insulator_\(genetics\).html).
- **Silencer**: A silencer is a DNA sequence capable of binding transcription regulation factors that block the binding of RNA polymerase to DNA sequence, thus provent genes from being expressed as proteins [[4]](https://en.wikipedia.org/wiki/Silencer_\(genetics\)).

![](/assets/promoter.png)
Figure1. Schematic overview of elements in eukaryotes.

##1.2 Multi-scale folding
The largest chromosomes contain hundreds of millions of base pairs that fold in a limitted space, which leads to multi-scale, hierarchical structures like： nucleosomes, chromatin fibres, chromosome domains, compartments and finally in chromosome territories. 

Information resides at all levels, from the histone–DNA interactions at the sub-nucleosomal scale to the chromosome–chromosome and chromosome–lamina interactions in the nuclear space. This multi-level architecture can be regulated and/or exploited by a variety of com- ponents such as transcription factors, architectural proteins and non-coding RNAs in order to coordinate gene expression and cell fate.

With the help of currently developed chromosome capture technologies, let's how them expanded our knowledge on chromosome structure.

![](/assets/20180629211526biophysics_201504585-1.jpg)
[Figure2](http://www.aimspress.com/article/10.3934/biophy.2015.4.585/figure.html).  Inside the nucleus, euchromatin and heterochromatin give rise to several grades of higher order structures: chromosome loops, Topological Associated Domains (TADs), Lamin Associated Domains (LADs) and chromosomal territories. Also the nucleolus, the “assembly-chain” of ribosomes, associates with specific DNA regions: the Nucleolar Associated Domains (NADs), that surround the highly transcribed region of nucleolus, giving rise to another grade of chromatin organization.


### Chromosome territories
### A/B Compartments 
### TAD(Topologically Associating Domains)
A topologically associating domain (TAD) is a self-interacting genomic region, meaning that DNA sequences within a TAD physically interact with each other more frequently than with sequences outside the TAD. These three-dimensional chromosome structures are present in animals as well as some plants, fungi, and bacteria. TADs can range in size from thousands to millions of DNA bases (hundreds kb usually).[[?]](https://en.wikipedia.org/wiki/Topologically_associating_domain).

TADs typically manifest as contiguous square domains along the **diagonal of Hi-C maps**. The spatial partitioning of the genome into TADs
correlates with many linear genomic features such as his- tone modifications, coordinated gene expression, association with the lamina and DNA replication timing, 
enhancer–promoter interactions. [[?]](http://dx.doi.org/10.1038/nrg.2016.112).

TAD **boundaries are enriched** for[[?]](https://www.nature.com/articles/nature11082)
- insulator proteins: CTCF (detected at ~76% of all boundaries)
- active transcription marks: H3K4me3 and H3K36me3
- nascent transcripts
- housekeeping genes (present in ~34% of TAD boundaries)
- repeat elements

There are also evidence to support that TADs are conserved between different cell types and across species.
- The positioning of TAD is relatively stable across cell types and appears to be independent of tissue-specific gene expression or histone modifications. During ESC differentiation, genome-wide **switching of compartments A and B occurs, whereas TAD positioning remains stable** [[?]](https://www.nature.com/articles/nature14222). 
- TAD positioning is **evolutionarily conserved**: 50–70% of TAD boundaries are shared between human and mouse ESCs [[?]](https://www.nature.com/articles/nature14222). 
- TAD is a stable **unit of replication-time regulation** [[?]](https://www.nature.com/articles/nature13986).

![](/assets/TAD.jpg)
Figure [[3]](https://doi.org/10.1016/j.tibs.2018.03.006). Hi-C-Detected Chromatin Folding Paradigms. TADs (more tightly folded than regions between them) are on-diagonal boxes of contact enrichment. Loops are radially symmetric peaks of contact intensity, often located at the corners of TADs in mammalian cells. Off-diagonal boxes indicate interactions due to compartmentation. Right: TADs and loops may be either mostly transcriptionally active (grey) or inactive (black). Loops may also be more tightly folded, but additionally have an increased likelihood of contact between their boundaries or anchors. Compartmentation is indicated by homotypic (active–active or inactive–inactive) TAD–TAD interactions. The bona fide pattern of chromatin folding is unknown and indicated only schematically.

### Sub TAD and insulation neighborhoods

### Chromatin loops
It has been recognized that, cis-regulatory elements like promoter-enhancer are usually far away along the linear genome in vertebrate creatures. However, in order to elicit the regulatory effect, the genome structure evolved to form a loop that bring together two elemnts to a spatial proximity. This chromotin formation is usually called "chromotin loops". One well known example is the locus control region (LCR) of the β-globin cluster, which inter-acts strongly, via long-range chromatin contacts, with its target genes in erythroid cells (where the β-globin gene is active) but shows little or no interaction in cells from different lineages.[[?]](http://dx.doi.org/10.1038/nrg.2016.112).

### Nucleosome-nucleosome interactions
This is the smallest scale of chromatin organization. For a long time, on the basis of in vitro electron microscopy, nucleosomes were thought to form arrays (often called the 30 nm chromatin fibres) with either solenoid or zig- zag shapes. However, recent studies provide more evidence to stand by a more flexible, heterogeneous groups arranged structure. [[?]](https://www.cell.com/cell/fulltext/S0092-8674\(15\)00132-4).


## 1.3 architectural proteins
- mediator
- cohesin
- CTCF

## 1.4 non-coding RNAs binding





**Referrence **
https://doi:10.1016/j.cell.2013.09.011 and https://www.youtube.com/watch?v=sAkH51R0DNg 1.0 <br>
https://doi.org/10.1016/j.tibs.2018.03.006 1.1<br>
http://dx.doi.org/10.1038/nrg.2016.112 1.1 1.2 1.3<br>
http://www.annualreviews.org/doi/10.1146/annurev-cellbio-100616-060531 1.1<br>
https://doi.org/10.1016/j.molcel.2013.02.011 1.1 structure<br>
http://www.genesdev.org/cgi/doi/10.1101/gad.281964.116. 1.1<br>




