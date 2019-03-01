---
description: 'Contributed by Victoria Tom, BENG183 2018 Fall. UCSD'
---

# A Brief Introduction to Machine Learning

## A Brief Introduction to Machine Learning

#### By Victoria Tom

* Overview
* Application to Bioinformatics
* Distance Functions
* Clustering Methods
* Hierarchical Clustering
* K-Means Clustering
* Summary

### Overview

Machine learning is currently a very popular field of research, in part because of its ability to analyze very large data sets at unprecedented scale in a variety of different fields. From analyzing consumer purchasing behavior to figuring out the best way to classify a disease, machine learning has the potential to be applied to many of our current research problems.

So what is machine learning?

At a high level, **machine learning** is a general term that we use to describe computer algorithms that we can use to predict an outcome based on the data that we input.

There are a couple different types of machine learning, which we use to solve different problems.

One way of looking at a problem is trying to decide if we want the output to be a result of supervised or unsupervised learning.

In **supervised learning**, we already know the **labels** of the output. These labels represent all of the different possible expected outcomes of our program. For example, if we want to use machine learning to figure out if a flower is a tulip or a rose, we already know beforehand what the expected output should be - either "tulip" for a picture of a tulip, or "rose" for a picture of a rose. We tend to use this type of learning to predict an outcome that we know.

In **unsupervised learning**, we don't know beforehand what we expect the output to look like beforehand. We let the computer decide how many labels there should be to best separate the different types of data. Unsupervised learning algorithms tend to focus more on how best to group different pieces of data together without us needing to specify what the different groups should be. We tend to use this type of learning to analyze sets of data for outcomes that we don't know.

We can also distinguish between discrete and continuous outputs from the machine learning algorithms.

**Discrete** outputs tend to come from a distinct and finite set of bracketed values, with no "in-between" values. For example, a discrete output can be an integer value like "3" if we're trying to count how many cats are in a picture, or a category like "romance" if we're trying to figure out what genre a piece of prose is written in.

**Continuous** outputs tend to be values along a sliding scale, with a potentially infinite number of values. An example of a continuous output would be ".9876564" for how likely it is that a given picture is of a cat, since ".9876564" is not a category that we'd predefine, nor is it a result that many other data points would also be classified as.

Below is an image that gives examples of each kind of machine learning.

![](../../.gitbook/assets/image%20%2811%29.png)

### Application to Bioinformatics

**Clustering** is an important tool that is often used in bioinformatics because of its ability to group data into different groups that we can then analyze. Clustering algorithms start with a collection of _n_ objects that we want want to divide into _k_ clusters so that objects within a cluster are more "similar" to each other than objects in other clusters.

A common application is to use clustering on gene expression data. By analyzing how different genes are grouped, we can predict functions of unknown by using known ones. We can also discover shared regulatory regions in DNA sequences and discover subtypes of a given disease.

For example, [researchers](https://www.ncbi.nlm.nih.gov/pubmed/11707567) were able to classify different subtypes of lung cancer by analyzing the differences in gene expression between them.

![](../../.gitbook/assets/image%20%288%29.png)

Bhattacharjee et al. \(2001\) Classification of human lung carcinomas by mRNA expression profiling reveals distinct adenocarcinoma subclasses Proc. Natl. Acad. Sci. USA, Vol. 98, 13790-13795

### Distance Functions

Before we move into a discussion of various clustering algorithms, let's go into the basics of how we determine how to group different data points into clusters.

In clustering, we usually try to group things that are "similar" together into clusters. We use **distance functions** as a way to quantitatively measure how "close" data points are to each other. Lower distances mean that the points are closer together, while larger values indicate less similarity.

There are several different ways to calculate the distance between two data points. The most common is the **Euclidean distance function**, which uses the distance formula to calculate the distance between two points.

Another alternative is to use **Pearson's correlation** \(aka Pearson’s r\) to measure how correlated the two profiles are, with values ranging between -1 and 1.

### Clustering Methods

One we determine how to measure how "close" data points are to each other, we need to determine how we measure the distances between different clusters.

One method is using the **Unweighted Pair Group Method with Arithmetic Mean \(UPGMA\)**, which calculates the average distance from each point in the cluster to all other points in another cluster. Once that is calculated, the two clusters with the lowest average distance are then joined together, which will create a new cluster.

Another clustering method is **Complete Linkage**. This method instead measures how similar 2 clusters are using the biggest dissimilarity between a member of one cluster and a member of another cluster. This method will tend to produce very tight clusters.

Another method is to do **Single Linkage**. This method measures how similar 2 clusters are using the minimum dissimilarity between members of the 2 clusters. This method of clustering tends to produce clusters in long chains and can identify outliers readily.

![](../../.gitbook/assets/image%20%2824%29.png)

### Hierarchical Clustering

Now let's look at one algorithm for clustering - the hierarchical clustering algorithm.

Using the hierarchical clustering algorithm will result in a dendrogram that groups every single data point into one large cluster, with similar data points grouped closer together.

The basic algorithm for hierarchical clustering is as follows: 1. Calculate the similarity between all possible combinations of two profiles using a distance function. 2. Place each profile in a separate cluster. 3. Group the two most similar clusters together to form a new cluster. 4. Recalculate the similarity between the new cluster and all the other remaining clusters using a user-defined clustering method. 5. Repeat steps 3 and 4 until all of the profiles end up in one large cluster.

We can then "cut" our dendrogram at a level that gives us the number of clusters that we want.

Here is an animation that shows how hierarchical clustering behaves. ![](https://github.com/Zhong-Lab-UCSD/BENG183/blob/master/finalPaper/IntroToMachineLearning_2/hClust.gif)

![](../../.gitbook/assets/image%20%2815%29.png)

### K-Means Clustering

The other algorithm we will cover is the k-means algorithm. Unlike hierarchical clustering, we know beforehand the number of clusters that we want \(k\).

The basic algorithm for k-means clustering is as follows:

1. Choose a k-value for the number of clusters we want to end up with.
2. Select k number of starting points that we want to initialize to start our clusters. 
3. For each data point, find the closest mean vector and assign the object to the corresponding cluster.
4. For each cluster, update its mean vector according to the current assignments.

![](../../.gitbook/assets/image%20%282%29.png)

We keep repeating the last two steps until a stopping criteria is met. Unlike the hierarchical clustering algorithm, the k-means clustering algorithm isn't always guaranteed to terminate. It can stop during **convergence**, when the algorithm no longer reassigns points, or it can run indefinitely until it stops at a user-defined number of iterations.

This contrasts with hierarchical clustering which has a more finite and predictable termination step \(when everything is inside of one cluster\). Additionally, the k-means algorithm may produce different outcomes based on how we initialize our initial k points.

Here is an animation that shows how k-means clustering behaves.

![](../../.gitbook/assets/image%20%284%29.png)

### Summary

In summary, machine learning is a powerful tool that we can use to analyze data. In bioinformatics, we commonly use clustering algorithms to analyze our data, with both k-means and hierarchical clustering algorithms as viable options. In the future, it is likely that machine learning will be used to drive furhter innovations in the fields of personalized medicine and genomics.

### Sources

1. Bhattacharjee et al. \(2001\) Classification of human lung carcinomas by mRNA expression profiling reveals distinct adenocarcinoma subclasses Proc. Natl. Acad. Sci. USA, Vol. 98, 13790-13795 
2. Sheng Zhong "Intro to machine learning", BENG 183
3. Derek Jow, Joey Sun, Victoria Tom "Introduction to Machine Learning", BENG 183
4. [https://commons.wikimedia.org/wiki/File:K-means\_convergence.gif](https://commons.wikimedia.org/wiki/File:K-means_convergence.gif)
5. [https://dashee87.github.io/data science/general/Clustering-with-Scikit-with-GIFs/](https://dashee87.github.io/data%20science/general/Clustering-with-Scikit-with-GIFs/)

