---
layout: default
title: Derivations
parent: Short Rate Models
grand_parent: Models
nav_order: 1
permalink: docs/models/shortRateModels/derivations
---

# Derivations
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Vasicek 1977 

### Solving for Short Rate $$r(t)$$ 

$$
\begin{align}
dr(t) &= \kappa(\theta - r(t))\ dt + \sigma\ dW_t \\
&= \kappa \theta \ dt - \kappa r(t)\ dt + \sigma\ dW_t \\
e^{\kappa t} dr(t) &= -\kappa r(t) e^{\kappa t}\ dt + \kappa \theta e^{\kappa t}\ dt + \sigma e^{\kappa t}\ dW_t\\
\int_0^t e^{\kappa s} \ dr(s) + \int_0^t \kappa r(s) e^{\kappa s}\ ds &= \int_0^t \kappa \theta  e^{\kappa s} \ ds + \int_0^t \sigma e^{\kappa s}\ dW_s\\
e^{\kappa t}r(t) - r(0) &= \theta e^{\kappa t} - \theta + \sigma \int_0^t e^{\kappa s} \ dW_s\\
r(t) &= r(0) e^{-\kappa t} + \theta(1-e^{-\kappa t}) + \sigma \int_0^t e^{-\kappa (t-s)}\ dW_s\\
\end{align}
$$


### Solving for Bond Price $$B(r, t)$$ 

$$
\begin{align}
P(0,t) &= E\left(e^{-\int_0^t r(s) \, ds} \mid \mathcal{F}_0\right)\\
&= e^{E\left(-\int_0^t r(s) \, ds\right) + \frac{1}{2} \text{Var}\left(-\int_0^t r(s) \, ds\right)}\\
E\left[\int_0^t r(s) \, ds\right] &= E\left[\int_0^t \left(r(0) e^{-\kappa s} + \theta (1-e^{-\kappa s}) + \sigma \int_0^s e^{-\kappa(s-u)} \, dW_u\right) ds\right]\\
&= r(0) \frac{1-e^{-\kappa t}}{\kappa} + \theta t - \theta \frac{1-e^{-\kappa t}}{\kappa} + 0 \\
&\text{as } E\left[\int_0^t \sigma \int_0^s e^{-\kappa (s-u)} \, dW_u \, ds\right] = 0 \text{ under the martingale measure.}\\
\text{Var}\left[\int_0^t r(s) \, ds \right] &= \int_0^t \text{Var}\left(r(s)\right) \, ds\\
&= \int_0^t \text{Var}\left(\sigma \int_0^s e^{-\kappa(s-u)} \, dW_u \right)ds\\
&= \int_0^t E\left(\sigma^2 \int_0^s e^{-2\kappa (s-u)} \, du \right)ds\\
&= \int_0^t \frac{\sigma^2}{2\kappa} \left(1-e^{-2\kappa s}\right)ds\\
&= \frac{\sigma^2}{2\kappa} t - \frac{\sigma^2}{4 \kappa^2} \left(1-e^{-2\kappa t}\right)\\
&= \frac{\sigma^2}{2\kappa} t - \frac{\sigma^2}{4 \kappa^2} (1-e^{-\kappa t})^2 - \frac{\sigma^2}{4\kappa^2} 2e^{-\kappa t} (1-e^{-\kappa t}) \\
&= -\frac{\sigma^2}{4\kappa^3} (1-e^{-\kappa t})^2 \\
P(0,t) &= \exp\left(-B(t) r(t) + A(t)\right)\\
B(t) &= \frac{1 - e^{-\kappa t}}{\kappa}\\
A(t) &= \theta t - \theta B(t) - \frac{\sigma^2}{4 \kappa^3} \left(1 - e^{-\kappa t}\right)^2
\end{align}
$$



