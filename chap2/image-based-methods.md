##2.1 Image based
Before the advent of C-technologies, the predominant method to study 3D genome organization was image-based methods. 

###2.1.1 Visualize DNA & RNA
#### FISH
FISH [[1]](http://www.pnas.org/content/pnas/79/14/4381.full.pdf) (fluorescence in situ hybridization) measured the spatial distances between two or more loci by hybridizing flurescently labeled probes to DNA after fixation, and then visualize the labels under light microscopy. 

**Limitations**:
- A large number of cells are need to get confident conclusion
- Resolution is limitted by the diffraction limit of light sources and the size of the probes (like 40kb)
- Limitted fluorescent labels

**Improvements**:
- Super-resolution microscopy [[2]](https://www.ncbi.nlm.nih.gov/pubmed/25896023)
- Short oligonucleotide-based probes [[3]](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3928790/)
- Multiplexed FISH method (more than 30 genomic loci at a time) [[4]](http://science.sciencemag.org/content/353/6299/598)
- HIPMap: High-throughput FISH [[5]](https://doi.org/10.1016/j.cell.2015.07.035)

#### CRISPR imaging
Efforts to label and image endogenous genomic elements in **live cells** have benefited from the series of
modular proteins with specific DNA recognition; like those methods developed for gene editing **(zinc-finger modules, TALEs and CRISPR (clustered regularly interspaced short palindromic repeat)-Cas (CRISPR-associated) system)**, these modules can guide the fluorescence signal to a specific sequence within the complex genome. Comprehensive review [[6]](https://www.annualreviews.org/doi/abs/10.1146/annurev-biophys-062215-010830) can be referred.

#### Tagged RNA sequence
Live-cell imaging of mRNA yields important insights into gene expression, transcriptional events. RNA hairpin sequences are inserted in tandem into a gene of interest to tag it, and coexpression of a fluorescent coat protein allows for mRNA detection. [[7]](https://www.nature.com/articles/nmeth.2305)
###2.1.2 Ultra structure and 3D organization
#### EM based methods
An electron microscope is a microscope that uses a beam of accelerated electrons as a source of illumination. As the wavelength of an electron can be up to 100,000 times shorter than that of visible light photons, electron microscopes have a higher resolving power than light microscopes and can reveal the structure of smaller objects.Transmission electron microscopy, combined with tomographic techniques, has been used for decades to generate 3D representations of biological structures, with resolutions down to the nanometer range.[[8]](https://www.cambridge.org/core/journals/microscopy-and-microanalysis/article/automated-procedures-for-the-alignment-and-reconstruction-of-multiple-tilt-electron-microscopic-tomography-data/ABB22F2BA4FF6E5E3E47109C58C745F0)
- TEM, serial-section EM tomography----reconstruction of large 3D volumes (250 to > 500 nm thick)[[9]](https://www.sciencedirect.com/science/article/pii/S1053811984710081)
- Multi-color EM [[10]](https://www.sciencedirect.com/science/article/pii/S2451945616303579), ChromEMT [[11]](http://science.sciencemag.org/content/357/6349/eaag0025)----Local ultrastructure and global 3D organization

#### X-ray based methods
#### Spatial and dynamic 3D nuclear organization
 - Wide-field / confocal / multiphoton 
 - LLS
 - etc .. 
    
# Referrence:
[1] Langer-Safer, Pennina R., Michael Levine, and David C. Ward. "Immunological method for mapping genes on Drosophila polytene chromosomes." Proceedings of the National Academy of Sciences 79.14 (1982): 4381-4385.
[2] Lakadamyali, Melike, and Maria Pia Cosma. "Advanced microscopy methods for visualizing chromatin structure." FEBS letters 589.20PartA (2015): 3023-3030.
[3] Beliveau, Brian J., Nicholas Apostolopoulos, and Chao‐ting Wu. "Visualizing genomes with Oligopaint FISH probes." Current protocols in molecular biology (2014): 14-23.
[4] Wang, Siyuan, et al. "Spatial organization of chromatin domains and compartments in single chromosomes." Science 353.6299 (2016): 598-602.
[5] Shachar, Sigal, et al. "Identification of gene positioning factors using high-throughput imaging mapping." Cell 162.4 (2015): 911-923.
[6] Chen, Baohui, Juan Guan, and Bo Huang. "Imaging specific genomic DNA in living cells." Annual review of biophysics 45 (2016): 1-23.
[7] Buxbaum, Adina R., Gal Haimovich, and Robert H. Singer. "In the right place at the right time: visualizing and understanding mRNA localization." Nature reviews Molecular cell biology 16.2 (2015): 95.
[8] Ellisman, Mark H., et al. "Automated procedures for the alignment and reconstruction of multiple tilt electron microscopic tomography data." Microscopy and Microanalysis 20.S3 (2014): 1258-1259.
[9] Soto, Gabriel E., et al. "Serial section electron tomography: a method for three-dimensional reconstruction of large structures." Neuroimage 1.3 (1994): 230-243. 
[10] Adams, Stephen R., et al. "Multicolor electron microscopy for simultaneous visualization of multiple molecular species." Cell chemical biology 23.11 (2016): 1417-1427.
[11] Ou, Horng D., et al. "ChromEMT: Visualizing 3D chromatin structure and compaction in interphase and mitotic cells." Science 357.6349 (2017): eaag0025.