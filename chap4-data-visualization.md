# Integrative data visualization

Here we'll mainly focused on Hi-C data visulazation, while most of the tools designed for Hi-C data are also able to integragate other data to improve the interpretability. 

We'll first walk through the **motivation** for visualizing complex dataset and then discuss the **object, needs and plights** in Hi-C data visualization. Then we'll provide a roadmap with some comparison of some of the most popular softwares available, based on some criteria that people may refer to. Finally we'll choose XXX as a showcase to prepare people for practical analysis. 

## 1.Motivation for Vis:
- Explore data feature, find patterns
- Interpretate the data 
- Verify or raise hypothesis

## 2.What data:
### i) Hi-C data:
- What is hi-c data, brief intro. may refer to other chapter 

###ii) Other useful info:
- genome, epigenome
- SNP
- CTCF, ChiP-seq 
- ChIA-PET
- ... 

## 3.Desired feaures of Hi-C Vis tools:
*** To take a cruise on a Hi-C map is just like navigate on a google map.(analogue, we could start from talking about features of some geographic apps like Google Map)***
***
- **Multi-omics** data, multi-techs data. Optional for users 
- **Vivid presentation**: Circos, Heatmaps, Birdview.
- **Interactive** presentation: mouse zoom-in & out, panning, sliding. 
- Easy to **share** the data: 
    - Cloud based, docker based, block chain(for server), URL share, QR code.
    - Records for eaxct parameters that enable collaborators and public to repeat the trials.
- Easy for **comparison**: 
 - Compare own data with published papaer —— preloaded dataset. 
 - Compare data from different analysis pipelines. 
 - Compare 2 datasets in one screen, with exact same scalability and same region, which needs fast and intelligent localization.
- **Desktop** applicaton, **off-line** usage.
- **3D** ,even **4D** vis.
- **One stop** service, the only desidered input is the raw reads data :D 

## 4.Current plights
- **Size**: trillions of pixels of one high resolution heatmap.
 - **Resolution** at different scale:
   - Compartments:1-10Mb 100-500 Kb bins
   - TADs: 0.1-1Mb 40-100Kb bins
   - Loops: 0.01-0.1Mb 10-40Kb bins
- **Storage** of the data, need a standard format ".hic"
- **Smart computation** with the need of in time zoom-in & out 
- **Input format** not uniform. A contact matrix, compressed TAD data or others.
- **Normalization** methods for comparing different datasets. 
- ...

## 5.Overview of tools
![](/assets/2.png)



## Referrence 

[1]	R. Calandrelli, Q. Wu, J. Guan, and S. Zhong, “GITAR : An open source tool for analysis and visualization of Hi-C data,” 2018.

[2]	B. Informatics, “HiGlass :   Web-based   Visual   Exploration   and   Analysis of   Genome   Interaction   Maps,” pp. 1–31, 2017.

[3]	D. Yang et al., “3DIV: A 3D-genome Interaction Viewer and database,” Nucleic Acids Res., vol. 46, no. D1, pp. D52–D57, 2018.

[4]	J. T. Robinson, D. Turner, N. C. Durand, H. Thorvaldsdóttir, J. P. Mesirov, and E. L. Aiden, “Juicebox.js Provides a Cloud-Based Visualization System for Hi-C Data,” Cell Syst., vol. 6, no. 2, p. 256–258.e1, 2018.

[5]	M. N. Djekidel, M. Wang, M. Q. Zhang, and J. Gao, “HiC-3DViewer: a new tool to visualize Hi-C data in 3D space,” Quant. Biol., vol. 5, no. 2, pp. 183–190, 2017.

[6]	G. G. Yardimci and W. S. Noble, “Software tools for visualizing Hi-C data,” Genome Biol., vol. 18, no. 1, 2017.









