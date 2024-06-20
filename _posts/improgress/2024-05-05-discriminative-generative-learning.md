---
layout: single
title: " Discriminative vs Generative Learning intuition for Machine Learning"
header:
categories:
  - ML
author_profile: True
---

Today i was reading "Probabilistic Machine Learning: An Introduction" by Kevin P. Murphy and i read this very interesting intuition. So generally there are two types of i guess probabilistic supervising learning model. One form is 
$$ 
P(y|x) 
$$ 
thats is given some features (x's) i want to classify some label, our y, this is known as discriminative learning models. These models includes algorithm such as Logistic regression (for classification) and linear models (for regression).

# Breif Introduction 

An alternatvie approach say hey we can use Bayes Theorem on 
$$ 
P(y|x) 
$$ 
so,

$$
\begin{align*}
  P(y|x) = \frac{P(y | x)P(x)}{P(y)}
\end{align*}
$$

So since $ P(y) $ it not effect by our features (x's) we don't care about is so,

$$
\begin{align*}
  P(y|x) \propto P(x | y)P(x)
\end{align*}
$$

Now, depending on the school of thought—Bayesian or frequentist— 
$$ 
P(x) 
$$ 
can be thought of as having its own distribution or not, respectively. But the important thing is that we now have another method of classifying/predicting new data using 
$$
P(x∣y) 
$$
, which is quite interesting. This is known as generative learning and includes algorithms such as naive Bayes and LDA.

# Intutively whats the difference?

Let's say we want to classify the difference between cats and dogs. A discriminative model, 
$$ 
P(y | x) 
$$
, takes features of cats versus dogs and uses these features to predict a label. Intuitively, it's trying to understand the difference between a cat and a dog. For example, cats might have pointy ears, while dogs have droopy ears.

On the other hand, generative models, denoted as 
$$ 
P(x | y) 
$$, focus on understanding the features of each category separately. Given all the cats, a generative model tries to understand cat features: how they look, what color they are, and other characteristics. Rather than comparing both pictures directly, the model generalizes the identification of cats.

However, if the model only tries to understand each animal on its own, it might not effectively distinguish between cats and dogs, unlike the discriminative model which explicitly learns the differences between the two categories, but then lacks the ability to understand maybe different species of cats.





