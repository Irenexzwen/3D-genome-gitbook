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
3. Show how to **interactively** explore **different datasets** at the same time. 
4. Show how to upload your **own** datasets, which is the most important part.

Just a reminder, all the information illustrated here can be learned from:
[1] https://github.com/hms-dbmi/higlass/wiki
[2] https://hms-dbmi.github.io/hic-data-analysis-bootcamp 
We're trying our best to walk you through the gist of this software within the least of your time by our understanding and reorganized materials :D 

### Concept1: Anatomy of HiGlass view board
"Tracks" and "Views" are the two most basic ingredients of a Higlass view. Each view is composed of a set of tracks which share common axes. All view operations can be found [here](https://github.com/hms-dbmi/higlass/wiki/View-Operations). 
![](/assets/ana_view.jpg)
- A **view** is simply the area with a gray bar at the top. A view can be understood as a canvas, and **tracks** are figures on this canvas. There is nothing elese. **Tracks** are of various types and will be elaborated later. 

#### Operations for **Views** includes:
##### a) **Resize** views before **adding(copying)** new views.<br>
We want to create four views in total showing two different datasets.To start, we'll resize the current view and replicate it twice

<p style="text-align: center">
    <video width="500" loop="loop" autoplay="autoplay">
        <source src="https://s3.amazonaws.com/pkerp/public/img/hic-bootcamp-presentation/resize-and-clone-twice.mp4" type="video/mp4">
    </video>
</p>

##### b) **Cross-view operations** 
transferring or linking parameters (such as **scaling factor** and **location**) between two separate views. Examples:Let's make sure the top two rows and the bottom two rows always show the same locations as each other.

<p style="text-align: center">
    <video width="500" loop="loop" autoplay="autoplay">
        <source src="https://s3.amazonaws.com/pkerp/public/img/hic-bootcamp-presentation/take-and-lock-zoom-and-location.mp4" type="video/mp4">
    </video>
</p>

##### c) View **synchronization**
location or zoom or both(just for two views at a time, if you want to sync many views, you have to do it pair by pair).

##### d) Go to interesting location

<p style="text-align: center">
    <video width="500" loop="loop" autoplay="autoplay">
        <source src="https://s3.amazonaws.com/pkerp/public/img/hic-bootcamp-presentation/zoom-top-and-bottom-to.mp4" type="video/mp4">
    </video>
</p>

##### e) Project viewport**

<p style="text-align: center">
    <video width="500" loop="loop" autoplay="autoplay">
        <source src="https://s3.amazonaws.com/pkerp/public/img/hic-bootcamp-presentation/project-viewport-on.mp4" type="video/mp4">
    </video>
</p>   

##### f) **Unclock** and **close**


### Concept2: Track types
#### Common feeatures for every track:
#### Different tracks:





## 7.How to interpretate the data 
- how to interpretate multi-omics data 
- how to choose the *best* result out of multi peak callers  
- **comming soon** 





# Lock zoom and location

* Let's make sure the top two rows and the bottom two rows always show the same locations as each other

<p style="text-align: center">
    <video width="500" loop="loop" autoplay="autoplay">
        <source src="https://s3.amazonaws.com/pkerp/public/img/hic-bootcamp-presentation/take-and-lock-zoom-and-location.mp4" type="video/mp4">
    </video>
</p>