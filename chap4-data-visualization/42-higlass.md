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
[1] https://github.com/hms-dbmi/higlass/wiki
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
<td><a href="Rectangular-heatmap">Rectangular heatmap</a></td>
<td><ul><li>Transforms(ICE,KR,etc)-see Chap3.2</li><li>Value scaling(linear,log)</li><li>Zoom limit(5k-20M)</li></ul></td>
</tr>
<tr>
<td><a href="https://github.com/hms-dbmi/higlass/wiki/Horizontal-and-vertical-heatmaps"><img src="https://cloud.githubusercontent.com/assets/2143629/24176286/67e87978-0e71-11e7-9441-cdabbf2fc804.png" height="50px"></a></td>
<td><a href="Horizontal-and-vertical-heatmaps">Horizontal and vertical heatmaps</a></td>
<td><ul><li>45° roatate of 2D heatmap</li><li>Can be added lef,right,top,bottom</li><li>Default faces: down & right(can be fpliiped)</li></ul></td>
</tr>
<tr>
<td><a href="https://github.com/hms-dbmi/higlass/wiki/Line-tracks"><img src="https://cloud.githubusercontent.com/assets/2143629/24176389/0acb6b8c-0e72-11e7-9396-5e0e7a242d82.png" height="50px"></a></td>
<td><a href="Line-tracks">Line</a></td>
<td><ul><li>Scaling(linear,log)</li><li>Label position</li><li>Axis position</li><li>Stroke color</li></ul></td>
</tr>
<tr>
<td><a href="https://github.com/hms-dbmi/higlass/wiki/Chromosome-grid"><img src="https://cloud.githubusercontent.com/assets/2143629/24176445/677221f0-0e72-11e7-81f3-ae29c71c1f6d.png" height="50px"></a></td>
<td><a href="Chromosome-grid">Chromosome grid</a></td>
<td><ul><li>Grid on chromosome scale</li><li>User can define the scale</li></ul></td>
</tr>
<tr>
<td><a href="https://github.com/hms-dbmi/higlass/wiki/Chromosome-axis"><img src="https://cloud.githubusercontent.com/assets/2143629/24176330/b38cb0c4-0e71-11e7-9ed7-60e8bee1f726.png" height="50px"></a></td>
<td><a href="Chromosome-axis">Chromosome axis</a></td>
<td><ul><li>Diff scale for zoom in&out</li><li>User can define the scale</li></ul></td>
</tr>
<tr>
<td><a href="Viewport-projection"><img src="https://cloud.githubusercontent.com/assets/2143629/24176502/afeb5f46-0e72-11e7-8c1d-0c3d12d75eff.png" height="50px"></a></td>
<td><a href="Viewport-projection">Viewport projection</a></td>
<td><ul><li>show one dataset with two different resolutions</li><li>Open from view</li></ul></td>
</tr>
<tr>
<td><a href="Gene-annotations"><img src="https://cloud.githubusercontent.com/assets/2143629/24176594/48af7d98-0e73-11e7-8a10-81c5e64b41be.png" height="50px"></a></td>
<td><a href="Gene-annotations">Gene annotations</a></td>
<td><a href="https://github.com/hms-dbmi/clodius/wiki/Gene-annotations">Developer docs</a></td>
</tr>
</tbody>
</table>


### Upload your own data 
coming soon.









