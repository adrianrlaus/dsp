[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)




```python
import thinkstats2 as thinkstats
import thinkplot
import nsfg
import first

import pandas as pd
import numpy as np
from matplotlib import pyplot as plt 
%matplotlib inline
from sklearn import preprocessing
import scipy

from analytic import *
```


```python
mu = 178 # mean = 178 cm
sigma = 7.7 # 1 std = 7.7 cm
normal_dist = scipy.stats.norm(loc=mu, scale=sigma) # the distribution we are looking at
type(normal_dist) 
```




    scipy.stats._distn_infrastructure.rv_frozen




```python
# just to verify the mean and standard deviation that we inputted 
# should match the mu and sigma above

normal_dist.mean(), normal_dist.std()
```




    (178.0, 7.7)




```python
# evaluate the distribution's CDF at a value. in this case 1 std below the mean
# 1 std below the mean is the mean - std, which is mu - sigma
normal_dist.cdf(mu - sigma)
```




    0.1586552539314574




```python
# so about 15.8% of people are more than 1 std below the mean
# think of it as percentileranks. there are 15.8% of people below 1 std from the mean
```


```python
# how many people are between 5'10" and 6'1". 177.8 Centimeters and 185.4
# we are using the 'norm' distribution bc according to the prompt, it is roughly normal
# below will give us the percentileranks(percentages) of people at 5'10" and 6'1"
cdf_510 = scipy.stats.norm.cdf(177.8, loc=mu, scale=sigma)
cdf_61 = scipy.stats.norm.cdf(185.4, loc=mu, scale=sigma)

# to ge the number of people between that range of heights, subtract
diff = cdf_61 - cdf_510

cdf_510, cdf_61, diff
```




    (0.48963902786483265, 0.8317337108107857, 0.3420946829459531)




```python
# so there are 48.9% of people 5'10" or below
# 83.1% of people 6'1" or below
# there are 34.2% of people between 5'10" and 6'1"
```


```python

```
