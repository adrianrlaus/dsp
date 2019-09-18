[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)




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

from probability import *
```


```python
resp = nsfg.ReadFemResp() # creates df of the female responses
```


```python
# use the variable 'NUMKDHH' to make the actual distribution for the number of children under 18
# then compute the biased distribution
# plot actual vs biased and compute means 
```


```python
resp['numkdhh'].value_counts()
```




    0    3563
    1    1636
    2    1500
    3     666
    4     196
    5      82
    Name: numkdhh, dtype: int64




```python
kids_hist = plt.hist(resp['numkdhh'], align='mid')
```


![png](output_4_0.png)



```python
kids_freq = resp['numkdhh'].value_counts().to_dict()
kids_freq
```




    {0: 3563, 1: 1636, 2: 1500, 3: 666, 4: 196, 5: 82}




```python
n = len(resp['numkdhh']) # number of responses for children in the household. Total Sample Size
n
```




    7643




```python
kids_pmf = {}

for kids, freq in kids_freq.items(): # the .items() allows you to go through the keys and values
    kids_pmf[kids] = freq / n

kids_pmf
```




    {0: 0.46617820227659296,
     1: 0.21405207379301322,
     2: 0.19625801386889966,
     3: 0.08713855815779144,
     4: 0.025644380478869553,
     5: 0.01072877142483318}




```python
# step-wise function. needed to convert the keys, values of the dict to a list to run
# where='post' dictates where the 'step' will start

plt.step(list(kids_pmf.keys()), list(kids_pmf.values()), where='post')
# need to learn how to add labels
# this is the 'actual' distribution
```




    [<matplotlib.lines.Line2D at 0x1a28d3a590>]




![png](output_8_1.png)



```python
# now get the 'biased' distribution. Ex: families with 0 kids should not be able to 
# respond b/c we are asking the 'kids' how many kids there are in their family
kids_pmf_bias = {}

for kids, probability in kids_pmf.items():
    kids_pmf_bias[kids] = probability * kids

# the sum is no longer 1. need to normalize. we use sklearn here
# Normalize
normalized_values = [probability / sum(kids_pmf_bias.values()) for probability in kids_pmf_bias.values()]

# add the normalized values to the dictionary
i = 0
for kids in kids_pmf_bias.keys():
    kids_pmf_bias[kids] = normalized_values[i]
    i += 1

kids_pmf_bias
```




    {0: 0.0,
     1: 0.20899335717935616,
     2: 0.38323965252938175,
     3: 0.25523760858456823,
     4: 0.10015329586101175,
     5: 0.052376085845682166}




```python
# step-wise plot of the 'biased distribution'
plt.step(list(kids_pmf_bias.keys()), list(kids_pmf_bias.values()), where='post')
```




    [<matplotlib.lines.Line2D at 0x1a289b4c50>]




![png](output_10_1.png)



```python
# compare both step-wise functions

plt.step(list(kids_pmf_bias.keys()), list(kids_pmf_bias.values()), where='post', label='biased')
plt.step(list(kids_pmf.keys()), list(kids_pmf.values()), where='post', label='un-biased')

plt.legend(title='Biased vs Un-biased Distributions')
```




    <matplotlib.legend.Legend at 0x1a28f83c90>




![png](output_11_1.png)



```python
# un-biased mean
resp['numkdhh'].mean()
```




    1.024205155043831




```python
# biased mean
# to get biased mean, i am multiplying the number of kids in each household by the probability that this occurs

prob_list = [kids * probability for kids, probability in kids_pmf_bias.items()]
   
sum(prob_list)
```




    2.403679100664282




```python

```
