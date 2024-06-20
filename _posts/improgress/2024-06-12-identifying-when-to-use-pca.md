---
layout: single
classes: wide
title: "Dimension Reduction Methods"
header:
categories:
  - Projects
author_profile: True
---
Main Ones to cover : LLE LTSA Isomap MDS Spectral embedding t-SNE 
https://www.youtube.com/watch?v=bqtNjwI60dQ&list=PLPrxGIUWsqP3MNmrqbarg-FbMW88_fzsp&index=6
https://www.youtube.com/watch?v=bqtNjwI60dQ&list=PLPrxGIUWsqP3MNmrqbarg-FbMW88_fzsp&index=6
https://www.youtube.com/watch?v=4Zk2UFGIrd0

Today i was learning about Spectral decomposition and the implciation leading to Spectral Value Decompositon, and as many of you guys know the important role SVD plays to Priciple component anlysis, but then the question arise, I want to use PCA but when should I?
The following notes are from "Introduction to Dimensionality Reduction - Presentation at WangLab in the University of Toronto". What i will try to do is outline the main methodologies used in dimension reductionality.

# What is a Manifold?

When we work with data we have many attributes to describe a certain event we combine all the into  a feature vector $ X = [x_1 | x_2 | x_3| ... | x_n] $ . Suppose we have a table describing people then each column can be age, income, location etc. so $ x_i $ represent columns which we combina into a column vector.

if the only have less then 3 attribute then we can graph these attributes. Majority of the time given there is not major noise in a data, that is error in sample, data naturally stay close to one another, this is known as the Manifold Hypothesis. 

![Manifold-types](/assets/images/manifolds/manifold_types.jpg)

There are two many types of ways data can lay in a low dimensional space, (a) subspace : which is hyperplane  in, subspace are importantly always linear OR  (b) submanifold, which is like a squiskly hyperplane, but importantly, locally linear, that is, if we zoom in very close into the submanifold it would seem we were in a flat plane. 

Additionally, a submanifold is a smooth continous function, as it allows use to use calculus. Before we cover the identify submanifold we need to cover the types of dimentionaliy reductions


# Types of Reduction Dimensionality
Generally Reduct of Dimension can be placed into three categories 

![Type-reduction-methods](/assets/images/manifolds/type_of_dimension_reductionality.jpg)

## Spectral Dimentional Reductionaly
 
There dimension method take a geometric approach, an a Example PCA, which uses the Coaraicne Matrix to computre eigenvalues and eigenvector. Now Since eigenvalues are the length of eigenvectors, then this can be used to identify the varaicne of a singualr feature (age). 
The problem then arrises since PCA uses eigenvalues and vector what happens if the data is in a submanifold?

![Spectral-methods](/assets/images/manifolds/spectral_decomposition.jpg)

clearly from (a) consdier the Green and red dots if we use PCA, the eigenvalue would be small, indicating small variacne, even though that data really sits on a submanifold,thus would lead to a underfitting model. 

So by idenfitying our data is in a submanifold, we we properly reduced the dimenstion by flatting out the submanifold and then reducing the size of the space, which would over underfitting.

## Probabilistic Dimension Reductionaliy

As the name suggest, this take a probalisitc approach to dimention reductionaly, which includes Probabilistic Principal Component Analysis (PPCA), SNE, T-SNE, UMAP and random projection, factor analysis and SDR. 
