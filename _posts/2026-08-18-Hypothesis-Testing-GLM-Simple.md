---
layout: single
classes: wide
title: "Hypothesis Testing in GLMs: Testing a Single Parameter"
categories:
  - Statistics
author_profile: true
---

# Hypothesis Testing in GLMs

## Likelihood-Based Testing

In a simple Generalised Linear Model (GLM) with one parameter, there are three common methods for testing our parameter using the likelihood function.

Suppose we want to test:

$$
H_0: \theta = \theta_0
$$

The three likelihood-based methods are:

- Wald Test
- Score Test
- Likelihood Ratio Test

In this post, we will focus on the **Wald Test** and **Score Test**.

## Simple GLM Model - With One Parameter

### Wald Test

The **Wald Test** is based on the distance between our estimated parameter $\hat{\theta}$ and the hypothesised value $\theta_0$.

The Wald statistic is defined as:

$$
W =
\frac{(\hat{\theta} - \theta_0)^2}
{\widehat{\operatorname{Var}}(\hat{\theta})}
$$

When $H_0$ is true,

$$
W \sim \chi^2_1
\qquad \text{as } n \rightarrow \infty.
$$

Notice that:

- $\sqrt{W} = Z$, thus $Z \sim \mathcal{N}(0,1)$, so $Z$ can be used as the test statistic.
- A small $W$ means that the distance between $\hat{\theta}$ and $\theta_0$ is small relative to the uncertainty in $\hat{\theta}$. Therefore, we have less evidence against $H_0$ for a given significance level $\alpha$.
- A large $W$ means that $\hat{\theta}$ is far from $\theta_0$ relative to its uncertainty, providing stronger evidence against $H_0$.

Generally, in a simple GLM we may be interested in testing a coefficient using:

$$
H_0: \beta_1 = 0
$$

against an alternative such as:

$$
H_a: \beta_1 > 0.
$$

### Proof

We know that the second-order Taylor series expansion around $x=a$ is:

$$
f(x)
\approx
f(a)
+
f'(a)(x-a)
+
\frac{1}{2}f''(a)(x-a)^2.
$$

Taking the second-order Taylor series expansion of the log-likelihood around $\theta=\hat{\theta}$, where $\hat{\theta}=\hat{\theta}_{MLE}$, we obtain:

$$
\ell(\theta;\mathbf{y})
\approx
\ell(\hat{\theta};\mathbf{y})
+
\ell'(\hat{\theta})(\theta-\hat{\theta})
+
\frac{1}{2}\ell''(\hat{\theta})(\theta-\hat{\theta})^2.
$$

Since $\hat{\theta}$ is the maximum likelihood estimate,

$$
\ell'(\hat{\theta})=0.
$$

Therefore,

$$
\ell(\theta;\mathbf{y})
\approx
\ell(\hat{\theta};\mathbf{y})
+
\frac{1}{2}\ell''(\hat{\theta})(\theta-\hat{\theta})^2.
$$

Let $\theta=\theta_0$. We obtain:

$$
2\left(
\ell(\theta_0;\mathbf{y})
-
\ell(\hat{\theta};\mathbf{y})
\right)
\approx
\ell''(\hat{\theta})
\left(\theta_0-\hat{\theta}\right)^2.
$$

Recall that the observed information is:

$$
J(\theta)=-\ell''(\theta).
$$

Therefore,

$$
2\left(
\ell(\hat{\theta};\mathbf{y})
-
\ell(\theta_0;\mathbf{y})
\right)
\approx
J(\hat{\theta})
\left(\hat{\theta}-\theta_0\right)^2.
$$

Since

$$
\widehat{\operatorname{Var}}(\hat{\theta})
\approx
\frac{1}{J(\hat{\theta})},
$$

we obtain:

$$
2\left(
\ell(\hat{\theta};\mathbf{y})
-
\ell(\theta_0;\mathbf{y})
\right)
\approx
\frac{
\left(\hat{\theta}-\theta_0\right)^2
}{
\widehat{\operatorname{Var}}(\hat{\theta})
}.
$$

The expression on the right-hand side is precisely the Wald statistic:

$$
W =
\frac{
\left(\hat{\theta}-\theta_0\right)^2
}{
\widehat{\operatorname{Var}}(\hat{\theta})
}.
$$

This demonstrates the relationship between the Wald statistic and the local curvature of the log-likelihood around the maximum likelihood estimate.

## Score Test

The **Score Test** works by normalising the score function and examining its value at $\theta_0$.

Recall that the score function is:

$$
U(\theta)
=
\frac{\partial \ell(\theta;\mathbf{y})}{\partial\theta}.
$$

When calculating our parameter estimates, we find the maximum likelihood estimate $\hat{\theta}$ by solving:

$$
U(\hat{\theta})=0.
$$

The Score Test uses this idea but asks a slightly different question: **what is the slope of the log-likelihood at the hypothesised value $\theta_0$?**

If

$$
U(\theta_0)\approx0,
$$

then $\theta_0$ is likely to be near $\hat{\theta}$, meaning that we have less evidence against $H_0$.

If $U(\theta_0)$ is far from zero, then the likelihood is still increasing or decreasing substantially at $\theta_0$, suggesting that $\theta_0$ is not close to the maximum likelihood estimate.

The Score statistic is:

$$
S =
\frac{U(\theta_0)^2}
{I(\theta_0)},
$$

where $I(\theta_0)$ is the Fisher information evaluated at $\theta_0$.

When $H_0$ is true,

$$
S \sim \chi^2_1
\qquad \text{as } n\rightarrow\infty.
$$

Notice that:

- $\sqrt{S}=Z$, thus $Z\sim\mathcal{N}(0,1)$.
- The Score Test only requires quantities evaluated at $\theta_0$.
- Unlike the Wald Test, we do not necessarily need to know the unrestricted estimate $\hat{\theta}$.
- If $U(\theta_0)$ is close to zero, then the slope of the log-likelihood at $\theta_0$ is close to zero, providing less evidence against $H_0$.

### Proof

Take a first-order Taylor expansion of the score function around $\theta=\theta_0$:

$$
U(\theta)
\approx
U(\theta_0)
+
U'(\theta_0)(\theta-\theta_0).
$$

Evaluate this when $\theta=\hat{\theta}$:

$$
U(\hat{\theta})
\approx
U(\theta_0)
+
U'(\theta_0)(\hat{\theta}-\theta_0).
$$

Since $\hat{\theta}$ is the maximum likelihood estimate,

$$
U(\hat{\theta})=0.
$$

Therefore,

$$
0
\approx
U(\theta_0)
+
U'(\theta_0)(\hat{\theta}-\theta_0).
$$

Recall that:

$$
U'(\theta)
=
\ell''(\theta)
=
-J(\theta).
$$

Therefore,

$$
U(\theta_0)
\approx
J(\theta_0)(\hat{\theta}-\theta_0).
$$

For sufficiently large samples, the observed information and Fisher information are approximately equivalent:

$$
J_n(\theta_0)
\approx
I_n(\theta_0).
$$

We also know that:

$$
\operatorname{Var}(\hat{\theta})
\approx
\frac{1}{I_n(\theta_0)}.
$$

Since $\theta_0$ is a constant,

$$
\operatorname{Var}(\hat{\theta}-\theta_0)
=
\operatorname{Var}(\hat{\theta}).
$$

Using

$$
U_n(\theta_0)
\approx
I_n(\theta_0)(\hat{\theta}-\theta_0),
$$

we can take the variance of both sides:

$$
\begin{aligned}
\operatorname{Var}\left[U_n(\theta_0)\right]
&\approx
I_n(\theta_0)^2
\operatorname{Var}(\hat{\theta}-\theta_0)
\\
&=
I_n(\theta_0)^2
\operatorname{Var}(\hat{\theta})
\\
&\approx
I_n(\theta_0)^2
\frac{1}{I_n(\theta_0)}
\\
&=
I_n(\theta_0).
\end{aligned}
$$

Therefore,

$$
\operatorname{Var}\left[U_n(\theta_0)\right]
\approx
I_n(\theta_0).
$$

Under $H_0$, we also have:

$$
\mathbb{E}[U_n(\theta_0)]=0.
$$

We can therefore standardise the score function:

$$
Z_S
=
\frac{
U_n(\theta_0)
}{
\sqrt{I_n(\theta_0)}
}
\overset{H_0}{\approx}
\mathcal{N}(0,1).
$$

Squaring the standardised statistic gives:

$$
S
=
Z_S^2
=
\frac{
U_n(\theta_0)^2
}{
I_n(\theta_0)
}
\overset{H_0}{\approx}
\chi^2_1.
$$

## Wald Test vs Score Test

The Wald Test and Score Test approach the same hypothesis from two different perspectives.

The **Wald Test** examines the distance:

$$
\hat{\theta}-\theta_0.
$$

It asks: *How far is our estimated parameter from the value specified under the null hypothesis?*

The **Score Test** examines:

$$
U(\theta_0).
$$

It asks: *How steep is the log-likelihood at the value specified under the null hypothesis?*

Therefore, the Wald Test focuses on the **distance between $\hat{\theta}$ and $\theta_0$**, while the Score Test focuses on the **slope of the likelihood at $\theta_0$**.

Under standard regularity conditions and as the sample size becomes large, both tests are asymptotically related and should generally lead to similar conclusions.

# Conclusion

For a simple GLM with a single parameter, likelihood-based hypothesis testing provides several ways of determining whether the data provide evidence against:

$$
H_0:\theta=\theta_0.
$$

In this post, we explored two of these methods.

The **Wald Test** measures how far $\hat{\theta}$ is from $\theta_0$ relative to the uncertainty associated with $\hat{\theta}$.

The **Score Test**, on the other hand, evaluates the slope of the log-likelihood at $\theta_0$. If the slope is close to zero, then $\theta_0$ may be close to the maximum likelihood estimate.

Both approaches ultimately produce test statistics that asymptotically follow a $\chi^2_1$ distribution under $H_0$.

The third likelihood-based approach is the **Likelihood Ratio Test**, which compares the likelihood under the null hypothesis with the maximised likelihood. This will complete the three main approaches to likelihood-based hypothesis testing.