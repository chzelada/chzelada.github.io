---
layout: default
title: Multi Arm Bandit
---
# Multi Arm Bandit

This page tells you a little bit about me.

$latex \int_0^1 x^2 dx$

```R
bayesian_bandit <- function(clicks=1,
                           impressions=1,
                           n_samples=1000,
                           prior,
                           proportion_clicks){
  n_visitors <- seq(0, impressions, by = 1)
  pars <- expand.grid(proportion_clicks = proportion_clicks,
                      n_visitors = n_visitors)
  
  pars$prior <- prior
  n_visitors <- rbinom(n = n_samples, 
                       size = impressions, 
                       prob = proportion_clicks)
  pars$likelihood <- dbinom(pars$n_visitors, 
                            size = impressions, 
                            prob = pars$proportion_clicks)
  pars$probability <- pars$likelihood * pars$prior
  pars$probability <- pars$probability / sum(pars$probability)
  pars <- pars[pars$n_visitors ==clicks, ]
  pars$probability <- pars$probability / sum(pars$probability)
  prior_out <- data_frame(proportion_clicks=pars$proportion_clicks,
                          probability=pars$probability)
  return(prior_out)
}
```


```python
def add(x, y):
  return x+y
```
