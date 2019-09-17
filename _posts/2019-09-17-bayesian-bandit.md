---
layout: post
author: Carlos Zelada
---

Understanding what a statistician does sometimes is hard to explain; this makes it hard for an organization to be data-driven.  So to understand some key concepts related to this, we could start by using the analogy of fishing.

## Point estimates
Let's start by imagining we are on the shore of a lake, and there's only one fish. 



So the first option we have is to use a fishing rod. If we are on a big lake, it will take a lot of time, and we will have to move around the shore many times.

This is precisely the idea behind the mean or the proportion of a population. We are trying to give a good estimate of each of the metrics.

### Mean
```R
mean <- sum(sample) / length(sample)
```
In this case we sample and as we sample we get a better estimate of the population mean.

### Proportion
```R
ctr<-sum(clicks)/impressions
```
For proportion **ctr** *(Click-through rate)* is use as an example since it a key metric in healthcare.com. If this is an ad we are interested in it because de revenue will be calculated as **revenue = ctr times cpc**, *(cpc, cost per click)*. 

<a href="https://www.codecogs.com/eqnedit.php?latex=\text{revenue}&space;=&space;\text{clicks}\times\text{cpc}" target="_blank"><img src="https://latex.codecogs.com/png.latex?\text{revenue}&space;=&space;\text{clicks}\times\text{cpc}" title="\text{revenue} = \text{clicks}\times\text{cpc}" /></a>

For new adds this metric is unknow and we get a better idea as we get for impressions of the ad.
