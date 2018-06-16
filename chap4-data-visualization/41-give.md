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

## Distinguished Features
###1) Oneline multiple types of genome interactions viewer
- a) multitypes of interaction
- b) double layer display
- c) interactive presentation

GIVE has includes genome-interaction data (Hi-C [6], ChIA-PET [7]), transcriptome-genome interaction data (MARGI [8], GRID-seq [9]) and transcriptome interaction data (PARIS [10], MARIO [11], LIGR-seq [12], SPLASH [13])

###2) Portable genome browser generator
- a) Automatic webpage generation with GIVE-HUG
- b) embed the code on your own webpage 

###3) Managing own data


 