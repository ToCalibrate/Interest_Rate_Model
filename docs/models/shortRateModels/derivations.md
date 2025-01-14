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
    dr(t) &= \kappa(\theta - r(t))dt + \sigma dWt \\
    dr(t) &= \kappa \theta dt - \kappa r(t) dt + \sigma dW_t \\
    e^{\kappa t} dr(t) &= -\kappa r(t) e^{\kappa t}dt + \kappa \theta e^{\kappa t}dt + \sigma e^{\kappa t}dW_t\\
    \int_0^t e^{\kappa s}dr(s) + \kappa r(s) e^{\kappa s}ds &= \int_0^t \kappa \theta  e^{\kappa s} ds + \int_0^t \sigma e^{\kappa s}dW_s\\
    e^{\kappa t}r(t) - r(0) &= \theta e^{\kappa t} - \theta + \sigma \int_0^t e^{\kappa s} dW_s\\
    r(t) &= r(0) e^{-\kappa t}+ \theta(1-e^{-\kappa t}) + \sigma \int_0^t e^{-\kappa (t-s)}dW_s\\
\end{align}
$$

### Solving for Bond Price $$B(r, t)$$ 

$$
\begin{align}
    P(0,t) &= E{\mathcal{Q}}(e^{-\int_0^t r(s) ds} \mid \mathcal{F}0)\\
    &= e^{E{\mathcal{Q}} (-\int0^t r(s) ds) + \frac{1}{2} Var{\mathcal{Q}} (-\int0^t r(s) ds)}\\
    E{\mathcal{Q}} \left[\int0^t r(s) ds\right] &= E{\mathcal{Q}} \left{\int0^t \left[r(0) e^{-\kappa s} + \theta (1-e^{-\kappa s}) + \sigma \int_0^s e^{-\kappa(s-u)} dW_u\right] ds\right }\\
    &= r(0) \frac{1-e^{-\kappa t}}{\kappa} + \theta t - \theta \frac{1-e^{-\kappa t}}{\kappa} + 0 \\
    &\text{as } E{\mathcal{Q}} \left[ \int0^t \sigma \int_0^s e^{-\kappa (s-u) dW_u ds}\right] = 0 \text{ under Martingale } \mathcal{Q} \text{ measure}\\
    Var{\mathcal{Q}} \left[\int0^t r(s) ds \right] &= \int_0^t Var{\mathcal{Q}} \left(r(s) \right) ds\\
    &= \int0^t Var{\mathcal{Q}} \left(\sigma \int0^s e^{-\kappa(s-u)} dW_u \right)ds\\
    &= \int_0^t E{\mathcal{Q}} \left(\sigma^2 \int_0^s e^{-2\kappa (s-u)}du \right)ds\\
    &= \int_0^t \frac{\sigma^2} {2\kappa} \left(1-e^{-2\kappa s}\right)ds\\
    &= \frac{\sigma^2} {2\kappa} t - \frac{\sigma^2} {4 \kappa^2} \left(1-e^{-2\kappa t}\right)\\
    &= \frac{\sigma^2} {2\kappa} t - \frac{\sigma^2} {4 \kappa^2} (1-e^{-\kappa t})^2 - \frac{\sigma^2} {4\kappa^2} 2e^{-\kappa t} (1-e^{-\kappa t}) \\
    &= -\frac{\sigma^2} {4\kappa^3} (1-e^{-\kappa t})^2 
\end{align}
$$

$$
\begin{align}
    P(0,t) &= exp(-B(t) r(t) + A(t))\\
    B(t) &= \frac{1-e^{-\kappa t}}{\kappa}\\
    A(t) &= \theta t - \theta B(t) -\frac{\sigma^2}{4 \kappa^3} (1-e^{-\kappa t})^2
\end{align}
$$
