---
layout: single
classes: wide
title: "Bayesian statistics vs frequentist statistics : Estimating Probability From Data"
header:
categories:
  - ML
author_profile: true
---

Today I was watching Kilian Weinberger lecture on Estimating Probabilities from Data: Maximum Likelihood Estimation" Cornell CS4780 SP17 and now I finally understand the difference between the types of statistics (Also I read "Probabilistic Machine Learning: An Introduction" by Kevin Murphy). The following post will discuss the difference between the two most common schools of statistics, through the lens of machine learning, data estimation using probaiblity; MLE and MAP.

# Recall 

An important part of why machine can learning is that we assume that all samples points taken are from the same distribution, $ (x_i, y_i) \~ P, \forall i \in \mathbb{Z}^{+} $ and are i.i.d. Now using this assumption which is the backbone of all learning algorithms, then there $ \exists P(x,y) $, for which a conditional expectation can also be calculated, $ P(y | x) $, that is, given a feature what the the probability that it lands on this specific label. Alternatively , $ P(x|y) $ must also exist, that is given a label what is the probability that it displays certain features. The study of both conditional probabilities are separated using Bayes Theorem,

$$
\begin{align*}
    P(x | y) &\propto P(y | x)P(x) \quad\quad\text{Discriminative Learning} \\ 
    P(y | x) &\propto P(x | y)P(y) \quad\quad\text{Generative Learning}
\end{align*}
$$

In essence, discriminative learning aims to create explicit boundaries between classes of labels, similar to SVMs, Perceptron, and k-NN. On the other hand, generative learning tries to model the distribution of individual classes, such as Naive Bayes or Gaussian Mixture Models (GMM). Within each of these types of learning, you can have parametric models, where we assume the distribution of \( p(x,y) \) comes from a certain well-known distribution like normal, Bernoulli, exponential, or non-parametric.

# What is a parameter? 
given some distribution a parameter is a point estimate that characteristics a known class of distribution. I'm sure you have heard of common well know distribution including $N(\mu, \sigma^2)$ or $ \mathrm{Bern}(\lambda)$. In this case $\theta$, our parameter can be a set, or singular point estimate which character our distribution so $\theta = (\sigma^2, \mu)$ or $\theta = (\lambda) $

# Motivating example  

For a motivating exmaples consdier flipped a equally wieghted coin. Say we coin and we get $$ D = \{ T , T, T, H, H, H, H, T, T, T, T \} $$. Now considering it is eually wieghted coin we would hope that our probbilities of getting each side of the dice as $$ \frac{1}{2}$$ something from pervious years we have come to know. Say we want to know what is the probaiblites of getting a head, then the most intuitive method would be to 

$$
\begin{equation*}
    P(\text{getting heads}) = \frac{n_h}{n_t + n_h}
\end{equation*}
$$

where $ \text{n} = \text{Number of times gotten a side}$ . Yet it used this equation for our set of outcomes $ D $, we find $ P(\text{heads}) = \frac{4}{11} $, which isn't 50 \% as we expected. Why is that did we not find the right probability?

# Frequentist vs Bayesian n Perspective 

When studying probability theory, we are concerned with $ p(D | \theta) $, which models the distribution with some known $ \theta $. On the other hand, in statistics, previously known as inverse probability theory, we are given some data, and we aim to infer the unknown parameters $ \theta $ given observations, $ p(\theta | D) $. 

Generally, Frequentist are concerned with 'frequency', meaning that over time, the asymptotic behavior of our probability will converge to a certain number, as in the example above. Importantly, this requires a lot of data; otherwise, we would be overfitting. On the other hand, Bayesian statisticians know that data is readily available, and indeed, we have some assumptions we know about the data. Thus, they assume some 'prior' distribution of $p(\theta)$ from expertise, enabling them to readily use it when a small sample size is available.

# Frequentist: MLE

So, we define 

$$
\begin{align*}
p(\mathcal{D}|\theta) = \prod_{n=1}^N p(y_n|x_n, \theta)
\end{align*}
$$

that is our i.i.d assumption of machine learning. Then applying a log (we use to simply computation), we get the log-likelihood,

$$
\begin{align*}
\mathcal{L}(\theta) = \sum_{n=1}^N log( p(y_n|x_n, \theta)).
\end{align*}
$$

So, then we define MLE of a parameter 

$$
 \hat{\theta}_{MLE} = \arg\max_{\theta} \sum_{n=1}^N \log p(y_n | x_n, \theta)
$$

So optimisations theory is easier, to optimise a function through minimize cost functions so,

$$
    \theta_{\text{MLE}}^{\hat{}} = \arg\max_{\theta} - \sum_{n=1}^N \log p(y_n | x_n, \theta)
$$

# MLE example
Going back to our examples we flips coins, we now can assume that $p(x,y) ~ Bern(\lambda) $, where now $\theta = P(Y = 1) $, where $Y = number of times of getting heads heads$ 

So,

$$
\begin{align*}
    \mathcal{L}(\theta) = \arg\max_{\theta} - \left( \sum_{n=1}^N \mathbb{1}_{y_n=1} \log(\theta) + \mathbb{1}_{y_n=0} \log(1 - \theta) \right).
\end{align*}
$$

Let, $ N1 = \sum_{n=1}^N \mathbb{1}_{y_n=1}$ and $ N0 =  sum_{n=1}^N \mathbb{1}_{y_n=0} $. Now, we can use differentiating and let the loss function equal 0 to find the minimum (like in high school finding the minimum point of a function) to find $\hat{\theta}_{MLE}$,

$$
\begin{align*}
    \hat{\theta}_{MLE}= \frac{N1}{N0 + N1}
\end{align*}
$$

Isn't this similar to our intuition right? This is known as classical statistics, or Frequentist statistics. Importantly we done assume  $\theta$ has any distribution itself but rather is a parameter which contains information about the distribution of a data points. 

# What is we didnt get any heads in out sample?
he $ \hat{\theta}_{MLE} = 0 $. Is this correct? Well, of course not. We know from our intuition it should be $ \frac{1}{2} $. So Frequentists use this method, knowing we (plus one) Laplace Smoothing to ensure in the case of our sample not having an event occurring,

$$
\begin{equation*}
\hat{\theta}_{MLE}= \frac{N1 + 1 }{N0 + N1 + 2}
\end{equation*}
$$

Since there is only two classes in our examples head or tails so we add 2 in the denominator.

# MAP
Alternatively in Bayesian statistics we don't consider Laplace smoothing or $\theta$ as just a parameter but rather in build upon the notion that we don't have allot of data and data can't always model the distribution of the sample accurately. So we make this assumption (adding bias) that $ \theta $ random variable. Now a random variable is neither a variables or random but rather a function which maps points of a measurable set $ \sigma$-algebra to the real number line, but a important property is that random variables can have distributions. So, now we can express to new equations, using Bayes Theorem,

$$
\begin{align*}
P(\theta | D) &= \frac{P(D | \theta) P(\theta)}{ P(D)} \Rightarrow \\ 
P(\theta | D) &\quad\propto\quad P(D | \theta) P(\theta). \\ 
\end{align*}
$$

Now in Bayesian Statistics, each component is named,  
- $ P(D | \theta) $ Likelihood of data given \( \theta \) 
- $ P(\theta | D)$ (posterior distribution): Distribution over the parameter(s) \( \theta \) after we have observed the data 
- $P(\theta) $ (prior): Distribution over the parameter(s) \( \theta \) before we see any data. 
We need to choose the prior distribution using our expertise and knowledge which of course can work out great, or horribly wrong if we assume the distribution of our prior wrong. So now,

$$
\begin{align*}
     p(\mathcal{D}|\theta) &= \prod_{n=1}^N p(y_n|x_n, \theta)p(\theta) \\
\end{align*}
$$

Applying log, 

$$
\begin{align*}
    \mathcal{L}(\theta)&= \sum_{n=1}^N log(p(y_n|x_n, \theta))+ \sum_{n=1}^N log( p(\theta)) \\
\end{align*}
$$

So,

$$
\begin{align*}
    \hat{\theta}_{map} = \arg\max_{\theta} \mathcal{L}(\theta)
\end{align*}
$$

Going back to the coin flip we can assume our prior distribution (guess) is $  p(\theta) = Beta(\theta|a, b) $ then our log likelihood ends up becoming 

$$
\begin{align*}
    \mathcal{L}(\theta) = &\left( \sum_{n=1}^N \mathbb{1}_{y_n=1} \log(\theta) + \mathbb{1}_{y_n=0} \log(1 - \theta) \right) + [(a - 1)log(\theta) + (b - 1)log(1 - \theta)]
\end{align*}
$$

Then using normal minimisation method of finding first derivative letting it equal to zero to find minimizer for $\hat{\theta})$ we get 

$$
\begin{align*}
    \hat{\theta}_{map} = \frac{N1 + a - 1}{N1 + N0 + a + b - 2}
\end{align*}
$$

So by assuming a prior distribution in Bayesian statistics we end up getting a very similar estimator found in Frequentist statistics using Laplace Smoothing. So in a sense they are very similar! 