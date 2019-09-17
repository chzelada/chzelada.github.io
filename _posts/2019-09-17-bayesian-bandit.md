---
layout: post
author: Carlos Zelada
---

Understanding what a statistician does sometimes is hard to explain; this makes it hard for an organization to be data-driven.  So to understand some key concepts related to this, we could start by using the analogy of fishing.

## Point estimates
![rod fishing](http://www.potatobushcamp.com/images/activities/potato-bush-fishing-2-L.jpg)

Let's start by imagining we are on the shore of a lake, and there's only one fish. 

So the first option we have is to use a fishing rod. If we are on a big lake, it will take a lot of time, and we will have to move around the shore many times.



This is precisely the idea behind the mean or the proportion of a population. We are trying to give a good estimate of each of the metrics.

### Mean

![mean](https://latex.codecogs.com/png.latex?%5Ctext%7Bmean%7D%20%3D%20%5Cfrac%7B%5Csum_%7Bi%3D1%7D%5En%20x_i%7D%7Bn%7D)

```R
mean <- sum(sample) / length(sample)
```
In this case we sample and as we sample we get a better estimate of the population mean.

### Proportion
```R
ctr<-sum(clicks)/impressions
```
For proportion **ctr** *(Click-through rate)* is use as an example since it a key metric in healthcare.com. If this is an ad we are interested in it because de revenue will be calculated as 

<a href="https://www.codecogs.com/eqnedit.php?latex=\text{expected&space;revenue}=\text{ctr}&space;\times&space;\text{cpc}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\text{expected&space;revenue}=\text{ctr}&space;\times&space;\text{cpc}" title="\text{expected revenue}=\text{ctr} \times \text{cpc}" /></a>

where cpc is the cost per click.

For new ads this metric is unknow and we get a better idea as we get for impressions of the ad.

## Confidence intervals
![net fishing](https://media.nationalgeographic.org/assets/photos/000/257/25789.jpg)
So now after spending a lot of time walking around the shore you get a better idea, to use a net insted of a rod. With a net you should increase your chance to get the fish. 

This is the idea of confidence intervals, instead of trying to give a point estimation we end up giving a interval and attach a probability of caching the populatin parameter inside this interval.

### Mean confidence interval
![mean confidence interval](https://latex.codecogs.com/gif.latex?%5Cmu%20%5Cin%20%28%5Cbar%20x%20-Z_%7B%5Calpha/2%7D%5Cfrac%7B%5Csigma%7D%7B%5Csqrt%20n%7D%2C%5Cbar%20x%20&plus;%20Z_%7B%5Calpha/2%7D%5Cfrac%7B%5Csigma%7D%7B%5Csqrt%20n%7D%29)

### Proportion confidence interval
![proportion confidence interval](https://latex.codecogs.com/gif.latex?%5Crho%20%5Cin%20%5Cleft%28%5Chat%20%5Crho%20-%20z_%7B%5Calpha/2%7D%5Csqrt%7B%5Cfrac%7B%5Chat%20%5Crho%20%281%20-%20%5Chat%20%5Crho%20%29%7D%7Bn%7D%7D%2C%5Chat%20%5Crho%20&plus;%20z_%7B%5Calpha/2%7D%5Csqrt%7B%5Cfrac%7B%5Chat%20%5Crho%20%281%20-%20%5Chat%20%5Crho%20%29%7D%7Bn%7D%7D%20%5Cright%20%29)


This is a great idea but updating the values after new information or more data is gatheres is not part of this. Thats because this equations and the theory behind it is old and comes from an age that data gathering was slow and in small numbers. Times have change and now data is generated at blazing speeds so updating our estimates is of paramount importance. Thats where bayes comes in.

## Bayes Theorem

![Bayes Theorem](https://latex.codecogs.com/gif.latex?P%28H%7CD%29%3D%5Cfrac%7BP%28D%7CH%29P%28H%29%7D%7BP%28D%29%7D)

- The prior  **P(H)** is the probability that H is true before data is considered.
- The posterior **P(H|D)** is the probability that H is true after data is considered.
- The likelihood **P(D|H)** is the evidence about H provided by the data D.
- **P(D)** is the total probability of the data taking into account all possible hypotheses.







