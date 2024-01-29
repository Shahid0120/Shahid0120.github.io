---
layout: single
title: "Functional vs Sequetial API for Keras in less then 3 minutes"
header:
categories:
  - Machine Learning
author_profile: false
---

Reading to Keras/Tensorflow documentation, it's a little hard to understand what exactly is the difference between sequential and functional API and all other resources are too long to read, so lets simplify it!

Lets talk visually:

![function_sequential_api.png](/assets/images/function_sequential_api/function_sequential_api.png)

The whole point of Tensorflow with Keras is to simply the process of creating neural networks so now we dont spend time on manully coding a neural network, but rather focus on improving the performance of our model. Now how exactly does Functional api improve flexibility but at the cost of complexity?

## Sequential API 
Sequential API's tipically look like this:

![sequential.png](/assets/images/function_sequential_api/sequential.png)

Notice, although we specify the pooling dimensions and strides and other arguements within the tf.keras.layers call , we can't input specific paramters like Z1,A1 or Z2. Importantly it all happens sequentially so the model will start from the top end go by each call one by one until the end.

# Function API : spot the difference
Alternatively, comparing this to functional API it allows use to play around with the parameters:

![functional_api.png](/assets/images/function_sequential_api/sequential.png)

Notice how we adding paramters to our calls to tf.keras.layers()(Paramter) providing us flexibility to choose which parameters we want to trasnform. Note this is just one way of taking advantage of function API. Other possible options are :
1. Multiple inputs - Now we can have multiple paramters since our functional isnt called linearly 
2. Sharing inputs - say we want Z1 to have multiple acitivations say Leaky-RelU and ReLU 

But as you can see the possibility or errors increases since you can play around with which inputs you want where. So be careful!

# Conclusion 

Hopefully now you understand the difference between Sequential and Functional API!
