---
layout: post
author: Iyad El Khoury
comments: true
---

Let $$(V, \lVert \cdot \rVert)$$ be a normed real vector space and $$v_1, v_2, \dots, v_n \in V$$ a family of $$n$$ unit vectors in $$V$$. A famous problem in geometry is to ask how small can the vector $$\varepsilon_1 v_1 + \dots + \varepsilon_n v_n$$ be made, where $$\varepsilon_i \in \{-1,1\}$$ is a choice of sign for each vector $$v_i$$? Our task is thus to find some upperbound, $$f(n)$$, such that for an arbitrary family of $$n$$ unit vectors, there exists some choice of signs, $$\{\varepsilon_i\}_{i} \in \{-1,1\}^n$$, satisfying $$\lVert\varepsilon_1 v_1 + \dots + \varepsilon_n v_n\rVert \leq f(n)$$. I will call any theorem of this kind a *small sum* theorem.

As the space of signs, $$\{-1,1\}^n$$, is exponential in $$n$$ and the vectors $$\{v_i\}_i$$ are arbitrary, it seems quite reasonable that the correct approach to this problem would be to borrow the probabilistic method in combinatorics. Let us begin with the case where $$V = \mathbb{R}^d$$ and $$\lVert \cdot \rVert$$ is a Euclidean norm.

### The Euclidean case
Let $$(\mathbb{R}^d,\langle \cdot \mid \cdot \rangle)$$ be a Euclidean space, denote by $$\lVert \cdot \rVert $$ the norm induced by the scalar product $$\langle \cdot \mid \cdot \rangle$$ and  $$v_1, v_2, \dots, v_n \in \mathbb{R}^d$$ be unit vectors. We will consider a random choice of signs $$\{\varepsilon_i\}_{i} \in \{-1,1\}^n$$, or more precisely, let $$\varepsilon_i \sim \text{Unif}(\{-1,1\})$$ be i.i.d Rademacher random varaibles. We are therefore interested in understanding the Euclidean norm of the random variable $$Z = \varepsilon_1 v_1 + \dots + \varepsilon_n v_n$$. To exploit the bilinearity of the Euclidean scalar product, it will be simpler to consider the norm squared of $$Z$$, that is to say the quantity $$\langle Z \mid Z\rangle$$. Calculating the expected value of $$\lVert Z \rVert^2$$ is direct:

$$
\mathbb{E}\big[\langle Z \mid Z \rangle\big] = \sum_{i=1}^n \sum_{j=1}^n \mathbb{E}[\varepsilon_i \varepsilon_j] \langle v_i \mid v_j \rangle = \sum_{i=1}^n \lVert v_i \rVert ^2= n
$$

By the first moment method, we thus now there exists a choice of sign $$\{\bar \varepsilon _i\}_i \in \{-1,1\}^n$$ such that $$\lVert \bar \varepsilon_1 v_1 + \dots + \bar \varepsilon_n v_n  \rVert^2 \leq n$$. This immedieatly gives us a first result:

<div class="theorem" markdown="1">
<span class="theorem-title"></span>
For any Euclidean norm, $$\lVert \cdot \rVert$$ on $$\mathbb{R}^d$$ and unit vecotrs $$v_1,\dots,v_n\in \mathbb{R}^d$$, there exists $$\{\varepsilon_i\}_i \in \{-1,1\}^n$$ such that:

$$ 
\left\lVert \varepsilon_1 v_1 + \dots + \varepsilon_n v_n \right\rVert \leq \sqrt{n} 
$$

</div>

We may also notice that this result is tight, for example, by considering the standard Euclidean norm and the canonical unit vectors $$e_1,\dots,e_n \in \mathbb{R}^d$$, the vector $$Z = \sum _i \varepsilon _i e_i $$ is a vertex of the hypercube $$\Sigma := [-1,1]^n$$ for any choice of $$\{\varepsilon _i \}_i \in \{-1,1\}^n$$. Therefore, in this case there is no choice of signs which obtains a norm of $$Z$$ smaller than $$\sqrt{n}$$.

### The infinity norm case
Let us denote by $$\lVert \cdot \rVert _\infty$$ the infinity norm of $$\mathbb{R}^d$$ defined by $$\lVert (x_1, \dots, x_d) \rVert _\infty = \max _i \vert x_i\vert$$. We recall that this is not a Euclidean norm, for example, the parallelogram law does not hold for $$\lVert \cdot \rVert _\infty$$. To establish a *small sum* theorem for the infinity norm, it suffices to find $$\{\varepsilon _i \}_i \in \{-1,1\}^n$$ such that all coordinates of $$Z$$ are smaller than some $$f(n)$$. Once again, our strategy is to use a probabilistic argument, and in this case, to find a function $$f$$ such that $$\mathbb{P}[\lVert Z \rVert _\infty > f(n)] < 1$$. By the symmetry between coordinates and the definition of the infinity norm, it will suffice to treat the one dimensional case and show that $$\mathbb{P}[\vert Z \vert> f(n)] < 1/d$$, since the previous inequality will follow from a union bound.

Let $$v_1,\dots,v_n \in [-1,1]$$ be real numbers of absolute value at most 1 and $$\varepsilon_i \sim \text{Unif}(\{-1,1\})$$ be i.i.d Rademacher random varaibles as before. By our previous discussion we are interested in establishing a concentration inequalty for the random variable $$Z = \sum _i \varepsilon _i v_i$$, which will translate directly into a *small sum* theorem. For this we will make use of the exponential moment method, which I will quickly review before applying it to our problem. 

#### The exponential moment method
Let $$Z$$ be some real valued random variable, then the function $$t\mapsto \mathbb{E}[\exp(tZ)]$$ is called the moment generating function of $$Z$$ and may be expanded as a power series given by the following formula $$M_Z(t) = \sum _{n\geq 0} \mathbb{E}[Z^n] \frac{t^n}{n!}$$. 

Given we have control on the moment generating function of $$Z$$, then, by Markov's inequality, we would obtain a concentration of measure inequality:

$$
\left\{
\begin{aligned}
\mathbb{P}[Z \geq \lambda] &= \mathbb{P}[\exp(tZ) \geq \exp(t\lambda)] \leq e^{-\lambda t} M_Z(t) \\
\mathbb{P}[-Z \geq \lambda] &= \mathbb{P}[\exp(-tZ) \geq \exp(t\lambda)] \leq e^{-\lambda t} M_{Z}(-t)
\end{aligned}
\right.
\quad \Longrightarrow \quad
\mathbb{P}[|Z| \geq \lambda] \leq e^{-\lambda t}\big(M_Z(t) + M_{Z}(-t)\big)
$$

A general way of doing so is by approximating the exponential function close to zero at the second order, then we would obtain an exponential bound on the moment generating function for all bounded random variables on an interval $$[-\varepsilon,\varepsilon]$$ for some strictly positive $$\varepsilon>0$$.
<!--
<div class="lemma" markdown="1">
<span class="lemma-title"></span>
Let $$X$$ be some random variable of mean zero and $$|X| \leq 1$$, then for all $$t \in [-1,1]$$ of absolute value at most 1 we have $$M_X(t) \leq \exp(t^2\text{Var}(X))$$.
<div>

<div class="proof" markdown="1">
<span class="proof-title"></span>
We begin by a classical second order estimate of the exponential function close to zero, namely that $$\exp(tX) \leq 1 + tX + t^2X^2$$ (which holds as $$|tX| \leq 1 $$). Applying the expectation, we find that:

$$
\mathbb{E}[\exp (tX)] \leq 1 + t^2 \text{Var}(X)
$$

The result then follows by the inequality $$1 + x \leq \exp(x)$$.
<span class="qed"> </span>
</div>
-->
Moreover, in the case where $$Z$$ may be expressed as a sum of independent random variables, this idea can be amplified by exploiting the formula $$\mathbb{E}[XY] = \mathbb{E}[X]\mathbb{E}[Y]$$ whenever $$X$$ and $$Y$$ are independentant random variables.

All in all, the better we understand the behaviour of our moment generating function, the tighter of an upperbound we can obtain on the density of the tails of our distribution. We will apply this strategy to the random variable $$\lVert \sum _i \varepsilon _i v_i\rVert $$ in order to obtain a new *small sum* theorem.