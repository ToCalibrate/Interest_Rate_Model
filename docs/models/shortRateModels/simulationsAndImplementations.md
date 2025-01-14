---
layout: default
title: Simulations and Implementations
parent: Short Rate Models
grand_parent: Models
nav_order: 2
permalink: docs/models/shortRateModels/simulationsAndImplementations
---

# Simulations and Calibrations
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Simulate for Short Rate Paths
```python
import numpy as np 
import pandas as pd 

class ShortRate(): 
    # Generate Short Rates using Monte Carlo Simulation 

    def __init__(self, r0, theta, kappa, sigma): 

        # Read in time length you want to predict 
        self.r0 = r0
        self.theta = theta 
        self.kappa = kappa 
        self.sigma = sigma 
    
    def Vasicek(self, n_simulation=100, tenor=10, dt=1): 
        # Simulate short rate paths under Vasicek design 

        # Initiate rate paths table 
        index = [i*dt for i in range(int(tenor/dt))]
        columns = [i+1 for i in range(n_simulation)]
        rate_paths = pd.DataFrame(index=index, columns=columns)
        rate_paths.loc[0, :] = self.r0 

        # Simulate rate path for each time increment
        for i in range(1, len(rate_paths)): 
            dWt = np.random.normal(0, np.sqrt(dt), size=n_simulation) 
            rate_paths.loc[i*dt, :] = rate_paths.loc[(i-1)*dt, :]
                                        + self.kappa*(self.theta-rate_paths.loc[(i-1)*dt, :])*dt
                                        + self.sigma * dWt

        return rate_paths

    def CIR(self, n_simulation=100, tenor=10, dt=1): 
        # Simulate short rate paths under CIR design 

        # Initiate rate paths table 
        index = [i*dt for i in range(int(tenor/dt))]
        columns = [i+1 for i in range(n_simulation)]
        rate_paths = pd.DataFrame(index=index, columns=columns)
        rate_paths.loc[0, :] = self.r0 

        # Simulate rate path for each time increment
        for i in range(1, len(rate_paths)): 
            dWt = np.random.normal(0, np.sqrt(dt), size=n_simulation) 
            rate_paths.loc[i*dt, :] = rate_paths.loc[(i-1)*dt, :]
                                        + self.kappa*(self.theta-rate_paths.loc[(i-1)*dt, :])*dt
                                        + self.sigma * np.sqrt(rate_paths.loc[(i-1)*dt, :]) * dWt

        return rate_paths
```

## Coming up......... 

### Swaption Analytical Formula Implementation using Hull White
