---
layout: single
title: "Statistical Learning Theory Episode One 'Building the foundation' "
header:
categories:
  - Statistics
author_profile: True
---
# Overview
 I'v been currently learning about staticial learning theory to gain a mathematical udnertsanding of machine learning. So today the first part of a few psot focusing in undertsanding statistical learning theory. This first post is based on 'Complete Statistical Theory of Learning (Vladimir Vapnik) | MIT Deep Learning Series'. Lets get into it!

# Why do we care about statistical learning theory? 

Statistical learnign theory predates today machie learing algorithsm. Originating from Russia in the 1960's, the key goals was to formualting 'learning' through data. Machine learing algorithm take example training data then it infers 'general ruels' which can both answer a its label and over time after many samples can generalised to unseen examples known as inductive reasoning/inferences. 

This domain of study lead to the now famous algorithsm known as Support Vector Machines which is now a staple of patter recognition.To enable this learning process statistician devleoped a framework to formuale this process; regression, classification, clustering. 

# Framework of staitsitcal learning theory 

General SLT attems to answer 4 main questions; 

1. Which learning tasks can be performed by computers in general (positive and negative results)?
2. What kind of assumptions do we have to make such that machine learning can be successful a.k.a inductive bias? (Turns out this is inevitable for a sucessfull learning algorithsm "No Free-Lunch Theorem"!)
3. What are the key properties a learning algorithm needs to satisfy in order to be successful?
4. Which performance guarantees can we give on the results of certain learning algorithms? - this ones important we want to ensure our mechanism learns the right outcome 

# Types of learning 

We will be focusing on explanation through the leaner-teacher model, in which the learning is the algorithm, the environment is the training data and the teacher guides the experience
1. Supervised vs unsupervised learning : the learner interects with the environment in suprervised learning the leaners "uses experiences from environment to gain expertise" in which a teacher provides the experiecnes (training data) and then "apply" its experiecnes to new data given by the teacher (test data). However, in unserpvised learning the teacher provides 'experiences' to the learner (training data), and the leaner aims to 'summerise' the experiences
2. Active vs Passive : If the learner interects with the enviuronement provided by the teacher (training data) and gives the teacher quiries about the experiecnes then is is an acitvie leaner, else if it doesnt inquire about the experiences and merlery just take the experiecnes in then its is passive 

The goals is the teacher naturlally is to provide the best informatio for the leaner to understand the taks as quickly as possible, but course how the teacher learner the task itself is unknown so we assume it is random process. An alternative is adversiary teacher, who pruposefuly provides bad information to see if the leaner undertsanding the experinces, usualyl used in worst-case scienario's!

# Formulising the learning equation 
