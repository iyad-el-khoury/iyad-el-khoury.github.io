---
layout: post
author: Iyad El Khoury
comments: true
---

A standard idea in probability, statistical theory and more generally in analysis is to approximate a function by a sequence of elementary maps in order to work with simpler objects and hopefully pass certain properties via a limit. Stein's method is a technique used in order to find precise bounds on the error obtained when approximating some random variables by simpler distributions such as normal, poisson or exponential distributions just to name a few. In this post I will introduce the method applied to Poisson approximation, which was originally developed by Louis Chen, the PhD student of Charles Stein.
### Probability metrics

Let $$(\Omega,\Sigma)$$ be a measurable space, before attacking our problem of approximations, we need to have a clear concensus of what it means for two distributions to be close to one another. We denote by $$\mathcal{P}$$ the set of all probability measures on $$(\Omega,\Sigma)$$ and by $$\mathcal{H}$$ some set of measurable functions $$f:\Omega \to \mathbb{R}$$. Then, we can define for $$\mathbb{P},\mathbb{Q}\in \mathcal{P}$$:

$$
d(\mathbb{P},\mathbb{Q}) = \sup_{h\in \mathcal{H}} \left \lvert \int_\Omega h d\mathbb{P} -  \int_\Omega h d\mathbb{Q}\right \rvert
$$

Given that the set $$\mathcal{H}$$ is rich enough, then $$d$$ will define a metric on $$\mathcal{P}$$ and we have a notion of comparison between to probability measures. Some common include the total variation metric $$d_{TV}$$, Kolmogorov's metric $$d_\mathcal{K}$$ or the Wasserstein metric, $$d_W$$:

$$
d_{TV}(\mathbb{P},\mathbb{Q}) = \sup_{A\in \Sigma} \left \lvert \int_\Omega \mathbb{1}_A d\mathbb{P} -  \int_\Omega \mathbb{1}_A d\mathbb{Q}\right \rvert =  \sup_{A\in \Sigma} \left \lvert \mathbb{P}(A) - \mathbb{Q}(A)\right \rvert
$$

### Stien-Chen operator

