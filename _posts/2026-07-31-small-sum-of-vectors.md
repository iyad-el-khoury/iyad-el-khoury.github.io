---
layout: post
author: Iyad El Khoury
comments: true
---

Let $$(V, \lVert \cdot \rVert)$$ be a normed real vector space and $$v_1, v_2, \dots, v_n \in V$$ a family of $$n$$ unit vectors in $$V$$. A famous problem in geometry is to ask how small can the vector $$\varepsilon_1 v_1 + \dots + \varepsilon_n v_n$$ be made, where $$\varepsilon_i \in \{-1,1\}$$ is a choice of sign for each vector $$v_i$$. Our task is thus to find some upper bound, $$f(n)$$, such that for an arbitrary family of $$n$$ unit vectors, there exists some choice of signs, $$\{\varepsilon_i\}_{i} \in \{-1,1\}^n$$, satisfying $$\lVert\varepsilon_1 v_1 + \dots + \varepsilon_n v_n\rVert \leq f(n)$$. I will call any theorem of this kind a *small sum* theorem.

As the space of signs, $$\{-1,1\}^n$$, is exponential in $$n$$ and the vectors $$\{v_i\}_i$$ are arbitrary, it seems reasonable that the correct approach to this problem would be to borrow the probabilistic method in combinatorics. Let us begin with the case where $$V = \mathbb{R}^d$$ and $$\lVert \cdot \rVert$$ is a Euclidean norm.

### The Euclidean case
Let $$(\mathbb{R}^d,\langle \cdot \mid \cdot \rangle)$$ be a Euclidean space, denote by $$\lVert \cdot \rVert $$ the norm induced by the scalar product $$\langle \cdot \mid \cdot \rangle$$ and  $$v_1, v_2, \dots, v_n \in \mathbb{R}^d$$ be unit vectors. We will consider a random choice of signs $$\{\varepsilon_i\}_{i} \in \{-1,1\}^n$$, or more precisely, let $$\varepsilon_i \sim \text{Unif}(\{-1,1\})$$ be i.i.d Rademacher random variables. We are therefore interested in understanding the Euclidean norm of the random variable $$Z = \varepsilon_1 v_1 + \dots + \varepsilon_n v_n$$. To exploit the bilinearity of the Euclidean scalar product, it will be simpler to consider the norm squared of $$Z$$, that is to say the quantity $$\langle Z \mid Z\rangle$$. Calculating the expected value of $$\lVert Z \rVert^2$$ is direct:

$$
\mathbb{E}\big[\langle Z \mid Z \rangle\big] = \sum_{i=1}^n \sum_{j=1}^n \mathbb{E}[\varepsilon_i \varepsilon_j] \langle v_i \mid v_j \rangle = \sum_{i=1}^n \lVert v_i \rVert ^2= n
$$

By the first moment method, we thus know there exists a choice of signs $$\{\bar \varepsilon _i\}_i \in \{-1,1\}^n$$ such that $$\lVert \bar \varepsilon_1 v_1 + \dots + \bar \varepsilon_n v_n  \rVert^2 \leq n$$. This immediately gives us a first result:

<div class="theorem" markdown="1">
<span class="theorem-title"></span>
For any Euclidean norm, $$\lVert \cdot \rVert$$ on $$\mathbb{R}^d$$ and unit vectors $$v_1,\dots,v_n\in \mathbb{R}^d$$, there exists $$\{\varepsilon_i\}_i \in \{-1,1\}^n$$ such that:

$$ 
\left\lVert \varepsilon_1 v_1 + \dots + \varepsilon_n v_n \right\rVert \leq \sqrt{n} 
$$

</div>

We may also notice that this result is tight, for example, by considering the standard Euclidean norm and the canonical unit vectors $$e_1,\dots,e_n \in \mathbb{R}^d$$, the vector $$Z = \sum _i \varepsilon _i e_i $$ is a vertex of the hypercube $$[-1,1]^n$$ for any choice of $$\{\varepsilon _i \}_i \in \{-1,1\}^n$$. Therefore, in this case there is no choice of signs which obtains a norm of $$Z$$ smaller than $$\sqrt{n}$$.

### The infinity norm case
Let us denote by $$\lVert \cdot \rVert _\infty$$ the infinity norm of $$\mathbb{R}^d$$ defined by $$\lVert (x_1, \dots, x_d) \rVert _\infty = \max _i \vert x_i\vert$$. We recall that this is not a Euclidean norm, for example, the parallelogram law does not hold for $$\lVert \cdot \rVert _\infty$$. To establish a *small sum* theorem for the infinity norm, it suffices to find $$\{\varepsilon _i \}_i \in \{-1,1\}^n$$ such that all coordinates of $$Z$$ are smaller than some $$f(n)$$. Once again, our strategy is to use a probabilistic argument, and in this case, to find a function $$f$$ such that $$\mathbb{P}[\lVert Z \rVert _\infty > f(n)] < 1$$. By the symmetry between coordinates and the definition of the infinity norm, it will suffice to treat the one dimensional case and show that $$\mathbb{P}[\vert Z \vert> f(n)] < 1/d$$, since the previous inequality will follow from a union bound. To achieve this we will make use of the exponential moment method, which I will quickly review before applying it to our problem. 

#### The exponential moment method
Let $$Z$$ be some real valued random variable, then the function $$t\mapsto \mathbb{E}[\exp(tZ)]$$ is called the moment generating function of $$Z$$ and may be expanded as a power series given by the following formula $$M_Z(t) = \sum _{n\geq 0} \mathbb{E}[Z^n] \frac{t^n}{n!}$$. 

Given we have control on the moment generating function of $$Z$$, then, by Markov's inequality, we would obtain a concentration of measure inequality:

$$
\left\{
\begin{aligned}
\mathbb{P}[Z \geq \lambda] &= \mathbb{P}[e^{tZ} \geq e^{t\lambda}] \leq e^{-\lambda t} M_Z(t) \\
\mathbb{P}[Z \leq -\lambda] &= \mathbb{P}[e^{-tZ} \geq e^{t\lambda}] \leq e^{-\lambda t} M_{Z}(-t)
\end{aligned}
\right.
\quad \Longrightarrow \quad
\mathbb{P}[\vert Z \vert \geq \lambda] \leq e^{-\lambda t}\big(M_Z(t) + M_{Z}(-t)\big)
$$

<!--

A general way of doing so is by approximating the exponential function close to zero at the second order, then we would obtain an exponential bound on the moment generating function for all bounded random variables on an interval $$[-\varepsilon,\varepsilon]$$ for some strictly positive $$\varepsilon>0$$.

<div class="lemma" markdown="1">
<span class="lemma-title"></span>
Let $$X$$ be some random variable of mean zero and $$\vert X \vert \leq 1$$, then for all $$t \in [-1,1]$$ of absolute value at most 1 we have $$M_X(t) \leq \exp(t^2\text{Var}(X))$$.
</div>

<div class="proof" markdown="1">
<span class="proof-title"></span>
We begin by a classical second order estimate of the exponential function close to zero, namely that $$\exp(tX) \leq 1 + tX + t^2X^2$$ (which holds as $$\vert tX \vert \leq 1 $$). Applying the expectation, we find that:

$$
\mathbb{E}[\exp (tX)] \leq 1 + t^2 \text{Var}(X)
$$

The result then follows by the inequality $$1 + x \leq \exp(x)$$.
<span class="qed"> </span>
</div>

-->

Moreover, in the case where $$Z$$ may be expressed as a sum of independent random variables, $$X_1,\dots,X_n$$, this idea can be amplified by exploiting the formula $$\mathbb{E}[XY] = \mathbb{E}[X]\mathbb{E}[Y]$$ whenever $$X$$ and $$Y$$ are independent random variables:

$$ 
\mathbb{P}[Z \geq \lambda] \leq   e^{-\lambda t} \mathbb{E}[\exp(tZ)] = e^{-\lambda t} \mathbb{E}[\prod_i \exp(tX_i)] = e^{-\lambda t} \prod_i \mathbb{E}[ \exp(tX_i)] 
$$


All in all, as we can choose a minimizing $$t$$, the better we understand the behaviour of our moment generating function, the tighter of an upper bound we can obtain on the density of the tails on our distribution. We will apply this strategy to the random variable $$ \sum _i \varepsilon _i v_i $$ in order to obtain a new *small sum* theorem.

#### A concentration of measure inequality

Let $$v_1,\dots,v_n \in [-1,1]$$ be real numbers of absolute value at most 1 and $$\varepsilon_i \sim \text{Unif}(\{-1,1\})$$ be i.i.d Rademacher random variables as before. By our previous discussion we are interested in establishing a concentration inequalty for the random variable $$Z = \sum _i \varepsilon _i v_i$$, which will translate directly into a *small sum* theorem. 

To be able to effectively apply the exponential moment method, we must carefully analyze $$M_Z(t)$$:

$$ 
\mathbb{E}[\exp(tZ)] = \prod_i \mathbb{E}[ \exp(t\varepsilon_i v_i)] = \prod_i\cosh(tv_i) \leq \prod_i e^{v_i^2t^2/2} \leq  e^{nt^2/2}
$$ 

where the inequality $$\cosh(x) \leq e^{x^2/2}$$ follows by a simple term by term comparison of the respective power series. Hence, for all $$\lambda \geq 0$$, by the exponential moment method combined with our previous inequality:

$$
\forall t\in \mathbb{R} \quad \mathbb{P}[Z \geq \lambda] \leq e^{nt^2/2-\lambda t} \implies \mathbb{P}[Z \geq \lambda] \leq \inf_{t\in \mathbb{R}} e^{nt^2/2-\lambda t}
$$

By a straight forward computation, we see that $$t = \lambda/n$$ is best possible and thus that  $$\mathbb{P}[Z \geq \lambda] \leq e^{-\lambda^2/2n}$$. By the symmetry $$Z\sim -Z$$, we immediatly obtain the identical upper bound on the lower tail of the distribution and therefore that $$ \mathbb{P}[\vert Z \vert \geq \lambda] \leq 2 e^{-\lambda^2/2n} $$. 

Let us now translate this concentration inequality into a *small sum* theorem. We return to the $$d$$-dimensional case, i.e when $$v_1,\dots,v_n \in \mathbb{S}^{d-1}$$. Fix some positive $$ \lambda > \sqrt{2n\ln(2d)}$$, then by the above concentration inequality we find that for each $$j\in \{1,\dots,d\}$$:

$$
\mathbb{P}[\vert Z_j \vert \geq \lambda] \leq 2e^{-\lambda^2/2n} < 1/d \quad \text{, where } Z_j \text{ is the }j\text{-th coordinate of } Z
$$

Thus, by the union bound, $$\mathbb{P}[\lVert Z \rVert _\infty \geq \lambda] <1$$ and hence there must exist some choice of signs, $$\{\bar \varepsilon _i\}_i \in \{-1,1\}^n$$ such that the infinity norm of $$\sum _i \bar \varepsilon _i v_i$$ is smaller than $$\lambda$$.

 To be able to obtain a best possible result, we may use a limiting argument. Pick any arbitrary sequence of $$\{\lambda_j\}_{j\geq 0}$$ of positive real numbers strictly greater than $$\sqrt{2n\ln(2d)}$$ converging to this lower bound $$\sqrt{2n\ln(2d)}$$. By the above, for all $$j\geq 0$$ there exists a choice of signs, $$\{ \varepsilon^{(j)} _i\}_i \in \{-1,1\}^n$$ such that $$\lVert \sum _i  \varepsilon _i v_i \rVert _\infty < \lambda_j $$. However, since the space of signs is finite, there exists a subsequence $$\{\lambda_{k_j}\}_{j\geq 0}$$ for which the choice of signs $$\{ \varepsilon^{(k_j)} _i\}_i $$ is constant, let us denote this constant value by $$\{\bar \varepsilon _i\}_i$$. Noticing that for all $$j\geq 0$$, $$\lVert \sum _i \bar \varepsilon _i v_i \rVert _\infty < \lambda_{k_j}$$, we deduce that in fact $$\lVert \sum _i \bar \varepsilon _i v_i \rVert _\infty \leq \sqrt{2n\ln(2d)}$$. We have concluded our second *small sum* theorem:

<div class="theorem" markdown="1">
<span class="theorem-title"></span>
Let $$v_1,\dots,v_n\in \mathbb{R}^d$$ be unit vectors for the infinity norm. Then there exists $$\{\varepsilon_i\}_i \in \{-1,1\}^n$$ such that:

$$ 
\left\lVert \varepsilon_1 v_1 + \dots + \varepsilon_n v_n \right\rVert _\infty \leq \sqrt{2n\ln(2d)}
$$

</div>

Quite interestingly, however not very surprising given our method, unlike the Euclidean case, this upper bound has a logarithmic dependance on the dimension of the space in which the $$\{v_i\}_i$$s live.

### A result regarding general norms

A trivial *small sum* theorem which we haven't yet discussed is the following basic application of the triangle inequality:

<div class="theorem" markdown="1">
<span class="theorem-title"></span>
Let $$(V,\lVert \cdot \rVert)$$ be a finite dimensional normed vector space over $$\mathbb{R}$$ and $$v_1,\dots,v_n\in V$$ be unit vectors with respect to $$\lVert \cdot \rVert$$.  Then there exists $$\{\varepsilon_i\}_i \in \{-1,1\}^n$$ such that:

$$ 
\left\lVert \varepsilon_1 v_1 + \dots + \varepsilon_n v_n \right\rVert \leq n
$$

</div>

Of course, this statement is true for *all* choice of signs, which makes the theorm uninteresting in our context.

However, when $$n$$ is much larger than $$d := \dim (V)$$,  we can use collinearity of our family to restrict ourselves to a constant portion of the $$\{v_i\}_i$$ and apply the triangle inequality on the rest of our vectors. Let us state a lemma, which will be proved in the next section, in order to implement this idea.

<div class="lemma" markdown="1">
<span class="lemma-title"></span>
Let $$V \subset \mathbb{R}^n$$ be a $$k$$ dimensional subspace of $$\mathbb{R}^n$$. Then there exists a vector $$v\in V \cap [-1,1]^d$$ with at least $$k$$ coordinates in $$\{-1,1\}$$. 
</div>

Geometrically, this lemma states that any $$k$$-dimensional subspace must intersect a $$n-k$$-dimensional face of the polytope $$[-1,1]^d$$, which is intuitive, for example in dimensions 2 and 3.

Admitting this lemma for a moment, let us now prove the follwing *small sum*  theorem, which can be thought of as a stronger version of Theorem 3 in the regime $$n \gg d$$:

<div class="theorem" markdown="1">
<span class="theorem-title"></span>
Let $$(V,\lVert \cdot \rVert)$$ be a $$d$$-dimensional normed vector space over $$\mathbb{R}$$ and $$v_1,\dots,v_n\in V$$ be unit vectors with respect to $$\lVert \cdot \rVert$$.  Then there exists $$\{\varepsilon_i\}_i \in \{-1,1\}^n$$ such that:

$$ 
\left\lVert \varepsilon_1 v_1 + \dots + \varepsilon_n v_n \right\rVert \leq d
$$

</div>
<div class="proof" markdown="1">
<span class="proof-title"></span>
Let us denote by $$M= \left(v_1\mid v_2 \mid \dots \mid v_n\right)$$ the $$d\times n$$ matrix whose columns are formed by the vectors $$\{v_i\}_i$$ and by $$\ker M$$ the kernel of this matrix. Of course, by the rank-nullity theorem, the dimension of $$\ker M$$ is $$n - r$$, where $$r = \dim\text{Span}(\{v_i\}_i)$$. Hence, $$\ker (M)$$ is least $$n-d$$ dimensional. Applying Lemma 1, there must exist a vector $$\lambda = (\lambda_1,\dots, \lambda_n) \in \ker M \cap [-1,1]^n$$ with at least $$n-d$$ of its coordinates in $$\{-1,1\}$$, we denote their indices by $$ I = \{i_1< i_2 < \dots < i_{n-d}\}$$. As $$\lambda\in \ker M$$ we have that:

$$
\sum_{j\in I}\lambda_{j} v_{j} + \sum_{j\notin I}\lambda_{j} v_{j} = 0
$$

Finally, let us denote by $$\{\varepsilon_i\}_{i} \in \{-1,1\}^n$$ the sign of each coordinate $$\lambda_i$$, where this sign is chosen arbitrarily whenever $$v_i = 0$$. Then our linear relation transforms into:

$$
\sum_{j\in I}\varepsilon_{j} v_{j} + \sum_{j\notin I}\varepsilon_j \vert\lambda_{j}\vert v_{j} = 0 \iff \sum_{j\in I}\varepsilon_{j} v_{j} + \sum_{j\notin I}\varepsilon_j v_{j} = \sum_{j\notin I}\varepsilon_j (1 - \vert\lambda_{j}\vert)v_{j}
$$

By the triangle inequality we conclude that:

$$
\left \lVert  \sum_{j\in I}\varepsilon_{j} v_{j} + \sum_{j\notin I}\varepsilon_j v_{j}  \right \rVert \leq \sum_{j\notin I} (1 - \vert\lambda_{j}\vert) \leq d 
$$

Completing the proof, as we have found signs $$\{\varepsilon _i \}_i \in \{-1,1\}^n$$ such that $$ \lVert \sum_i\varepsilon_iv_i \rVert \leq d$$.
<span class="qed"> </span>
</div>


#### Proof of Lemma 1

We now give a proof of Lemma 1, let us fix $$V\subset \mathbb{R}^d$$ and denote $$k:= \dim V$$. In the rest of this section we will denote by $$\lVert \cdot \rVert$$ the standard Euclidean norm in $$\mathbb{R}^d$$.

 We would like to find a vector $$x\in V$$ which has at least $$k$$ coordinates in $$\{-1,1\}$$. Intuitevly, we expect a vector with many coordinates in $$\{-1,1\}$$ to have a larger Euclidean norm, thus it feels natural to pick $$x\in V\cap [-1,1]^d$$ as a vector of maximal norm.
 
 <div class="proof" markdown="1">
<span class="proof-title"></span>
For $$J\subset [d]$$, denote $$F_J := \text{Span}(e_j \mid j\in J)$$, with the convention that $$F_\emptyset = \{0\}$$. We consider the squared Eucldian norm as a function on $$\Sigma := V\cap [-1,1]^d$$, $$\lVert \cdot \rVert^2:\Sigma \ni z \mapsto \lVert z \rVert^2$$
 
 
  As $$\Sigma$$ is compact and $$\lVert \cdot \rVert^2$$ is continuous, there exists $$x = (x_1,\dots,x_d)\in \Sigma$$ maximising this function. Define $$J :=\{j\in [d] \mid x_j \in \{-1,1\} \}$$ and suppose for contradiction that $$x$$ has strictly less than $$k$$ coordinates in $$\{-1,1\}$$, i.e $$\vert J\vert < k$$. Then, the vector space $$F_J^\perp = F_{J^c}$$ is of dimension at least $$d-k+1$$ and intersects non-trivialy with $$V$$. Fix arbitrarily some non-zero $$w\in V \cap F_{J^c}$$, since for all indices $$j\in J^c$$, $$\vert x_j\vert < 1$$ and for all $$j\in J$$, $$z_j = 0$$ there exists a neighberhood, $$I$$ of 0, such that for all $$\delta \in I$$  $$x + \delta z$$ remains in $$\Sigma$$.
  
   Finally, as $$\lVert x + 2\delta z \rVert^2 = \lVert x \rVert^2 +\delta \langle z,x\rangle + \delta^2\lVert z \rVert^2$$, choosing non-zero $$\delta \in I$$ with the same sign as $$\langle z,x\rangle$$ (or arbitrarily if this term is zero), we have found another vector in $$\Sigma$$ with strictly larger square Euclidean norm, a contradiction.
<span class="qed"> </span>
</div>