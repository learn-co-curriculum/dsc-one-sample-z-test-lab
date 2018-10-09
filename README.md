
# One-sample z-test - Lab

### Introduction
In this lab we will go through quick tests to help you better understand the ideas around hypothesis testing.

## Objectives
You would be able to
* Understand and explain use cases for a 1-sample z-test
* Set up null and alternative hypotheses
* Calculate z statistic using z-tables and cdf functions
* Calculate and interpret p-value for significance of results.

## Exercise 1
A rental car company claims the mean time to rent a car on their website is 60 seconds with a standard deviation of 30 seconds. A random sample of 36 customers attempted to rent a car on the website. The mean time to rent was 75 seconds. Is this enough evidence to contradict the company's claim? 

<img src="http://www.guptatravelsjabalpur.com/wp-content/uploads/2016/04/car-rentalservice.jpg" width=400>

Follow the 5 steps shown in previous lesson and use alpha = 0.05. 


```python
# State you null and alternative hypotheses


# Ha : time to rent the car is greater than 60 seconds
# Ho : time to rent a car is less than or equal to 60 sec
```


```python
# Your solution here

import math
import scipy.stats as stats
mu = 60
sigma = 30
n=36
x_bar = 75
z = (x_bar - mu)/(sigma/math.sqrt(n))
p = 1 - stats.norm.cdf(z)

p,z
```




    (0.0013498980316301035, 3.0)




```python
# Interpret the results in terms of p-value obtained

# with p value less than 0.05 , we can reject the null hypothesis and say that time to rent a car
# is significantly more than what company claims. 
```

## Exercise 2

Twenty five students complete a preparation program for taking the SAT test.  Here are the SAT scores from the 25 students who completed  program:

``
434 694 457 534 720 400 484 478 610 641 425 636 454
514 563 370 499 640 501 625 612 471 598 509 531
``

<img src="http://falearningsolutions.com/wp-content/uploads/2015/09/FAcogtrain71FBimage.jpg" width=400>

We know that the population average for SAT scores is 500 with a standard deviation of 100.

The question is, are these students’ SAT scores significantly greater than a population mean? 

*Note that the the maker of the SAT prep program claims that it will increase (and not decrease) your SAT score.  So, you would be justified in conducting a one-directional test. (alpha = .05).*




```python
# State your hypotheses 


# Ha : there is an increase in grades after program
# Ho : there is no incerase in grade 
```


```python
# Give your solution here 

import numpy as np 
x = np.array([434, 694, 457, 534, 720, 400, 484, 478, 610, 641, 425, 636, 454,
514, 563, 370, 499, 640, 501, 625, 612, 471, 598, 509, 531])
x_bar = x.mean()
n = len(x)
mu = 500
sigma = 100
z = (x_bar - mu)/(sigma/math.sqrt(n))
p = 1 - stats.norm.cdf(z)
p,z

# p = 0.03593031911292577, z = 1.8
```




    (0.03593031911292577, 1.8)




```python
# Interpret the results in terms of p-value obtained

# The p value is less than tha alpha so we can colculde that:
# the training has a SIGNIFICANT effect on the SAT outcome. 
```

## Summary

In this lesson, we conducted a couple of simple tests comparing sample and population means, in an attempt to reject our null hypotheses. This provides you with a strong foundation to move ahead with more advanced tests and approaches in statistics. 
