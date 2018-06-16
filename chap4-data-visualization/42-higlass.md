# HiGlass 
HiGlass is a web-based tool for exploring genomic contact matrices and tracks.HiGlass is a viewer for HiC and other genomic data. It can be used online (http://higlass.io), or run locally with private data(docker). It uses a client-server architecture to allow users to view large contact matrices in a web browser (https://www.biorxiv.org/content/early/2017/10/30/121889). 


## Distinguished features
 - smooth navigation, continuous interface
 - multiple datasets, map link, auto sync, optional sync(by loc or zoom) 
 - various representations (horizontal triangular, vertical triangular, 2D heatmap, 1D track)
 - highly configurable 
 - diff scale of data (linear, log)
 - export (SVG, JSON config) with metadata rather than lengthy url records everything
 - share data local net or publicly
 - locally or web databased

## Get Started
We will unfold the main features of Higlass as follows:
1. Show anatomy of HiGlass **view** board.
2. Show the category of **tracks** which represents multi-omics data.
3. Show how to upload your **own** datasets, which is the most important part.

Just a reminder, all the information illustrated here can be learned from:
[1] https://github.com/hms-dbmi/higlass/wiki &nbsp
[2] https://hms-dbmi.github.io/hic-data-analysis-bootcamp 
We're trying our best to walk you through the gist of this software within the least of your time by our understanding and reorganized materials :D 

### Concept1: Anatomy of HiGlass view board
"Tracks" and "Views" are the two most basic ingredients of a Higlass view. Each view is composed of a set of tracks which share common axes. All view operations can be found [here](https://github.com/hms-dbmi/higlass/wiki/View-Operations). 
![](/assets/ana_view.jpg)
- A **view** is simply the area with a gray bar at the top. A view can be understood as a canvas, and **tracks** are figures on this canvas. There is nothing elese. **Tracks** are of various types and will be elaborated later. 

#### Operations for Views includes:
##### a) **Resize** views before **adding(copying)** new views.<br>
We want to create four views in total showing two different datasets.To start, we'll resize the current view and replicate it twice

<p style="text-align: center">
    <video width="500" loop="loop" autoplay="autoplay">
        <source src="https://s3.amazonaws.com/pkerp/public/img/hic-bootcamp-presentation/resize-and-clone-twice.mp4" type="video/mp4">
    </video>
</p>

##### b) Cross-view operations
transferring or linking parameters (such as **scaling factor** and **location**) between two separate views. Examples:Let's make sure the top two rows and the bottom two rows always show the same locations as each other.

<p style="text-align: center">
    <video width="500" loop="loop" autoplay="autoplay">
        <source src="https://s3.amazonaws.com/pkerp/public/img/hic-bootcamp-presentation/take-and-lock-zoom-and-location.mp4" type="video/mp4">
    </video>
</p>

##### c) View synchronization
location or zoom or both(just for two views at a time, if you want to sync many views, you have to do it pair by pair).

##### d) Go to interesting location

<p style="text-align: center">
    <video width="500" loop="loop" autoplay="autoplay">
        <source src="https://s3.amazonaws.com/pkerp/public/img/hic-bootcamp-presentation/zoom-top-and-bottom-to.mp4" type="video/mp4">
    </video>
</p>

##### e) Project viewport

<p style="text-align: center">
    <video width="500" loop="loop" autoplay="autoplay">
        <source src="https://s3.amazonaws.com/pkerp/public/img/hic-bootcamp-presentation/project-viewport-on.mp4" type="video/mp4">
    </video>
</p>   

##### f) **Unclock** and **close**


### Concept2: Track types
#### Common feeatures for every track:
- Label (Positions, color, opacity, background color)
- Color mmap:from matplotlib or custom defined(https://github.com/hms-dbmi/higlass/wiki/Rectangular-heatmap). **Configure Series --> Color map**
![](/assets/colormap.jpg)
- zoom limit
#### Different tracks( Icon | Higlass-wiki | Special-features):
<table>
<tbody>
<tr>
<td><a href="https://github.com/hms-dbmi/higlass/wiki/Rectangular-heatmap"><img src="https://cloud.githubusercontent.com/assets/2143629/24176191/e66e26e0-0e70-11e7-84fd-e945b95048b7.png" height="50px"></a></td>
<td><a href="https://github.com/hms-dbmi/higlass/wiki/Rectangular-heatmap">Rectangular heatmap</a></td>
<td><ul><li>Transforms(ICE,KR,etc)-see Chap3.2</li><li>Value scaling(linear,log)</li><li>Zoom limit(5k-20M)</li></ul></td>
</tr>
<tr>
<td><a href="https://github.com/hms-dbmi/higlass/wiki/Horizontal-and-vertical-heatmaps"><img src="https://cloud.githubusercontent.com/assets/2143629/24176286/67e87978-0e71-11e7-9441-cdabbf2fc804.png" height="50px"></a></td>
<td><a href="https://github.com/hms-dbmi/higlass/wiki/Horizontal-and-vertical-heatmaps">Horizontal and vertical heatmaps</a></td>
<td><ul><li>45° roatate of 2D heatmap</li><li>Can be added lef,right,top,bottom</li><li>Default faces: down & right(can be fpliiped)</li></ul></td>
</tr>
<tr>
<td><a href="https://github.com/hms-dbmi/higlass/wiki/Line-tracks"><img src="https://cloud.githubusercontent.com/assets/2143629/24176389/0acb6b8c-0e72-11e7-9396-5e0e7a242d82.png" height="50px"></a></td>
<td><a href="https://github.com/hms-dbmi/higlass/wiki/Line-tracks">Line</a></td>
<td><ul><li>Scaling(linear,log)</li><li>Label position</li><li>Axis position</li><li>Stroke color</li></ul></td>
</tr>
<tr>
<td><a href="https://github.com/hms-dbmi/higlass/wiki/Chromosome-grid"><img src="https://cloud.githubusercontent.com/assets/2143629/24176445/677221f0-0e72-11e7-81f3-ae29c71c1f6d.png" height="50px"></a></td>
<td><a href="https://github.com/hms-dbmi/higlass/wiki/Chromosome-grid">Chromosome grid</a></td>
<td><ul><li>Grid on chromosome scale</li><li>User can define the scale</li></ul></td>
</tr>
<tr>
<td><a href="https://github.com/hms-dbmi/higlass/wiki/Chromosome-axis"><img src="https://cloud.githubusercontent.com/assets/2143629/24176330/b38cb0c4-0e71-11e7-9ed7-60e8bee1f726.png" height="50px"></a></td>
<td><a href="https://github.com/hms-dbmi/higlass/wiki/Chromosome-axis">Chromosome axis</a></td>
<td><ul><li>Diff scale for zoom in&out</li><li>User can define the scale</li></ul></td>
</tr>
<tr>
<td><a href="https://github.com/hms-dbmi/higlass/wiki/Viewport-projection"><img src="https://cloud.githubusercontent.com/assets/2143629/24176502/afeb5f46-0e72-11e7-8c1d-0c3d12d75eff.png" height="50px"></a></td>
<td><a href="https://github.com/hms-dbmi/higlass/wiki/Viewport-projection">Viewport projection</a></td>
<td><ul><li>show one dataset with two different resolutions</li><li>Open from view</li></ul></td>
</tr>
<tr>
<td><a href="https://github.com/hms-dbmi/higlass/wiki/Gene-annotations"><img src="https://cloud.githubusercontent.com/assets/2143629/24176594/48af7d98-0e73-11e7-8a10-81c5e64b41be.png" height="50px"></a></td>
<td><a href="https://github.com/hms-dbmi/higlass/wiki/Gene-annotations">Gene annotations</a></td>
<td><a href="https://github.com/hms-dbmi/clodius/wiki/Gene-annotations">Developer docs</a></td>
</tr>
</tbody>
</table>


### Chapter3 Upload your own data 
In most cases, people would like to upload their own data for different tracks. To embed your own data and present them on your own browser, you should follow these steps.
- Download docker
- Install python package: cooler and clodius 
- Capsule your data into docker container

#### Install docker:
[Docker](https://www.docker.com) is a computer program that performs operating-system-level virtualization also known as containerization. It resembles VM in some ways but much thinner. Instead of virtualizing hardware, containers rest on top of a single Linux instance. This means you can leave behind the useless elements, leaving you with a small, neat capsule containing your application. Higlass also embrace docker. 

To **install** docker, you can first download and install it on your local machine or server [docker CE](https://www.docker.com/community-edition)(community edition). Win and Mac users can directly use it by open it. Linux users need to start the service by running the following command with root privileges.
```
service docker start
```

#### Install & Run higlass container
Next, **pull down** the higlass-container from higlass-docker repository [(tutorial)](https://github.com/hms-dbmi/higlass-docker). After that, you can try to create an instance on that containner and open your own higlass website in your own browser [(tutorial)](https://github.com/hms-dbmi/higlass/wiki#processing-and-importing-data). However, you may get confused about some commands if you're new to Docker. To solve this, you can refer to [docker's docs](https://docs.docker.com/engine/reference/commandline/docker/) or to make life eaiser: [Docker cheat sheet](https://www.docker.com/sites/default/files/Docker_CheatSheet_08.09.2016_0.pdf). 


```
docker pull gehlenborglab/higlass 
# If no version tag is specified,docker will download the latest.
```
One important thing is that you can not change parameters of an already setup container, you have to stop it first, remove that and create a new one. This also suggest that, we'd better not put your data into a container, instead, we store the data locally and map it to different container by <code>docker --run -volume</code>. 
```
docker stop higlass-container
docker rm higlass-container

docker run --detach \ # start the containner background,it will last until you rm your container
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
[Cooler](https://pypi.org/project/cooler/) is a support library for a sparse, compressed, binary persistent storage format, called cool, used to store genomic interaction data, such as Hi-C contact matrices. To get started you can try this [walkthrough](https://github.com/mirnylab/cooler-binder/blob/master/cooler_cli.ipynb). Basically this tool include some useful functions listed below (not all included). 















