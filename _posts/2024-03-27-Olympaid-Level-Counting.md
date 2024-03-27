---
layout: single
title: "Olympiad Level Counting Made Easy with Jensen's inequality"
header:
categories:
  - Statistics
author_profile: True
---

Have you every wondered how high school students with no formal higher level of mathematical knowledge are able to solve complex questions like this? Prove that

$$
    \frac{1}{x-1}+ \frac{1}{x} + \frac{1}{x+1} \geq \frac{3}{x},\quad x > 1.
$$

Or

$$
    (1 + \frac{1}{x})(1 + \frac{1}{y})(1 + \frac{1}{z}) \geq 64.
$$

Many of you have no idea how some 14 year old kid is able to solve these questions, yet at my final year of university, I am still not able to intuitively solve these. I believe that this is true for most university students.

Now, of course, the most rational method would be trying to move all the variables to one side, then try estimating the values for which the right-hand side equals the left-hand side. Then, the exam hits you with give me exact values for $$x,y,z$$ and now you are stumped with this 1 hour exam and  you'll just about spend most of your time guessing possible values. Here comes the bang, Olympiad contestants in my eyes now are of course genius, but they know a set of specialised tools in their tool bag of which they select the appropriate tool for the job. Now, selecting a the right tool can be difficult (Mathematics tool bags a very,very deep). 

## One of the most powerful tools in the mathematics tool bag : Jensen's Inequality.
For any convex function $$h$$, we have,

$$
    \mathbb{E}h(Y) \geq h(\mathbb{E}Y)
$$

How did we get to conclusion of the great 'power' of Jensen's Inequality? According to my professor, Dr.Zdravko Botev, power comes from two key characteristics (1) simplicity (2) usefulness. Not only is Jensen Inequality applicable in a range of context, including counting as above, but also real analysis, probability, economics, statistics, and machine learning, but it's proof that it is so simple.

$$\textit{Proof.}$$ From the definition of convexity, we have for x and all Y:

$$
    h(Y) \geq h(x) + v^T(Y-x)
$$

By the monotonicty and linearity of expectation, we have

$$
    \mathbb{E}h(Y) \geq h(x) + v^T\mathbb{E}(Y-x)
$$

Now, since this is true for each $$x$$ we can chose $$x = \mathbb{E}(Y)$$. So,

$$
    \mathbb{E}h(Y) \geq h(\mathbb{E}Y) + v^T\mathbb{E}(Y-\mathbb{E}Y) \Rightarrow  \mathbb{E}h(Y) \geq h(\mathbb{E}Y).
$$

Which is Jensen's Inequality. 

## Now, how do we apply this powerful tool to our counting problem?
The idea is that we want to find a convex function which applies to the problem and hence we can use Jensen's Inequality. So, for:

$$
    \frac{1}{x-1}+ \frac{1}{x} + \frac{1}{x+1} \geq \frac{3}{x},\quad x > 1.
$$

We can try $$h(x) = \frac{1}{x}$$ or $$ h(x) = \frac{1}{x + 1}$$ or $$h(x) = \frac{1}{x - 1}$$ and we can confirm that these a convex function by showing  $$h"(x) > 0, \forall x \in \mathbb{R}$$. Now, lets try  $$h(x) = \frac{1}{x}, x > 1$$.
Now, for a random variables $$Y$$ we apply Jensen's Inequality, 

$$
    \mathbb{E}[\frac{1}{Y}] \geq \frac{1}{\mathbb{E}Y}
$$

Next we consider a distribution for $$ Y $$. Since, we have 3 fractions a logical choice would be for $$Y$$ distribution, 

$$
    \mathbb{P}(Y = x) = \mathbb{P}(Y = x + 1) = \mathbb{P}(Y = x - 1) = \frac{1}{3}.
$$

For this $$Y$$, we have a three point distribution, we can compute the expectations and hence Jensen's inequality,

$$
\begin{align*}
    \mathbb{E}[\frac{1}{Y}] = \frac{1}{3} \times \frac{1}{x} + \frac{1}{3} \times \frac{1}{x - 1} + \frac{1}{3} \times \frac{1}{x + 1}, \\
    \frac{1}{\mathbb{E}Y} = \frac{1}{\frac{1}{3} \times \frac{1}{x} + \frac{1}{3} \times \frac{1}{x - 1} + \frac{1}{3} \times \frac{1}{x + 1}} = \frac{1}{x}.
\end{align*}
$$

So, 
    
$$
\begin{align*}
    \mathbb{E}[\frac{1}{Y}] &\geq \frac{1}{\mathbb{E}Y} \Rightarrow \\
    \frac{1}{3}[\frac{1}{x-1} + \frac{1}{x} + \frac{1}{x+1}] &\geq \frac{1}{x} \Rightarrow \\
    \frac{1}{x-1} + \frac{1}{x} + \frac{1}{x+1} &\geq \frac{3}{x}.
\end{align*}
$$


Wala! Wasn't that hard, right? Maybe you can try this one,

$$
    (1 + \frac{1}{x})(1 + \frac{1}{y})(1 + \frac{1}{z}) \geq 64.
$$

hint: $$h(x) = \text{ln}(1 + \frac{1}{x})$$
