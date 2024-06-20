---
layout: single
title: "Intuition about Dscriminative vs Generative Learning for Machine Learning"
header:
categories:
  - Databases
author_profile: True
---

Generative and Discriminative Classifiers: The most important difference be- tween naive Bayes and logistic regression is that logistic regression is a discrimina- tive classifier while naive Bayes is a generative classifier.
These are two very different frameworks for how
to build a machine learning model. Consider a visual
metaphor: imagine we’re trying to distinguish dog
images from cat images. A generative model would
have the goal of understanding what dogs look like
and what cats look like. You might literally ask such
a model to ‘generate’, i.e., draw, a dog. Given a test
image, the system then asks whether it’s the cat model or the dog model that better fits (is less surprised by) the image, and chooses that as its label.
A discriminative model, by contrast, is only try- ing to learn to distinguish the classes (perhaps with- out learning much about them). So maybe all the dogs in the training data are wearing collars and the cats aren’t. If that one feature neatly separates the classes, the model is satisfied. If you ask such a model what it knows about cats all it can say is that they don’t wear collars.


