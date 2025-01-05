---
layout: default
title: Evolution
nav_order: 3
permalink: docs/evolution
---

## Evolution of Interest Rate Models 

With decent understanding of everything mentioned in the basics, here the story begins. 

### Short Rate Models 

It should start with the short rate modeling. In a time-homogeneous risk-neutral equillibrium market, we first have a derivation of the generalized term-structure from Vasicek at 1977. 

A special case is derived to show the market equillibrium following a Ornstein-Uhlenback process which is equivalent to a stationary Gauss-Markov process. Based on my understanding, equillibrium here means a stable bond price or equivalently a stable interest rate based on supply and demand of the underlyings. This is also the reason that this special case is a mean-reverting process. This special case has a form: 

  is risk-neutral Stochastic Brownian Motion and  is following Normal Distribution. 

$$
dr(t) = k(\theta - r(t)) + \sigma d\tilde{W}(t) \hspace{0.5cm} \text{(Vasicek 1977)}
$$

$$
dr(t) = k(\theta - r(t))dt + \sigma \sqrt{r(t)} d\tilde{W}(t) \hspace{0.5cm} \text{(CIR 1985)}
$$

$$
dr(t) = (\theta(t)-k(t)r(t))dt + \sigma(t)r(t) d\tilde{W}(t) \hspace{0.5cm} \text{(Hull-White 1990)}
$$

$$
df(t, T) = \alpha (t, T)dt + \sigma(t, T)dW(t)
$$

$$
\frac{\mu(t, S_1)-r(t)}{\sigma(t, S_1)} = 
$$

If we want a calibration for zero coupon bond price, we derive it using Feynman-Kac. Solving the PDE gives us an Affine Term-Structure Model. 

### Instantaneous Forward Rate Models 

For HJM
$$
E_{Q}\left(e^{-\int_{t}^{T} r(u)du} \right)
$$

$$
e^{-\int_{t}^{T} f(t,u)du}
$$

### Market Models 
