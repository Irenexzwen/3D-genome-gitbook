# GIVE - Genomic Interaction Visualization Engine
[Give](https://zhong-lab-ucsd.github.io/GIVE_homepage/) is a highly adaptive and interactive open source programming library. It provides the easiest way to  a portable genome browser to examine geneome interactions with different kinds of data, which can be embedded in your own websites. 

Publication (https://www.biorxiv.org/content/early/2018/03/15/177832)

## Architecture of GIVE
The architecture of **GIVE** is important for users to understand how it works and how to use it. 
In generally, **GIVE** is composed of two parts:
- HTML tag library
- GIVE-Toolbox

**HTML tag library** is used to specify what types of data should be included in the browser by indicating specific tags in the code. <\br>
**GIVE-Toolbox** is a set of command line commands to add and manage custom data, which automates all necessary database operations relieving the user from working with a database language. 

Besides, **[GIVE Data Hub](https://www.givengine.org/give-data-hub.html)** holds large number of datasets, users can select some of them to view and compare and generate the HTML code to share or embed. User can also upload their own datasets to it with conformation from GIVE team.

## Distinguished Features
###1) Oneline multiple types of genome interactions viewer
- multitypes of interaction
- double layer display
- interactive presentation

a) GIVE includes genome-interaction data (Hi-C, ChIA-PET), transcriptome-genome interaction data (MARGI [8], GRID-seq [9]) and transcriptome interaction data (PARIS [10], MARIO [11], LIGR-seq [12], SPLASH [13])

###2) Portable genome browser generator
- automatic webpage generation with GIVE-HUG
- embed the code on your own webpage 

###3) Managing your own data


 