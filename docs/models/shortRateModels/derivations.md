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
    dr(t) &= \kappa(\theta - r(t))dt + \sigma dWt \
    dr(t) &= \kappa \theta dt - \kappa r(t) dt + \sigma dW_t \
    e^{\kappa t} dr(t) &= -\kappa r(t) e^{\kappa t}dt + \kappa \theta e^{\kappa t}dt + \sigma e^{\kappa t}dW_t\
    \int_0^t e^{\kappa s}dr(s) + \kappa r(s) e^{\kappa s}ds &= \int_0^t \kappa \theta  e^{\kappa s} ds + \int_0^t \sigma e^{\kappa s}dW_s\
    e^{\kappa t}r(t) - r(0) &= \theta e^{\kappa t} - \theta + \sigma \int_0^t e^{\kappa s} dW_s\
    r(t) &= r(0) e^{-\kappa t}+ \theta(1-e^{-\kappa t}) + \sigma \int_0^t e^{-\kappa (t-s)}dW_s\
\end{align}
$$

### Solving for Bond Price $$B(r, t)$$ 

