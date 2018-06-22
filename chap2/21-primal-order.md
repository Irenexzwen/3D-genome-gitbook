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
The primary-order chromatin usually refers to the unpacked chromatin fiber where 11-nm coils of nucleosomes are exposed [[1]](https://doi.org/10.1016/j.csbj.2018.02.003). Primary structure encompasses DNA methylation (pink) and sequence features, DNA-bound factors (blue), nucleosome position and modifications (multicolored), and DNA accessibility [[2]](http://dx.doi.org/10.1016/j.tig.2015.03.010).
## 2.2.2 Selected methods for primary structure<a name="222"></a>
![](/assets/primary.png)
### ChIP-seq<a name="a"></a>
ChIP-seq [[3]](http://www.genome.org/cgi/doi/10.1101/gr.136184.111.)(Chromatin immunoprecipitation followed by next-generation DNA sequencing). A method to identify DNA-associated protein-binding sites.
### DNase-seq<a name="b"></a>
### ATAC-seq<a name="c"></a>

### MNase-seq<a name="d"></a>
Nucleosome-associated DNA is particularly insensitive to digestion by **micrococcal nuclease (MNase)**. With this feature, MNase-seq [[5]](https://doi.org/10.1016/j.cell.2007.05.009) [[6]](https://doi.org/10.1016/j.cell.2008.02.022) [[7]](https://www.nature.com/articles/ng.545) is a powerful tool to study the open chromotin region. The enzyme cut the exposed DNA with sticky ends. Just like the packman shows, the enzyme will digest the helix until it reaches an obstruction，such as a nuecleosome or other proteins [[8]](https://doi.org/10.1038/nrg3788).
### FAIRE-seq<a name="e"></a>
FAIRE-seq [[6]](http://www.genome.org/cgi/doi/10.1101/gr.5533506) is **Formaldehyde-assisted isolation of regulatory elements followed by sequencing**. Nucleosome-bound DNA is crosslinked and removed by phenol–chloroform extraction and the remaining nucleosome- free DNA is analyzed by microarray or sequencing.This is a simpler assay for open chromatin than DNase-seq, although its **resolution** is somewhat lower (around 200bp).

##2.2.3 Selected methods comparison<a name="223"></a> **add year of invention 
<table>
<tbody>
<tr>
<td>Method</td>
<td>Descriptions</td>
<td>Resolutions</td>
</tr>
</tbody>
</table>























**Referrence **
[1] Chang, Pearl, et al. "Computational Methods for Assessing Chromatin Hierarchy." Computational & Structural Biotechnology Journal (2018).
[2] Risca, Viviana I,, and W. J. Greenleaf. "Unraveling the 3D genome: genomics tools for multiscale exploration." Trends in Genetics 31.7(2015):357-372.
[3] Landt, Stephen G., et al. "ChIP-seq guidelines and practices of the ENCODE and modENCODE consortia." Genome research 22.9 (2012): 1813-1831.
[5] Barski, Artem, et al. "High-resolution profiling of histone methylations in the human genome." Cell 129.4 (2007): 823-837. **This paper reports the first use of MNase digestion followed by ChIP–seq**
[6] Schones, Dustin E., et al. "Dynamic regulation of nucleosome positioning in the human genome." Cell 132.5 (2008): 887-898.
[7] He, Housheng Hansen, et al. "Nucleosome dynamics define transcriptional enhancers." Nature genetics 42.4 (2010): 343.
[8] Meyer, Clifford A., and X. Shirley Liu. "Identifying and mitigating bias in next-generation sequencing methods for chromatin biology." Nature Reviews Genetics 15.11 (2014): 709.
[6] Giresi, P.G. et al. (2007) FAIRE (formaldehyde-assisted isolation of regulatory elements) isolates active regulatory elements from human chromatin. Genome Res. 17, 877–885

