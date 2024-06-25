---
layout: single
classes: wide
title: "Hierarchical Clustering: Intuition and Types"
header:
categories:
  - ML
author_profile: True
---
Today I faced a bit of a problem on my IBM UNSW data science problem, I have the feature “project_description” which includes a range of inputs ranging from “FACADE/ROOFS” to “FY16 RESO A IP SURVEILLANCE CAMERA INSTALLATION”. I recently used a automated labelling method for another feature, but this seem too big of a task for this feature. After researching for a bit I’v found another possible solution “Clustering”! So today I want to share a little overview about clustering, all information is from “Data and Knowledge Modeling and Analysis” via University of waterloo.

# What is clustering?

It is form of unsupervised learning, which means there is nothing we a trying to predict or classify, rather we are trying to put samples together based on similarity, therefore our data is unlabeled. What does this really mean? In supervised learning our client our label feature “we are trying to predict project failure”, but in unlablled data they still give use an objective, but there is not specific feature why are trying to predict or classify using.

So in a sense we are trying to find inherent structure of the date, even though it may not entirely exist!

Definition of clustering : group of instances based on similarity and disimilarity.

Regularly, clustering is used for market segmentation, that is given a set of data, form groups on with inherent characteristic (features) so that was can maximise return on advertisement.

# Types of clustering algorithms

There are four main types of clustering approaches:
1. Hierarchical Approach
2. Partitioning Approach
3. Density based approach
4. others - NN, Kernal, Affinity Prop

# Should I perform clustering on cleaned data or do some transformations?

Clustering can be performed directly on cleaned data, but also can be performed AFTER a dimention reduction algorithm is performed, like PCA. Majority of the times this usually leads to better reduced , since reducing dimentionality reduce non-importanly features and vairacne thus present a more accurate manifold/hyper-plane of the data.

# Does Clustering requres a training pahse like supervised learning?

Since we are not trying to predict/classify our goals now is to organise data into groups thus we dont split our datase but rather trying to optimsie division of data with respect to an optimsiation criteria, we choose.

When is clustering performed in a data sciecne pipeline.Permalink

Clustering is usually perofrmed in the exploratory data anlytics stages

Questions to ask when doing Clustering AlgorithmPermalink

Some of the questions we ask priror to starting the clustering algorithm is;

1. How do we represent patterns? Do we represent them as sets of points?
2. How we we decided our measure of similarity? Remember in KNN algorithm we use distance in  norm to measure
3. How many cluster to we have? Again similar to KNN we decides the number of neightbour we choose, how do we know this is right?
4. How do we assess the performance of our clusters? Given we cluster a gorup, then how do we evaluate this?
5. How do we interpret the results?

# Measuring Similarity for Clustering

Similar, to KNN our goals is to put points close to each other in a cluster while far apart points in different cluster, but consequently how would we determine 2 cluster if points are close by. In the examples below one ration method woulc be to cluster data points together (right corner), but how would we seperate the the points seperatly even thought they are as close to each other (middle points).

clustering simialrity

# Hierarchical Algorithms

This methods entails building a “hierarchy” of cluster. Generally, “hierarchy” means to order somethings from highest to lower or from lowest to highest. There are two types of

1. Agglomerative - lowest to highest; start with a bunch of cluster then move to one cluster using a optimization criteria
2. Divisive - highest to lowest; start with 1 cluster then divide into multiple cluster using optimization criteria

# Visualising the problem
Lets use an simple example, say we want given a client comes to use with customer information. The client ask’s ‘find customer segments for us to create a targeted a marketing strategy’. Now we are given only two features ‘Age’ of customer and ‘Annual Spending’. So the first step is to visualise the two groups.

![visualise-cluster](/assets/images/clustering/visualise-problem.png)

As you can see we only have 8 data-points in this case. Now we that maybe the best approach would be to cluster into maybe 4 clusters,

![human-intution-clustering](/assets/images/clustering/human-intuition-clustering-example.png)

How would a computer do this?

# Agglomerative Hierarchical AlgorithmsPermalink

Generally Agglomerative Hierarchical Algorithms are cateogrised in to these cateogries,

![aggol-cateogries](/assets/images/clustering/aggol-cats.png)

Down up approach, so in we start with finding the closest points in to a given to each point and then make each its own cluster, in this case it would be out human intuition,

![human-intution-clustering](/assets/images/clustering/human-intuition-clustering-example.png)

Although in this case this may be the best number of cluster, in reality this may not be the case. Since all points are in a cluster we next try to find minimum distance to each neighbouring cluster. In this case the purple cluster is clostes to the botton on the green cluster is

![closest-pnt-cluster](/assets/images/clustering/best-point-three-cluster-aggol.png)

and then join these clusters, so,

![three-clusters-agglomerative](/assets/images/clustering/three-cluster-algglomerative.png)

Then we calculate each pnts distance inside the blue cluster to each pnt to other clusters. That is for say a given point in the purple cluster,

![distance-one-point-three-clusters-agglomerative](/assets/images/clustering/finding-distances-three-cluster-agglomerative.png)

So this is done another 4 times this case in the purple cluster and then we find the mimum distance between a datapoint in purple to another cluster that is in this case,

![min-dist-point-three-clusters-agglomerative](/assets/images/clustering/best-point-three-cluster-aggol.png)

And so we combine these two clusters,

![two-clusters-agglomerative](/assets/images/clustering/two-clusters-aggol.png)

This continues until we finally have one cluster, that is all points are in the same cluster, which is where we initially started!

![one-clusters-agglomerative](/assets/images/clustering/one-cluster-aggol.png)

# How to effectivley visualise this our different opottions for clusters?

In most cases we dealing with multidimentional features space, so visualising it impossible unless we do some dimension reductionality technique like PCA etc. So the most effective way to visualise thses different potential cluster is through tree-diagrams, althought there are other methods including banner, point representation, etc. There are two main types of tree diagrams used in clustering representation dendrograms and n-tree.

# Dendrograms

![dendogram-aggol-clustering](/assets/images/clustering/dendogram-aggol.png)

So in the for a agglomerative hierarchical algorithms we start at the bottom and compute, even thought we compute the distance between each point and all other points, we only graph the closest point in the dendrograms. In this case, point 3 was clostes to point 8 with distance of 0.07, while for point 4 closest point was point 6.

Importantly, for point 1 the clostes point was point 4 (not shown in graph), so bacuase of this it form 1 big cluster with point 1, 4, 6 rather then point 4 only since point 4 clostes point isn’t 1 but 6.

# n-tree
Below, internal nodes are clusters (A,B,C) whilst the terminal notes/leaves are the data points.

![n-tree-diagram](/assets/images/clustering/n-tree-diagram.png)

Importantly a dendrograms is a type of n-tree, which all internal notes satisify, 
$$
\begin{align*}
h(A) \leq h(C) \Longleftrightarrow A \subseteq C
\end{align*}
$$ 
where h: height on n-tree. And A and C a clusters. Intutivley clearly on our 5-tree diagram h(A) less then h(C) this makes sense we reber back to the n-tree diagram clearly if were were to draw clusters then C takes all points  to , but Cluster A only contains  to  a subset of elements and C. So 

# Divisive Hierarchical Clustering

In this instance we want to do the opposite of of agglomerative clustering where we start we one large cluster an