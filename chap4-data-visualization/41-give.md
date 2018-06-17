# GIVE - Genomic Interaction Visualization Engine
[Give](https://zhong-lab-ucsd.github.io/GIVE_homepage/) is a highly adaptive and interactive open source programming library. It provides the easiest way to  a portable genome browser to examine geneome interactions with different kinds of data, which can be embedded in your own websites. 

<!-- header source -->
<script src="https://www.givengine.org/bower_components/webcomponentsjs/webcomponents-lite.min.js"></script> 
<link rel="import" href="https://www.givengine.org/components/chart-controller/chart-controller.html">

<div style="position: relative; width: 100%; height: 600px">
<chart-controller title-text="A 2-minute starter of building a genome browser with GIVE" ref="hg19" num-of-subs="2" coordinates='["chr18:19140000-19450000", "chr18:19140000-19450000"]' group-id-list='["genes", "CHi-C_promoter"]'></chart-controller>
</div>


**A quick example by embedding code generated from GIVE into gitbook, What a fantasia!**
This is an interactive pannel, where you can change the chromosome location(leftup corner), interaction datasets(left columns), even zoom-in-and-out by placing your mouse on the chromosome ruler and scoll the mouse wheel!

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
Here, we'll show few examples to get you prepared before you dive into details and personalized adjustment. Part of the showcases are come from [GIVE homepage Examples]() and [Tutorials](https://github.com/Zhong-Lab-UCSD/Genomic-Interactive-Visualization-Engine/tree/master/tutorials).

### Example1: Create a GIVE viewer based on html code
With GIVE generator, you can get a short piece of code without much effort. Thanks to the specialized HTML library, personal preferences can be easily defined by changing parameters of <code>chart-controller </code> or <code>chart-area</code> libraries.

Once you have the code, there are few ways to view your browser!
- Online HTML testing website like [jsfiddle](https://jsfiddle.net/)
- Local <code>.html</code> file (just copy paste the code into it), and then open it.
- Personal webpage, or html based apps like gitbook (a kind of markdown editor). 

a) with online test environment, you can refer to [GIVE Tutorial 0](https://github.com/Zhong-Lab-UCSD/Genomic-Interactive-Visualization-Engine/blob/master/tutorials/0-shortexample.md):
![](/assets/2-minutes-show.gif)

c) if you want to integrate the code on your personal website, you can add the code in your html file. Please pay attention that **all features in <code>char-controller<\code> should not be seperated by newline. To best fit your browser, you could wrap the controller with div tag.**
```
<!-- header source -->
<script src="https://www.givengine.org/bower_components/webcomponentsjs/webcomponents-lite.min.js"></script> 
<link rel="import" href="https://www.givengine.org/components/chart-controller/chart-controller.html">

<div style="position: relative; width: 100%; height: 600px">
<chart-controller title-text="A 2-minute starter of building a genome browser with GIVE" ref="hg19" num-of-subs="2" coordinates='["chr18:19140000-19450000", "chr18:19140000-19450000"]' group-id-list='["genes", "CHi-C_promoter"]'></chart-controller>
</div>
```
You can [tweak](https://github.com/Zhong-Lab-UCSD/Genomic-Interactive-Visualization-Engine/blob/master/tutorials/1.2-html-tweak.md) the browser with different reference genomes, number of subview interactions, the data and the coordinates. 

### Example2: Generate personalized browser code with GIVE data hub
GIVE data hub has included a lot of public datasets.There are UCSC genome annotation, ChIP-seq data, RNA-seq data, Hi-C data, DNase data, Cage data, RipSeq data, interaction data so on and so forth. Users can select them from data hub and generate their own code to explore something interesting. 

![](/assets/datahub1.gif)


###Upload your own data 
Now that we've already got an idea how GIVE works, now we can explore our own data with the power of GIVE. 
- Download docker
- Install python package: cooler and clodius 
- Capsule your data into docker container

#### Install docker:
[Docker](https://www.docker.com) is a computer program that performs operating-system-level virtualization also known as containerization. It resembles VM in some ways but much thinner. Instead of virtualizing hardware, containers rest on top of a single Linux instance. This means you can leave behind the useless elements, leaving you with a small, neat capsule containing your application. Higlass also embrace docker. 

To **install** docker, you can first download and install it on your local machine or server [docker CE](https://www.docker.com/community-edition)(community edition). Win and Mac users can directly use it by openning it. Linux users need to start the service by running the following command with root privileges.
```
service docker start
```

#### Install & Run higlass container
Next, **pull down** the higlass-container from higlass-docker repository [(tutorial)](https://github.com/hms-dbmi/higlass-docker). After that, you can try to create an instance on that container and open your own higlass website in your own browser [(tutorial)](https://github.com/hms-dbmi/higlass/wiki#processing-and-importing-data). However, you may get confused about some commands if you're new to Docker. To solve this, you can refer to [docker's docs](https://docs.docker.com/engine/reference/commandline/docker/) or to make life easier: [Docker cheat sheet](https://www.docker.com/sites/default/files/Docker_CheatSheet_08.09.2016_0.pdf). 


```
docker pull gehlenborglab/higlass 
# If no version tag is specified, docker will download the latest.
```
One important thing is that you can not change parameters of an already setup container, you have to stop it first, remove that and create a new one. This also suggests that we'd better not put your data into a container, instead, we store the data locally and map it to a different container by <code>docker --run -volume</code>. 
```
docker stop higlass-container
docker rm higlass-container

docker run --detach \ # start the container background, it will last until you rm your container
           --publish 8888:80 \  # map a container’s port(80) to the host(8880) so that you can visit it with localhost:8888
           --volume ~/hg-data:/data \   # map local data dir ~/hg-data to container dir /data
           --volume ~/hg-tmp:/tmp \
           --name higlass-container \  # name of your container
           gehlenborglab/higlass
```
Here you go, if you intsall docker on your own computer then you can visit your higlass by <code>localhost:8888.com</code>. If you install docker on a server with IP:AA:BBB:CC:DD, then with url <code>AA:BBB:CC:DD:8888</code> you can see your own viewer on your browser. 

#### Create your own tracks data
You can use your own data to substitute tracks with specific format and datatype. Refer to [here](https://github.com/hms-dbmi/higlass/wiki#processing-and-importing-data) for more details.
<table>
  <tr>
    <th>Tracks</th>
    <th>Tools</th>
    <th>Filetype</th>
  </tr>
  <tr>
    <td>Contact matrix</td>
    <td>cooler</td>
    <td>cool</td>
  </tr>
  <tr>
    <td>Line</td>
    <td>clodius</td>
    <td>BigWig\bedGraphs</td>
  </td>
  </tr>
  <tr>
    <td>TAD annotation</td>
    <td>clodius</td>
    <td>bed-like</td>
  </td>
  </tr>
  <tr>
    <td>Gene annotation</td>
    <td>clodius</td>
    <td>bed-like</td>
  </td>
  </tr>
</table>

##### Tools: Cooler
[Cooler](https://pypi.org/project/cooler/) is a support library for a sparse, compressed, binary persistent storage format, called cool, used to store genomic interaction data, such as Hi-C contact matrices. To get started you can try this [walkthrough](https://github.com/mirnylab/cooler-binder/blob/master/cooler_cli.ipynb). Basically, this tool includes some useful functions listed below (not all included). 

- Do contact matrix balancing
- Create and load contact matrix
- generate zoom levels for Higlass viewer
- Display a contact matrix 
- ...































 
 