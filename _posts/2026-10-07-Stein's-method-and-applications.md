---
layout: post
author: Iyad El Khoury
comments: true
---

A standard idea in probability, statistical theory and more generally in analysis is to approximate a function by a sequence of elementary maps in order to work with simpler objects and hopefully pass certain properties via a limit. Stein's method is a technique used in order to find precise bounds on the error obtained when approximating some random variables by simpler distributions such as normal, poisson or exponential distributions just to name a few. In this post I will introduce the method applied to Poisson approximation, which was originally developed by Louis Chen, the PhD student of Charles Stein.

### Probability metrics

Let $$(\Omega,\Sigma)$$ be a measurable space, before attacking our problem of approximations, we need to have a clear concensus of what it means for two distributions to be close to one another. We denote by $$\mathcal{P}$$ the set of all probability measures on $$(\Omega,\Sigma)$$ and by $$\mathcal{H}$$ some set of measurable functions $$\{f:\Omega \to \mathbb{R}\}$$. Then, we can define for $$\mathbb{P},\mathbb{Q}\in \mathcal{P}$$:

$$
d(\mathbb{P},\mathbb{Q}) = \sup_{h\in \mathcal{H}} \left \lvert \int_\Omega h d\mathbb{P} -  \int_\Omega h d\mathbb{Q}\right \rvert
$$

Given that the set $$\mathcal{H}$$ is rich enough, then $$d$$ will define a metric on $$\mathcal{P}$$ and we have a notion of comparison between two probability measures. Some common examples include the total variation metric $$d_{TV}$$ for general measure spaces and Kolmogorov's metric $$d_\mathcal{K}$$ or the Wasserstein metric, $$d_\mathcal{W}$$, for $$\Omega = \mathbb{R}$$ and $$\Sigma = \text{Bor}(\mathbb{R})$$:

$$
d_{TV}(\mathbb{P},\mathbb{Q}) := \sup_{A\in \Sigma} \left \lvert \int_\Omega \mathbb{1}_A d\mathbb{P} -  \int_\Omega \mathbb{1}_A d\mathbb{Q}\right \rvert =  \sup_{A\in \Sigma} \left \lvert \mathbb{P}(A) - \mathbb{Q}(A)\right \rvert
$$

$$
d_\mathcal{K}(\mathbb{P},\mathbb{Q}) := \sup_{t\in \mathbb{R}} \left \lvert \int_\Omega \mathbb{1}_{(-\infty, t)} d\mathbb{P} -  \int_\Omega \mathbb{1}_{(-\infty, t)} d\mathbb{Q}\right \rvert =  \sup_{t\in \mathbb{R}} \left \lvert \mathbb{P}((-\infty,t)) - \mathbb{Q}((-\infty,t))\right \rvert
$$

$$
d_\mathcal{W}(\mathbb{P},\mathbb{Q}) := \sup_{f:\mathbb{R}\to \mathbb{R}, f \text{ 1-Lipshitz}} \left \lvert \int_\Omega f d\mathbb{P} -  \int_\Omega f d\mathbb{Q}\right \rvert 
$$

Given a probability space $$(\Omega,\Sigma, \mathbb{P})$$, two real valued random variables $$X,Y:\Omega \to \mathbb{R}$$ and some metric, $$d$$ on $$\mathcal{P}$$ (the set of probability distributions on $$(\mathbb{R},\text{Bor}(\mathbb{R}))$$), we will slighlty abuse notation and write , $$d(X,Y) := d(\mathbb{P}_X,\mathbb{P}_Y)$$. In the rest of the post this is the notation we shall use to compare the distributions of two real valued random variables. Note that given some sequence of real valued random variables $$\{X_n\}_{n\geq 0}$$, then $$\{X_n\}_n$$ converges in distribution to $$X:\Omega \to \mathbb{R}$$ if and only if $$d_\mathcal{K}(X_n,X) \to 0$$ as $$n\to \infty$$. In particular, as $$d_\mathcal{K}(\cdot,\cdot) \leq d_{TV}(\cdot,\cdot)$$, then $$d_{TV}(X_n,X)\to 0$$ implies convergence in distribution.
### The Stien-Chen Operator
We will now restrict ourselves to applying Stein's method to obtain results on Poisson approximations. Let us fix $$\lambda > 0$$ and $$Z_\lambda \sim \text{Poi}(\lambda)$$. We denote by $$\mathcal{F} := \{f:\mathbb{N}\to \mathbb{R} : \lVert f \rVert_\infty < \infty\}$$ the set of bounded real sequences (which we view as functions on $$\mathbb{N}$$) and $$\mathcal{G}_\lambda := \{f:\mathbb{N}\to \mathbb{R} : f(Z_\lambda) \in \text{L}_1\}$$ the set of functions such that the  random variable induced by $$Z_\lambda$$ is in $$\text{L}_1$$. Both $$\mathcal{F}$$ and $$\mathcal{G}_\lambda$$ are real vector spaces with a canonical norm defined on them; $$\lVert f \rVert_\infty := \sup_{n\geq 0}\lvert f(n)\rvert$$,  $$\lVert f \rVert_{(\lambda)}:= \mathbb{E}[|f(Z_\lambda)|]$$ respectively.


