---
layout: single
classes: wide
title: "Episode One (IBM x UNSW machine learning project) : Data Preprocessing"
header:
categories:
  - ML
author_profile: True
---

Today was the first day of attending a term-long project with Data Society UNSW, in collaboration with IBM. The lecturer from Dr. Saeed Kasmani, a Senior AI engineer from IBM presented the fundamentals of data science workflow. The main premise is that throughout the term, we will try to optimize a machine learning algorithm with a dataset. During the term, an IBM machine learning engineer will teach us the fundamentals of machine learning, including data preprocessing and learning algorithms. 


# The client and objective

Your client is a multinational real estate developer that builds residential and commercial properties 
around the world. They have a large portfolio of projects that are in development simultaneously. They 
currently have a 25% failure rate for their projects that is significantly higher than the industry 
benchmark of less than 10%. They would like to understand what the key leading indicators for project 
failure are when they are planning their projects. This will allow them to only invest capital into the best 
quality projects. They also want to know ongoing which projects are likely to fail so they can cut their 
losses and cease the projects. Secondly, the real estate developer would like to search local building 
policies to quickly find the relevant answers as they plan their developments. This could include zoning 
policies, environmental policies and development planning policies

# Break down the client objective  

1. Improve picking projects - find the likelihood of project failure
2. Reduced speed to policy search

# Weekly project Overview

![weeklyoverview](/assets/images/ibm/ibm-weekly-break.png)


## Data preprocessing  

Our main objective before making any inference of learning models is to understand the fundamental question 

### Does our data useful 'proxy' for understanding our problem?

This is known as exploratory data analysis, for which is a process done after the data is usable.

## What is usable data?
Making a usable dataset is the process 
1. Data Wrangling - sourcing, loading, and precleaning the 
data so we can see what it really looks like, fixing critical issues 
2. Data profiling and cleaning - understanding the essential characteristics of the data , applying preliminary transformations to  confer context and meaning. Continuing implementing strategies for missing and invalid data (Imputations methods)
3. Data mugging - reshaping data to prepare it for analysis

One important lesson is that this is not a linear cycle, from Data Wrangling to Data mugging to learning models. It a iterative process for which we will continuously revise our data to import our analysis and learning model.

![data-cleaning](/assets/images/ibm/IBM_data_cleaning_fixing.jpg)

# How to go about Data Cleaning and Profiling?

After conducting basic data wrangling, you would proceed to preliminary data cleaning, including reformatting, data type conversion, and dealing with dirty data. Secondly, basic data profiling includes finding data types, data ranges (continuous), and categories. Thirdly, one of the most important parts of this stage is 'assessing data quality'.

When assessing data quality, we look at accuracy, reliability (veracity), currency, and relevance. This covers how many invalid or missing values each feature, row, or the overall dataset has, and what the effect is of throwing out or imputing the data.

Remember, in learning algorithms, we assume each sample (i.e., each row) is part of some unknown distribution. That is to say, even the samples that are missing play a part. Therefore, by removing or imputing samples, we risk changing the distribution of the training set, which can result in large test errors!

# Visualizing Data

After this process is done, we are now ready to explore our data visually. Through this process, we can identify skewness, the mean, and even outliers. Graphs include scatterplots, wireframe plots, surface plots, histograms, box-whisker plots, and heat maps. After all these processes, we finally begin to understand the data and the features of each column.

# Final steps before trying a learning model

Yay, we are on our last step before the big one: ML algorithms! So now all data is cleaned, we have a solid grasp of the data, and we need to select which data helps us the most in categorizing/predicting our label. This involves three steps: feature engineering, feature reduction, and feature selection!

Feature engineering in machine learning involves extracting useful features from the given input data, considering the target to be learned and the machine learning model used. It involves transforming data into forms that better relate to the underlying target to be learned. This includes variable transformations such as square root and Box-Cox transformations, and categorical encoding, like one-hot encoding in sk-learn.

Feature reduction and selection involve reducing the number of variables. This is more commonly done under unsupervised learning using techniques such as PCA, factor analysis, and t-SNE. Amazingly, sk-learn has a whole user guide on feature selection!

And there we have it! Now, we know the basic outline of data preprocessing. Just a little note: finding valuable, straight-to-the-point information on data preprocessing is extremely difficult. Some textbooks cover the basics, while others go too in-depth. There isn't anything that's just enough to perform a basic data science project.