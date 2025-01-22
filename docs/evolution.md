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

A special case is derived to show the market equillibrium following a Ornstein-Uhlenback process which is equivalent to a stationary Gauss-Markov process. Here, equillibrium refers to the identical market price of risk premium. 

$$
\frac{\mu(t, S_1)-r(t)}{\sigma(t, S_1)} = \frac{\mu(t, S_2)-r(t)}{\sigma(t, S_2)}
$$

Based on my understanding, equillibrium can be interpreted as a stablizing bond price or equivalently a stablizing interest rate based on supply and demand of the underlyings. This is also the reason that this special case is a mean-reverting process. This special case has a form: 

$$
dr(t) = k(\theta - r(t)) + \sigma d\tilde{W}(t) \hspace{0.5cm} \text{(Vasicek 1977)}
$$

where $$\tilde{W}(t)$$ is risk-neutral Stochastic Brownian Motion and $$r(t)$$ is following Normal Distribution. 

If we want a calibration for zero coupon bond price, we derive the risk neutral pricing formula using Feyman-Kac. Solving the PDE gives us an Affine Term-Structure Model. Detailed derivation will be given in the next few sections. 

Now, to overcome the possibility that interest rate will go negative and balance the effect of expected return and risk/volatility, three researchers proposed a new model form in 1985 named after their initials C.I.R.: 

$$
dr(t) = k(\theta - r(t))dt + \sigma \sqrt{r(t)} d\tilde{W}(t) \hspace{0.5cm} \text{(CIR 1985)}
$$

This time $$r(t)$$ follows a non-central Chi-squared distribution and remains positive which makes more sense practically. Similarly, an Affine model can be derived. 

Next, to further accomadate the lack of precise no-arbitrage condition for initial calibration, we redevelop time-homogeneous equillibrium model to time-homogeneous Markov model. This can also refer as the transition from endogenous to exogenous model on short rate since the drift and volatility terms are no longer constants but some deterministic functions. Calibrating to these functions will potentially close the arbitrage gap to achieve initial precise no-arbitrage. Anyways, the first ones propose this are Ho & Lee in 1986 based on binomial/trinomial tree models. This model can also be calibrated to Affine Term Structure Model, but it is lack of the mean-reverting dynamic and not continuous with the tree design. Another model that developed by Hull White in 1990 which is also an extension to the Vasicek model. 

$$
dr(t) = (\theta(t)-k(t)r(t))dt + \sigma(t) d\tilde{W}(t) \hspace{0.5cm} \text{(Hull-White 1990)}
$$

Hull White is able to generate an analytical solution for caplet, floorlet and swaption which is a big step in real world calibtraion. It is worth noting that Hull White model is capable of transition from short rate modeling to forward rate modeling with its Markov property and flexibility in parameter tuning. 

### Instantaneous Forward Rate Models 

Instantaneous forward rate models model forward rate $$f(t, T)$$ instead of short rate $$r(t)$$. There are two essential differences between the two. One is the rate dependency, and the other one is the bond valuation definition. 

For short rate modeling, the rate is an instantly forward looking rate at time $$t$$ and therefore only depends on $$t$$. In addition, we assume that the bond price under risk-neutral measure $$Q$$ is defined as 

$$
E_{Q}\left(e^{-\int_{t}^{T} r(u)du} \right)
$$

While in instantaneous forward rate models, the rate is an instantly forward looking rate after time interval $$(t, T)$$ and therefore depends on the tenor $$t$$ to $$T$$. In addition, we assume the bond price no longer depends on a static short rate, but a dynamic forward rate that is evolving based on the tenor. 

$$
e^{-\int_{t}^{T} f(t,u)du}
$$ 

This difference leads to the generalized formula of HJM framework named after Heath–Jarrow–Morton. 

$$
df(t, T) = \alpha (t, T)dt + \sigma(t, T)dW(t) \hspace{0.5cm} \text{(HJM 1991)}
$$

Under risk-neutral & no-arbitrage, $$f(t, t)$$ in HJM is equivalent to $$r(t)$$ in Hull White. This forward looking characteristic enables us to calibrate swaption prices using Hull White under HJM framework. 

### Market Models 

In order to make the calibration reconciling with market observable increments, we need to introduce the LIBOR Market model as it can be calibrated to actual LIBOR rates product. 

Actually, in 1976, Fisher Black who is famous for his Black-Scholes model had already introduced a model called Black-76 model. 

However, we won't elaborate it and will focus on a model that is actually calibratable called BGM model. 

### To be continued...........
