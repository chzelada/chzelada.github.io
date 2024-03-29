---
layout: post
author: Carlos Zelada
---

Understanding what a statistician does sometimes is hard to explain; this makes it hard for an organization to be data-driven.  So to understand some key concepts related to this, we could start by using the analogy of fishing.

## Point estimates
![rod fishing](http://www.potatobushcamp.com/images/activities/potato-bush-fishing-2-L.jpg)

Let's start by imagining you are on the shore of a lake, and there's only one fish. 

So the first option you have is to use a fishing rod. If you are on a big lake, it will take a lot of time, and you will have to move around the shore many times.



This is precisely the idea behind the mean or the proportion of a population. You are trying to give a reasonable estimate of each of the metrics.

### Mean

![mean](https://latex.codecogs.com/png.latex?%5Ctext%7Bmean%7D%20%3D%20%5Cfrac%7B%5Csum_%7Bi%3D1%7D%5En%20x_i%7D%7Bn%7D)

```R
mean <- sum(sample) / length(sample)
```
In this case,  as you sample, you get a better estimate of the population mean.

### Proportion
```R
ctr<-sum(clicks)/impressions
```
For proportion **ctr** *(Click-through rate)* is used as an example since it a key metric in healthcare.com. If this is an ad you are interested in it because the revenue is calculated as 

<a href="https://www.codecogs.com/eqnedit.php?latex=\text{expected&space;revenue}=\text{ctr}&space;\times&space;\text{cpc}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\text{expected&space;revenue}=\text{ctr}&space;\times&space;\text{cpc}" title="\text{expected revenue}=\text{ctr} \times \text{cpc}" /></a>

In the formula, cpc is used for cost per click.

For new ads, this metric is unknow, and you get a better idea as you get more impressions of the ad.

## Confidence intervals
![net fishing](https://media.nationalgeographic.org/assets/photos/000/257/25789.jpg)
So now after spending a lot of time walking around the shore, you get a better idea, to use a net instead of a rod. With a net, you should increase your chance to get the fish. 

This is the idea of confidence intervals, instead of trying to give a point estimation, you end up giving an interval and attach a probability of caching the population parameter inside this interval.

### Mean confidence interval
![mean confidence interval](https://latex.codecogs.com/gif.latex?%5Cmu%20%5Cin%20%28%5Cbar%20x%20-Z_%7B%5Calpha/2%7D%5Cfrac%7B%5Csigma%7D%7B%5Csqrt%20n%7D%2C%5Cbar%20x%20&plus;%20Z_%7B%5Calpha/2%7D%5Cfrac%7B%5Csigma%7D%7B%5Csqrt%20n%7D%29)

### Proportion confidence interval
![proportion confidence interval](https://latex.codecogs.com/gif.latex?%5Crho%20%5Cin%20%5Cleft%28%5Chat%20%5Crho%20-%20z_%7B%5Calpha/2%7D%5Csqrt%7B%5Cfrac%7B%5Chat%20%5Crho%20%281%20-%20%5Chat%20%5Crho%20%29%7D%7Bn%7D%7D%2C%5Chat%20%5Crho%20&plus;%20z_%7B%5Calpha/2%7D%5Csqrt%7B%5Cfrac%7B%5Chat%20%5Crho%20%281%20-%20%5Chat%20%5Crho%20%29%7D%7Bn%7D%7D%20%5Cright%20%29)


This is a great idea but updating the values after new information or more data is gathered is not part of this. That's because this equations and the theory behind it is old and comes from an age that data gathering was slow and in small numbers. Times have changed, and now data is generated at blazing speeds so updating our estimates is of paramount importance. That's where Bayes comes in.

## Bayes Theorem

![Bayes Theorem](https://latex.codecogs.com/gif.latex?P%28H%7CD%29%3D%5Cfrac%7BP%28D%7CH%29P%28H%29%7D%7BP%28D%29%7D)

- The prior  $$P(H)$$ is the probability that H is true before data is considered.
- The posterior $$P(H \mid D)$$ is the probability that H is true after data is considered.
- The likelihood $$P(D \mid H)$$ is the evidence about H provided by the data D.
- $$P(D)$$ is the total probability of the data taking into account all possible hypotheses.

So the probability that you are interested in is given de data that we have generated so far $$(D)$$ what is the probability of the hypothesis $$(H)$$. 

As an example, imaging you have a landing page with two ads. Both ads are new, so we need to get an idea of its true conversion rate. So far we have this information


| Ad | impressions | click |
|---|-----|-----|
|1 | 10 | 5 |
|2 | 10 | 6 |


For the first ad, we have a ctr of 0.5

> How sure you are that if you get 1000 impressions to this ad. The conversion rate will continue to be 0.5

Based on experience alone, you know that calculating conversion rates with only ten impressions are not even close to the ads true click-through rate.

Now imagine you have a landing page and only one block where you show an ad. But you have ten ads that you can show in that block. All ads are new, and you don't have any knowledge of its ctr. Since this is the only block that you have available to put the ads you want to show only the ads that have the best conversion rate, this will bring more revenue. 

But how to manage this?

This brings us to our main topic and what we need to cover to propose a solution.

- Bayesian statistics
- Multi-arm bandits 
- Exploration and exploitation trade-off

The proposed solution will be covered in a next blog post.


