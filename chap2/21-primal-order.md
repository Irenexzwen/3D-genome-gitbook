# 2.2 Experimental techniques for accessing primary-order Chromatin
1. [Introduction](#introduction)
2. [Selected methods for primary structure](#222)<br>
    2.1. [ChIP-seq](#a)<br>
    2.2. [DNase-seq](#b)<br>
    2.3. [ATAC-seq](#c)<br>
    2.4. [MNase-seq](#d)<br>
    2.5. [FAIRE-seq](#e)<br>
3. [Selected methods comparison](#223)

## 2.2.1 Introduction<a name="introduction"></a>
The primary-order chromatin usually refers to the unpacked chromatin fiber where 11-nm coils of nucleosomes are exposed [[1]](https://doi.org/10.1016/j.csbj.2018.02.003). Primary structure encompasses DNA methylation and sequence features, DNA-bound factors, nucleosome position and modifications, and DNA accessibility [[2]](http://dx.doi.org/10.1016/j.tig.2015.03.010). Biological functions and gene expression are intimately rely on primary order structure, especially chromotin accessibility mediated by protein complexes and epigenetic modifications.
## 2.2.2 Selected methods for primary structure<a name="222"></a>
![](/assets/primary.png)
### ChIP-seq<a name="a"></a>
ChIP-seq [[3]](http://www.genome.org/cgi/doi/10.1101/gr.136184.111.) **Chromatin immunoprecipitation followed by next-generation DNA sequencing**. A method to identify DNA-associated protein-binding sites. Chromatin is fixed in cells then fragmented by sonication or MNase digestion before enrichment for the protein epitope of interest using a specific antibody. Crosslinks are reversed using proteinase K and heat and the DNA is then prepared for analysis by sequencing, array hybridization, or PCR [[2]](http://dx.doi.org/10.1016/j.tig.2015.03.010).
### DNase-seq<a name="b"></a>
DNase-seq [[4]](https://www.nature.com/articles/nmeth.1313) is a method in which **DNase I digestion** of chromatin is combined with next-generation sequencing to identify regulatory regions of the genome, including enhancers and promoters and TF footprint.DNA in isolated nuclei is digested with DNase I at a concentration that must be optimized for each experiment. A library is prepared from the digested fragments by ligation of adapters and cleavage of ~20-bp sequence tags followed by size selection of a unique library molecule size or by biochemical fractionation of fragments followed by ligation of sequencing adapters [[2]](http://dx.doi.org/10.1016/j.tig.2015.03.010).
### ATAC-seq<a name="c"></a>
ATAC-seq [[5]](https://www.ncbi.nlm.nih.gov/pubmed/24097267) **Assay for transposase- accessible chromatin using sequencing**. A method that combines next-generation sequencing with in vitro transposition of sequencing adapters into native chromatin.**Tn5 transposase** is used to transpose sequencing adapter oligos into the gDNA of permeabilized, unfixed cells. The resulting library is then purified and sequenced.

### MNase-seq<a name="d"></a>
Nucleosome-associated DNA is particularly insensitive to digestion by **micrococcal nuclease (MNase)**. With this feature, MNase-seq [[6]](https://doi.org/10.1016/j.cell.2007.05.009) [[7]](https://doi.org/10.1016/j.cell.2008.02.022) [[8]](https://www.nature.com/articles/ng.545) is a powerful tool to study the open chromotin region. The enzyme cut the exposed DNA with sticky ends. Just like the packman shows, the enzyme will digest the helix until it reaches an obstruction，such as a nuecleosome or other proteins [[9]](https://doi.org/10.1038/nrg3788).
### FAIRE-seq<a name="e"></a>
FAIRE-seq [[10]](http://www.genome.org/cgi/doi/10.1101/gr.5533506) is **Formaldehyde-assisted isolation of regulatory elements followed by sequencing**. Nucleosome-bound DNA is crosslinked and removed by phenol–chloroform extraction and the remaining nucleosome- free DNA is analyzed by microarray or sequencing.This is a simpler assay for open chromatin than DNase-seq, although its **resolution** is somewhat lower (around 200bp).

##2.2.3 Selected methods comparison<a name="223"></a> 
<table>
 <tbody>
    <tr>
        <th>Method</td>
        <th>Targets</td>
        <th>Resolution(bp)</td>
        <th>Notes</td>
    </tr>
    <tr>
        <td>ChIP-seq</td>
        <td>Mapping of DNA- bound proteins<br>(including nucleosomes)</td>
        <td>~100</td>
        <td><ul><li><b>Higher resolution than ChIP-chip</b></li><li>Bias towards CG-rich sequence</li></ul></td>
    </tr>
    <tr>
    <td>DNase-seq</td>
    <td>Open chromatin</td>
    <td>~1</td>
    <td><ul><li><b>Detects TF footprints</li><li><b>Greater sensitivity at promoters than FAIRE-seq</b><\li><li>Bias towards CG-rich sequence</li><li>Time-consuming</li></ul></td>
    </tr>
    <tr>
    <td>ATAC-seq</td>
    <td>Open chromatin<br>nucleosome positions<br>TF footprints</td>
    <td>~1</td>
    <td><ul><li><b>Simple, fast protocol</li><li><b>lower input requirements(1-50,000 cells)</li><li>lower sequencing depth</b><\li><li>Bias towards CG-rich sequences<br>sequence bias of Tn5 transposase </li><li>Fresh tissue isolation, mitochondrial DNA contamination, immature data analysis tools</li></ul></td>
    </tr>
    <tr>
    <td>MNase-seq</td>
    <td>Nucleosomes<br>Inferred closed regions</td>
    <td>~1-10</td>
    <td><ul><li><b>Genome-wide nucleosome core positioning</li><li>large numbers of reads for sufficient depth</li><li>MNase sequence bias</li></ul></td>
    </tr>
    <tr>
    <td>FAIRE-seq</td>
    <td>Open chromatin</td>
    <td>~200</td>
    <td><ul><li><b>Simple experimental procedure</li><li>Variable crosslink efficienc</li><li>lower resolution</li><li>high noise-to-signal ratio</li></ul></td>
    </tr>
 </tbody>
</table>
* Other techniques for primary-order structure detection one can refer to review [2]. Comprehensive discussion for technical bias of these methods one can refer to review [9].
















# Referrence 
[1] Chang, Pearl, et al. "Computational Methods for Assessing Chromatin Hierarchy." <br>
Computational & Structural Biotechnology Journal (2018).
[2] Risca, Viviana I,, and W. J. Greenleaf. "Unraveling the 3D genome: genomics tools for multiscale exploration." Trends in Genetics 31.7(2015):357-372.<br>

[3] Landt, Stephen G., et al. "ChIP-seq guidelines and practices of the ENCODE and modENCODE consortia." Genome research 22.9 (2012): 1813-1831.<br>

[4] Hesselberth, Jay R., et al. "Global mapping of protein-DNA interactions in vivo by digital genomic footprinting." Nature methods 6.4 (2009): 283. <br>

[5] Buenrostro, Jason D., et al. "Transposition of native chromatin for fast and sensitive epigenomic profiling of open chromatin, DNA-binding proteins and nucleosome position." Nature methods 10.12 (2013): 1213.<br>

[6] Barski, Artem, et al. "High-resolution profiling of histone methylations in the human genome." Cell 129.4 (2007): 823-837. **This paper reports the first use of MNase digestion followed by ChIP–seq**.<br>

[7] Schones, Dustin E., et al. "Dynamic regulation of nucleosome positioning in the human genome." Cell 132.5 (2008): 887-898.<br>

[8] He, Housheng Hansen, et al. "Nucleosome dynamics define transcriptional enhancers." Nature genetics 42.4 (2010): 343.<br>

[9] Meyer, Clifford A., and X. Shirley Liu. "Identifying and mitigating bias in next-generation sequencing methods for chromatin biology." Nature Reviews Genetics 15.11 (2014): 709.<br>

[10] Giresi, P.G. et al. (2007) FAIRE (formaldehyde-assisted isolation of regulatory elements) isolates active regulatory elements from human chromatin. Genome Res. 17, 877–885.<br>


