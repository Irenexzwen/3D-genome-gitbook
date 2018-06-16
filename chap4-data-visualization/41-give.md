# GIVE - Genomic Interaction Visualization Engine
[Give](https://zhong-lab-ucsd.github.io/GIVE_homepage/) is a highly adaptive and interactive open source programming library. It provides the easiest way to  a portable genome browser to examine geneome interactions with different kinds of data, which can be embedded in your own websites. 

<!-- header source -->
<script src="https://www.givengine.org/bower_components/webcomponentsjs/webcomponents-lite.min.js"></script> 
<link rel="import" href="https://www.givengine.org/components/chart-controller/chart-controller.html">

<div style="position: relative; width: 100%; height: 600px">
<chart-controller title-text="A 2-minute starter of building a genome browser with GIVE" ref="hg19" num-of-subs="2" coordinates='["chr18:19140000-19450000", "chr18:19140000-19450000"]' group-id-list='["genes", "CHi-C_promoter"]'></chart-controller>
</div>
**A quick example by embedding code generated from GIVE, What a fantasia!**

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

###2) Portable genome browser generator
- automatic webpage generation with GIVE-HUG
- embed the code on your own webpage 

###3) Managing your own data
- upload your dataset to Data hub

##Get started
Here, we'll show few examples to get you prepared before you dive into details and personalized adjustment. Part of the showcases are come from [GIVE homepage Examples]() ,[Tutorials]() 

 