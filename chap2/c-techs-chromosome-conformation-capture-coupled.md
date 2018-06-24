#2.3 C-Techs (chromosome conformation capture)-coupled 
1. [Introduction](#231)
2. [Overivew of 3C methods](#232)<br>
    2.1. [Specificity](#2321)<br>
    2.2. [Through-put and resolution](#2322)
3. [Hi-C](#233)
4. [ChIA-PET](#234)
5. [Selected methods comparison](#235)




## 2.3.1 Introduction<a name="231"></a>

The foundamental object of 3C(Chromosome Conformation Capture) techniques and 3C-derived methods is to understand the physical wiring diagram of the genome by identifying the physical interaction between chromosomes. 

To capture the interaction (crosslink between strings), there are few steps in general:
- Take a snapshot of the flowing cells - **Crosslink** with fixative agent (formaldehyde)
- Zoom in on crosslinked part and exclude untangled parts - **Digested** with a restriction enzyme
- Analyze the components come from the same chromatin - **Reverse crosslink** and **sequence**
- Finish the jigsaw puzzle and get the results - **Align** the reads and **summarize** the contacts

> Based on these general ideas, then we'll dive deeper by walking through two of the most popular  techniques and then briefly introduce some other methods. 

## 2.3.2 Overivew of 3C methods<a name="232"></a>

![](/assets/3creview.png)
*Figure I. Schematic Representation of Chromosome Conformation Capture (3C) and 3C-Derived Methods. These methods help to elucidate nuclear organization by detecting physical interactions between genetic elements located throughout the genome. Abbreviations: IP, immunoprecipitation; RE, restriction enzyme.*

To better understand the difference between these methods, I'd like to distingush them between the following couple of aspects:

#### 1) Specificity - What does _one, all, many_ mean<a name="2321"></a>
‘1’, ‘Many’ and ‘All’ indicate how many loci are interrogated in a given experiment. For example, ‘1 versus All’ indicates that the experiment probes the interaction profile between 1 locus and all other potential loci in the genome. ‘All versus All’ means that one can detect the interaction profiles of all loci, genome-wide, and their interactions with all other genomic loci [1].

These kind of specificity is determined by the primer when people use **specific primers** before PCR. 

#### 2) Through-put and resolution<a name="2322"></a>
Hi-C techniques has the highest through-put (billion reads per sample) but suffering of a relative low resolution of 0.1-1Mb. However, the other methods usually have a higher resolution  around 1kb. For more details one can refer to table2 in [2].

## 2.3.3 Hi-C<a name="233"></a>
Hi-C is the highest through-put version of 3C-derived technologies. Due to the decreasing cost of 2nd generation sequencing, hi-c is widely used.

The principle of Hi-C can be illustrated as:
![](/assets/hic.gif)


##### Hi-C critical steps
- Fixation: keep DNA conformed
- Digestion: enzyme frequency and penetration
- Fill-in: biotin for junction enrichment
- Ligation: freeze interactions in sequence
- Biotin removal: junctions only!
- Fragment size: small fragments sequence better
- Adapter ligation: paired-end and indexing
- PCR: create enough material for flow cell

##### Hi-C derived techniques 
- Hi-C original: [Lieberman-Aiden et al., Science 2010](doi: 10.1126/science.1181369)
- Hi-C 1.0: [Belton-JM et al., Methods 2012](doi: 10.1016/j.ymeth.2012.05.001)
- In situ Hi-C: [Rao et al., Cell 2014](doi: 10.1016/j.cell.2014.11.021)
- Single cell Hi-C: [Nagano et al., Genome Biology 2015](https://doi.org/10.1186/s13059-015-0753-7)
- DNase Hi-C [Ma, Wenxiu, Methods et al](https://www.ncbi.nlm.nih.gov/pubmed/25437436)
- Hi-C 2.0: [Belaghzal et al., Methods 2017](https://www.ncbi.nlm.nih.gov/pubmed/28435001)
- DLO-Hi-C: [Lin et al., Nature Genetics 2018](https://doi.org/10.1038/s41588-018-0111-2)
- Hi-C improving: [Golloshi et al., Methods 2018](https://www.biorxiv.org/content/biorxiv/early/2018/02/13/264515.full.pdf)
- Arima 1-day Hi-C: [Ghurye et al., BioRxiv 2018](https://www.biorxiv.org/content/early/2018/02/07/261149)

## 2.3.4 ChIA-PET<a name="234"></a> 
ChIA-PET is another method that combines ChIP and pair-end sequencing to analysis the chromtin interaction. It allows for targeted binding factors such as: estrogen receptor alpha, CTCF-mediated loops, RNA polymerase II, and a combination of key architectural factors. on the one hand, it has the benefit of achieving a higher resolution compared to Hi-C, as only ligation products involving the immunoprecipitated molecule are sequenced, on the other hand, ChIA-PET has systematic biases due to ChIP process:
- Only one type of binding factor selected
- Different antibodies
- ChIP conditions

The principle of ChIA-PET can be illustrated as:

##2.3.5 Selected methods comparison<a name="235"></a> **add year of invention 
<table>
 <tbody>
    <tr>
        <th>Method</td>
        <th>Targets</td>
        <th>Resolution</td>
        <th>Notes</td>
    </tr>
    <tr>
        <td>3C</td>
        <td>one-vs-one</td>
        <td>~1–10 kb<br></td>
        <td><ul><li><b>Higher resolution than ChIP-chip</b></li><li>Bias towards CG-rich sequence</li></ul></td>
    </tr>
    <tr>
    <td>4C</td>
    <td>one-vs-all</td>
    <td>~10 Mb</td>
    <td><ul><li><b>Detects TF footprints</li><li><b>Greater sensitivity at promoters than FAIRE-seq</b><\li><li>Bias towards CG-rich sequence</li><li>Time-consuming</li></ul></td>
    </tr>
    <tr>
    <td>5C</td>
    <td>many-vs-many</td>
    <td>~1 kb</td>
    <td><ul><li><b>Simple, fast protocol</li><li><b>lower input requirements</b><\li><li>Bias towards CG-rich sequences<br>sequence bias of Tn5 transposase </li><li>Fresh tissue isolation, mitochondrial DNA contamination, immature data analysis tools</li></ul></td>
    </tr>
    <tr>
    <td>Hi-C</td>
    <td>all-vs-all</td>
    <td>~1-10</td>
    <td><ul><li><b>Genome-wide nucleosome core positioning</li><li>large numbers of reads for sufficient depth</li><li>MNase sequence bias</li></ul></td>
    </tr>
    <tr>
    <td>ChIA-PET</td>
    <td>interaction of whole genome mediated by protein</td>
    <td>~200</td>
    <td><ul><li><b>Simple experimental procedure</li><li>Variable crosslink efficienc</li><li>lower resolution</li><li>high noise-to-signal ratio</li></ul></td>
    </tr>
 </tbody>
</table>
















#Referrence
[1] Schmitt, Anthony D., Ming Hu, and Bing Ren. "Genome-wide mapping and analysis of chromosome architecture." Nature reviews Molecular cell biology 17.12 (2016): 743.
[2] Risca, Viviana I., and William J. Greenleaf. "Unraveling the 3D genome: genomics tools for multiscale exploration." Trends in Genetics 31.7 (2015): 357-372.

https://doi.org/10.1016/j.csbj.2018.02.003<br>
https://github.com/hms-dbmi/hic-data-analysis-bootcamp/blob/master/HiC-Protocol.pptx 


