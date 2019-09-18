[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)



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
from scipy import stats 

from cumulative import *
```


```python
# percentilerank = percent out of 100. Ex: 80th percentile
# percentile = score/value
```


```python
# generate 1000 numbers from np.random.random --> this will generate numbers between 0 and 1
# plot their PMF and CDF
# is the distribution uniform?

rand_list = np.random.random(size=1000)
```


```python
# plot PMF
rand_pmf = {}
rand_hist = {}
n = 1000 

# generate a 'histogram'
for value in rand_list:
    rand_hist[value] = rand_hist.get(value, 0) + 1  # .get() the same is dict[key] except that if the 
                                                    # key does not exist, the output is None

# using the histogram, get the pmf
for value, freq in rand_hist.items():
    rand_pmf[value] = freq / n
    
# pmf = thinkstats2.Pmf(rand_list)
# thinkplot.Pmf(pmf, linewidth=0.1)
# thinkplot.Config(xlabel='Random variate', ylabel='PMF')
```


```python
plt.step(list(rand_pmf.keys()), list(rand_pmf.values()), where='post')
```




    [<matplotlib.lines.Line2D at 0x1a19360250>]




![png](output_4_1.png)



```python
# this is showing us that the probability is uniform
# every number has an equal chance of being chosen
```


```python
# plot CDF
# what we want is.. value : percentilerank
rand_cdf = {}
rand_list.sort()

# list of percentileranks corresponding to each value
cdf_percentilerank_list = [stats.percentileofscore(rand_list, value) for value in rand_list] 

i = 0 # counter to iterate through each percentilerank in the above list
for value in rand_list:
    rand_cdf[value] = cdf_percentilerank_list[i] / 100 # divide by 100 to get the range fomr 0 to 1
    
    i += 1
    
```


```python
plt.step(list(rand_cdf.keys()), list(rand_cdf.values()), where='post')
```




    [<matplotlib.lines.Line2D at 0x1a16dab7d0>]




![png](output_7_1.png)



```python
# the cdf is uniform. as the values get higher, its percentile rank also increases
```
