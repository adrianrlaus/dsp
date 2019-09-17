[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

import thinkstats2 as thinkstats
import thinkplot
import pandas as pd
import numpy as np
import matplotlib as plt 
%matplotlib inline

from first import * # code made from the first chapter

def CohensD(group1, group2):
    
    n1, n2 = len(group1), len(group2)
    var1 = group1.var()
    var2 = group2.var()
    
    var_tot = (n1 * var1 + n2 * var2) / (n1 + n2)
    
    std = math.sqrt(var_tot)
    
    d = (group1.mean() - group2.mean()) / std # where std is 'pooled standard deviation'
    
    return d
    
preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1]

first_babies = live[live.birthord == 1]
other_babies = live[live.birthord != 1]

CohensD(first_babies['totalwgt_lb'], other_babies['totalwgt_lb'])

other_babies['totalwgt_lb'].mean() - first_babies['totalwgt_lb'].mean()

# so other babies are 0.125 pounds heavier than first babies.
# not much a difference
# also the Cohen's D is negative. what does this mean? this means that the effect lowers the mean.
# there is a lower difference when compared to pregnacy length
