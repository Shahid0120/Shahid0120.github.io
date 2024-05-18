---
layout: single
title: "How sampling distribution is the link between Machine Learning and data science"
header:
categories:
  - Random
author_profile: True
---

# Ever wondered how these two field like with concrete examples?
Data science formull is defined "statistics, scientific computing, scientific methods, processes, algorithms and systems to extract or extrapolate knowledge and insights from potentially noisy, structured, or unstructured data". In a informal sense we are trying to transform raw data into strucutre data for a specific task. Now this take can range from mere simple data analysis to more complex task including classifying data or regression problems. Now, one role of data sciecne is to provide data to machine learning engineers for a spcifci learning problem.  So the next question begins 'what does the macvhien learnign requires from a data scientist to ensrue data is correct?'. We will look at the basics of machine learning algorithsm, including loss functions, assumptions and then devlve into the importance of data quality given by data scientist.

# Little about machine learning
Machine learning is a process where by a machine, usually a program, learns from given data where by we have input, $$ X $$ and output $$ Y $$, known as feature inputs and labels, respectively. Now the goals is to create a program which can adequatly be able to given predict 'label' given a new input. An exmaples can be classify females and males, know a data scientist will go out and take picture of males and females, and then label them both males or female, then this is given to a machine leanring program for which is looks at data and tries to understand distinction bewteen male and females, untill it get very good at it. Then we will given it new picture and then hopefully it will be able to identify correctly geneder of the male or female. 

# Now an important assumptio we make is Machine learning is that all samples take have the same distribtion $$ P $$ and are i.i.d why? 

This creates the link between machien learning and data sciecne. Ifall possible data that we can be given is from the same distribition, since if they it would be impossible to predict or classify random selected people since we a any random input. 

## Example : Gender Shades project 2018

In 2018 gender classification algorithms developed by IBM and Microsoft was studye based on miclassification based upon skin tone, from four cateogires: darker-skinned females, darker-skinned males, lighter-skinned females, and lighter-skinned males. All three algorithms performed the worst on darker-skinned females, with error rates up to 34% higher than for lighter-skinned males. 

A key reaosn might be the samples distribution, now say the task to recognise face, if a data scientist provides face of only light-skinned males then cleary the algorithsm will only be able to identify these indviduals and fall short on other skins tones. So the distribution we wrong for the task since the data that the algorith was trained was different to the actually dsitirbution it was testet on 

# Continying 
Additionaly, these samples must be i.i.d, so we have already adressed the identifcallty distribution, but indepecne is importance is to ensure that these samples done effect one another cause if they do it would be impossible to find the relationship between two samples (x_i, y_i)

# How a Machine algorithm works using out asusmption

So currently I've talked about the assumption that all possible data that an algorithsm will very see is given by data sciecntist so the roels of trhe data sciecne to provides data which will represent all possible data it will be given in the future. 

# How then does a Machine learning engineer optimise this data?
(add picture)
so out goals to minimise the error rates of our algorithm chosen h, we do this through choose a loss function which is appropriate to the task, now importantly iv talked about teh improtance of the algorithm bening able to generalise to any data set and that the data, of course  is assumpted to from the same distribution $$ P $$. Our easier first guess is for out loos function 

l(h;D) 

but the key problem is that this only optimsised out dataset in a sense it memories out data givne but give new sample it would not be able to rpedict it well, so we must create a denfition which generlaise well for all possible data from a asusmed distirbution 
$$
E(l(X,Y))_{(x_i,y_i) ~ P}
$$
That is we want to find the middle weight of all possible samples from data future and past 

# How we we implement this into our machine leanring program?

This is why we split data into test and training set, for the sole reason is that out assumption is all points are (xi,yi) ~ P so we act like our data is a represnetaiotn of the whole population of task we need to learn and for that reason we only touch our test set for final evaluation process. we it would givne use a interpretation of how well 

# Conlusion 
So the reaosn why data sciecne is importacne of machine learning engineers is that since machine leanirng engineeers assume that all data for a learnign as has the same distribution, the data scienctist roles is to ensure that the data they provides represent all possible inputs for that task. 