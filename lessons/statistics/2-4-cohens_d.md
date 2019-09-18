

```python
import thinkstats2 as thinkstats
import thinkplot
import pandas as pd
import numpy as np
import matplotlib as plt 
%matplotlib inline

from first import * # code made from the first chapter
```


```python
preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1]
```


```python
preg
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>caseid</th>
      <th>pregordr</th>
      <th>howpreg_n</th>
      <th>howpreg_p</th>
      <th>moscurrp</th>
      <th>nowprgdk</th>
      <th>pregend1</th>
      <th>pregend2</th>
      <th>nbrnaliv</th>
      <th>multbrth</th>
      <th>...</th>
      <th>laborfor_i</th>
      <th>religion_i</th>
      <th>metro_i</th>
      <th>basewgt</th>
      <th>adj_mod_basewgt</th>
      <th>finalwgt</th>
      <th>secu_p</th>
      <th>sest</th>
      <th>cmintvw</th>
      <th>totalwgt_lb</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3410.389399</td>
      <td>3869.349602</td>
      <td>6448.271112</td>
      <td>2</td>
      <td>9</td>
      <td>NaN</td>
      <td>8.8125</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3410.389399</td>
      <td>3869.349602</td>
      <td>6448.271112</td>
      <td>2</td>
      <td>9</td>
      <td>NaN</td>
      <td>7.8750</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>5.0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>7226.301740</td>
      <td>8567.549110</td>
      <td>12999.542264</td>
      <td>2</td>
      <td>12</td>
      <td>NaN</td>
      <td>9.1250</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>7226.301740</td>
      <td>8567.549110</td>
      <td>12999.542264</td>
      <td>2</td>
      <td>12</td>
      <td>NaN</td>
      <td>7.0000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>7226.301740</td>
      <td>8567.549110</td>
      <td>12999.542264</td>
      <td>2</td>
      <td>12</td>
      <td>NaN</td>
      <td>6.1875</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>4870.926435</td>
      <td>5325.196999</td>
      <td>8874.440799</td>
      <td>1</td>
      <td>23</td>
      <td>NaN</td>
      <td>8.5625</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>4870.926435</td>
      <td>5325.196999</td>
      <td>8874.440799</td>
      <td>1</td>
      <td>23</td>
      <td>NaN</td>
      <td>9.5625</td>
    </tr>
    <tr>
      <th>7</th>
      <td>6</td>
      <td>3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>4870.926435</td>
      <td>5325.196999</td>
      <td>8874.440799</td>
      <td>1</td>
      <td>23</td>
      <td>NaN</td>
      <td>8.3750</td>
    </tr>
    <tr>
      <th>8</th>
      <td>7</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3409.579565</td>
      <td>3787.539000</td>
      <td>6911.879921</td>
      <td>2</td>
      <td>14</td>
      <td>NaN</td>
      <td>7.5625</td>
    </tr>
    <tr>
      <th>9</th>
      <td>7</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3409.579565</td>
      <td>3787.539000</td>
      <td>6911.879921</td>
      <td>2</td>
      <td>14</td>
      <td>NaN</td>
      <td>6.6250</td>
    </tr>
    <tr>
      <th>10</th>
      <td>12</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3612.781968</td>
      <td>4146.013572</td>
      <td>6909.331618</td>
      <td>1</td>
      <td>31</td>
      <td>NaN</td>
      <td>7.8125</td>
    </tr>
    <tr>
      <th>11</th>
      <td>14</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2418.069494</td>
      <td>2810.302771</td>
      <td>3039.904507</td>
      <td>2</td>
      <td>56</td>
      <td>NaN</td>
      <td>7.0000</td>
    </tr>
    <tr>
      <th>12</th>
      <td>14</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2418.069494</td>
      <td>2810.302771</td>
      <td>3039.904507</td>
      <td>2</td>
      <td>56</td>
      <td>NaN</td>
      <td>4.0000</td>
    </tr>
    <tr>
      <th>13</th>
      <td>14</td>
      <td>3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2418.069494</td>
      <td>2810.302771</td>
      <td>3039.904507</td>
      <td>2</td>
      <td>56</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>14</th>
      <td>15</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1667.816099</td>
      <td>3200.862017</td>
      <td>5553.495599</td>
      <td>1</td>
      <td>33</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>15</th>
      <td>15</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1667.816099</td>
      <td>3200.862017</td>
      <td>5553.495599</td>
      <td>1</td>
      <td>33</td>
      <td>NaN</td>
      <td>7.6875</td>
    </tr>
    <tr>
      <th>16</th>
      <td>15</td>
      <td>3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1667.816099</td>
      <td>3200.862017</td>
      <td>5553.495599</td>
      <td>1</td>
      <td>33</td>
      <td>NaN</td>
      <td>7.5000</td>
    </tr>
    <tr>
      <th>17</th>
      <td>18</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2957.257457</td>
      <td>3404.403067</td>
      <td>4153.371741</td>
      <td>2</td>
      <td>14</td>
      <td>NaN</td>
      <td>6.3125</td>
    </tr>
    <tr>
      <th>18</th>
      <td>18</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2957.257457</td>
      <td>3404.403067</td>
      <td>4153.371741</td>
      <td>2</td>
      <td>14</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>19</th>
      <td>21</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3408.342437</td>
      <td>3965.763949</td>
      <td>7237.122630</td>
      <td>1</td>
      <td>48</td>
      <td>NaN</td>
      <td>8.7500</td>
    </tr>
    <tr>
      <th>20</th>
      <td>21</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3408.342437</td>
      <td>3965.763949</td>
      <td>7237.122630</td>
      <td>1</td>
      <td>48</td>
      <td>NaN</td>
      <td>8.1875</td>
    </tr>
    <tr>
      <th>21</th>
      <td>23</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>6210.373020</td>
      <td>8120.841310</td>
      <td>13533.382043</td>
      <td>2</td>
      <td>64</td>
      <td>NaN</td>
      <td>5.5625</td>
    </tr>
    <tr>
      <th>22</th>
      <td>23</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>6210.373020</td>
      <td>8120.841310</td>
      <td>13533.382043</td>
      <td>2</td>
      <td>64</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>23</th>
      <td>24</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3409.573258</td>
      <td>4068.628645</td>
      <td>7424.840414</td>
      <td>1</td>
      <td>27</td>
      <td>NaN</td>
      <td>6.7500</td>
    </tr>
    <tr>
      <th>24</th>
      <td>24</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3409.573258</td>
      <td>4068.628645</td>
      <td>7424.840414</td>
      <td>1</td>
      <td>27</td>
      <td>NaN</td>
      <td>7.3750</td>
    </tr>
    <tr>
      <th>25</th>
      <td>24</td>
      <td>3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3409.573258</td>
      <td>4068.628645</td>
      <td>7424.840414</td>
      <td>1</td>
      <td>27</td>
      <td>NaN</td>
      <td>6.8125</td>
    </tr>
    <tr>
      <th>26</th>
      <td>28</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3407.794208</td>
      <td>3808.343516</td>
      <td>6949.846082</td>
      <td>2</td>
      <td>57</td>
      <td>NaN</td>
      <td>8.1250</td>
    </tr>
    <tr>
      <th>27</th>
      <td>31</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3405.679025</td>
      <td>4272.084519</td>
      <td>5211.943113</td>
      <td>1</td>
      <td>2</td>
      <td>NaN</td>
      <td>7.1250</td>
    </tr>
    <tr>
      <th>28</th>
      <td>31</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3405.679025</td>
      <td>4272.084519</td>
      <td>5211.943113</td>
      <td>1</td>
      <td>2</td>
      <td>NaN</td>
      <td>6.0625</td>
    </tr>
    <tr>
      <th>29</th>
      <td>31</td>
      <td>3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3405.679025</td>
      <td>4272.084519</td>
      <td>5211.943113</td>
      <td>1</td>
      <td>2</td>
      <td>NaN</td>
      <td>7.4375</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>13563</th>
      <td>12547</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3453.545517</td>
      <td>6628.022524</td>
      <td>11499.619080</td>
      <td>1</td>
      <td>52</td>
      <td>NaN</td>
      <td>7.6875</td>
    </tr>
    <tr>
      <th>13564</th>
      <td>12547</td>
      <td>3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3453.545517</td>
      <td>6628.022524</td>
      <td>11499.619080</td>
      <td>1</td>
      <td>52</td>
      <td>NaN</td>
      <td>7.6250</td>
    </tr>
    <tr>
      <th>13565</th>
      <td>12550</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3080.452699</td>
      <td>3745.326058</td>
      <td>5268.550165</td>
      <td>1</td>
      <td>79</td>
      <td>NaN</td>
      <td>8.1250</td>
    </tr>
    <tr>
      <th>13566</th>
      <td>12551</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2418.538866</td>
      <td>3653.453268</td>
      <td>3951.940400</td>
      <td>2</td>
      <td>75</td>
      <td>NaN</td>
      <td>7.5000</td>
    </tr>
    <tr>
      <th>13567</th>
      <td>12554</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1914.676604</td>
      <td>2177.957240</td>
      <td>2764.045534</td>
      <td>2</td>
      <td>75</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13568</th>
      <td>12554</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1914.676604</td>
      <td>2177.957240</td>
      <td>2764.045534</td>
      <td>2</td>
      <td>75</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13569</th>
      <td>12556</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2474.619764</td>
      <td>3250.573384</td>
      <td>3965.699528</td>
      <td>1</td>
      <td>44</td>
      <td>NaN</td>
      <td>5.8125</td>
    </tr>
    <tr>
      <th>13570</th>
      <td>12556</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2474.619764</td>
      <td>3250.573384</td>
      <td>3965.699528</td>
      <td>1</td>
      <td>44</td>
      <td>NaN</td>
      <td>6.6875</td>
    </tr>
    <tr>
      <th>13571</th>
      <td>12556</td>
      <td>3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2474.619764</td>
      <td>3250.573384</td>
      <td>3965.699528</td>
      <td>1</td>
      <td>44</td>
      <td>NaN</td>
      <td>6.0000</td>
    </tr>
    <tr>
      <th>13572</th>
      <td>12556</td>
      <td>4</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2474.619764</td>
      <td>3250.573384</td>
      <td>3965.699528</td>
      <td>1</td>
      <td>44</td>
      <td>NaN</td>
      <td>5.8125</td>
    </tr>
    <tr>
      <th>13573</th>
      <td>12561</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2418.089703</td>
      <td>2698.650781</td>
      <td>4497.301527</td>
      <td>1</td>
      <td>10</td>
      <td>NaN</td>
      <td>6.5625</td>
    </tr>
    <tr>
      <th>13574</th>
      <td>12561</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2418.089703</td>
      <td>2698.650781</td>
      <td>4497.301527</td>
      <td>1</td>
      <td>10</td>
      <td>NaN</td>
      <td>6.1250</td>
    </tr>
    <tr>
      <th>13575</th>
      <td>12564</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1820.850938</td>
      <td>2129.214067</td>
      <td>2768.191208</td>
      <td>2</td>
      <td>44</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13576</th>
      <td>12565</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3195.641221</td>
      <td>3834.241709</td>
      <td>6652.409365</td>
      <td>1</td>
      <td>78</td>
      <td>NaN</td>
      <td>6.4375</td>
    </tr>
    <tr>
      <th>13577</th>
      <td>12565</td>
      <td>2</td>
      <td>35.0</td>
      <td>1.0</td>
      <td>8.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3195.641221</td>
      <td>3834.241709</td>
      <td>6652.409365</td>
      <td>1</td>
      <td>78</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13578</th>
      <td>12566</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2080.317155</td>
      <td>2422.820274</td>
      <td>2627.548587</td>
      <td>2</td>
      <td>2</td>
      <td>NaN</td>
      <td>6.0000</td>
    </tr>
    <tr>
      <th>13579</th>
      <td>12566</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2080.317155</td>
      <td>2422.820274</td>
      <td>2627.548587</td>
      <td>2</td>
      <td>2</td>
      <td>NaN</td>
      <td>7.0000</td>
    </tr>
    <tr>
      <th>13580</th>
      <td>12568</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2734.687353</td>
      <td>4258.980140</td>
      <td>7772.212858</td>
      <td>2</td>
      <td>28</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13581</th>
      <td>12568</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2734.687353</td>
      <td>4258.980140</td>
      <td>7772.212858</td>
      <td>2</td>
      <td>28</td>
      <td>NaN</td>
      <td>6.3750</td>
    </tr>
    <tr>
      <th>13582</th>
      <td>12568</td>
      <td>3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2734.687353</td>
      <td>4258.980140</td>
      <td>7772.212858</td>
      <td>2</td>
      <td>28</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13583</th>
      <td>12569</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2580.967613</td>
      <td>2925.167116</td>
      <td>5075.164946</td>
      <td>2</td>
      <td>61</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13584</th>
      <td>12569</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2580.967613</td>
      <td>2925.167116</td>
      <td>5075.164946</td>
      <td>2</td>
      <td>61</td>
      <td>NaN</td>
      <td>6.3750</td>
    </tr>
    <tr>
      <th>13585</th>
      <td>12570</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>5181.311509</td>
      <td>6205.829154</td>
      <td>11325.017623</td>
      <td>2</td>
      <td>40</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13586</th>
      <td>12570</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>5181.311509</td>
      <td>6205.829154</td>
      <td>11325.017623</td>
      <td>2</td>
      <td>40</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13587</th>
      <td>12570</td>
      <td>3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>5181.311509</td>
      <td>6205.829154</td>
      <td>11325.017623</td>
      <td>2</td>
      <td>40</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13588</th>
      <td>12571</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>4670.540953</td>
      <td>5795.692880</td>
      <td>6269.200989</td>
      <td>1</td>
      <td>78</td>
      <td>NaN</td>
      <td>6.1875</td>
    </tr>
    <tr>
      <th>13589</th>
      <td>12571</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>4670.540953</td>
      <td>5795.692880</td>
      <td>6269.200989</td>
      <td>1</td>
      <td>78</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13590</th>
      <td>12571</td>
      <td>3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>4670.540953</td>
      <td>5795.692880</td>
      <td>6269.200989</td>
      <td>1</td>
      <td>78</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13591</th>
      <td>12571</td>
      <td>4</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>4670.540953</td>
      <td>5795.692880</td>
      <td>6269.200989</td>
      <td>1</td>
      <td>78</td>
      <td>NaN</td>
      <td>7.5000</td>
    </tr>
    <tr>
      <th>13592</th>
      <td>12571</td>
      <td>5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>4670.540953</td>
      <td>5795.692880</td>
      <td>6269.200989</td>
      <td>1</td>
      <td>78</td>
      <td>NaN</td>
      <td>7.5000</td>
    </tr>
  </tbody>
</table>
<p>13593 rows × 244 columns</p>
</div>




```python
hist = thinkstats2.Hist(live.birthwgt_lb, label='birthwgt_lb')
thinkplot.Hist(hist)
thinkplot.Show(xlabel='pounds', ylabel='frequency')
```


![png](output_3_0.png)



    <Figure size 576x432 with 0 Axes>



```python
for weeks, freq in hist.Smallest(10):
    print(weeks, freq)
```

    0.0 8
    1.0 40
    2.0 53
    3.0 98
    4.0 229
    5.0 697
    6.0 2223
    7.0 3049
    8.0 1889
    9.0 623



```python
firsts = live[live.birthord == 1]
others = live[live.birthord != 1]

first_hist = thinkstats2.Hist(firsts.prglngth)
other_hist = thinkstats2.Hist(others.prglngth)
```


```python
width = 0.45
thinkplot.PrePlot(2)
thinkplot.Hist(first_hist, align='right', width=width)
thinkplot.Hist(other_hist, align='left', width=width)
thinkplot.Show(xlabel='weeks', ylabel='frequency',
               xlim=[27, 46])
```


![png](output_6_0.png)



    <Figure size 576x432 with 0 Axes>



```python
mean = live.prglngth.mean()
var = live.prglngth.var()
std = live.prglngth.std()
```


```python
print(mean, var, std)
```

    38.56055968517709 7.302662067826851 2.702343810070593



```python
def CohenEffectSize(group1, group2):
    diff = group1.mean() - group2.mean()

    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)

    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / math.sqrt(pooled_var)
    return d
```


```python
def CohensD(group1, group2):
    
    n1, n2 = len(group1), len(group2)
    var1 = group1.var()
    var2 = group2.var()
    
    var_tot = (n1 * var1 + n2 * var2) / (n1 + n2)
    
    std = math.sqrt(var_tot)
    
    d = (group1.mean() - group2.mean()) / std # where std is 'pooled standard deviation'
    
    return d
```


```python
CohensD(firsts['prglngth'], others['prglngth'])
```




    0.028879044654449883




```python
# ok so the code i made was correct, as well as the variable i chose. 
```


```python
"""Chapter 2 Exercise 4

Using the variable totalwgt_lb, investigate whether first babies are lighter or heavier than others. 
Compute Cohen’s d to quantify the difference between the groups. 
How does it compare to the difference in pregnancy length?"""
```




    'Chapter 2 Exercise 4\n\nUsing the variable totalwgt_lb, investigate whether first babies are lighter or heavier than others. \nCompute Cohen’s d to quantify the difference between the groups. \nHow does it compare to the difference in pregnancy length?'




```python
# use the variable name totalwgt_lb which is the last column
# get the weight of first babies, then the weight of others
# are first babies heavier than others?
# compute Cohen's D 
# how does is compare to pregnancy length? does it have a larger 'effect size'?


```


```python
preg.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>caseid</th>
      <th>pregordr</th>
      <th>howpreg_n</th>
      <th>howpreg_p</th>
      <th>moscurrp</th>
      <th>nowprgdk</th>
      <th>pregend1</th>
      <th>pregend2</th>
      <th>nbrnaliv</th>
      <th>multbrth</th>
      <th>...</th>
      <th>laborfor_i</th>
      <th>religion_i</th>
      <th>metro_i</th>
      <th>basewgt</th>
      <th>adj_mod_basewgt</th>
      <th>finalwgt</th>
      <th>secu_p</th>
      <th>sest</th>
      <th>cmintvw</th>
      <th>totalwgt_lb</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3410.389399</td>
      <td>3869.349602</td>
      <td>6448.271112</td>
      <td>2</td>
      <td>9</td>
      <td>NaN</td>
      <td>8.8125</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3410.389399</td>
      <td>3869.349602</td>
      <td>6448.271112</td>
      <td>2</td>
      <td>9</td>
      <td>NaN</td>
      <td>7.8750</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>5.0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>7226.301740</td>
      <td>8567.549110</td>
      <td>12999.542264</td>
      <td>2</td>
      <td>12</td>
      <td>NaN</td>
      <td>9.1250</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>7226.301740</td>
      <td>8567.549110</td>
      <td>12999.542264</td>
      <td>2</td>
      <td>12</td>
      <td>NaN</td>
      <td>7.0000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>7226.301740</td>
      <td>8567.549110</td>
      <td>12999.542264</td>
      <td>2</td>
      <td>12</td>
      <td>NaN</td>
      <td>6.1875</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 244 columns</p>
</div>




```python
live.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>caseid</th>
      <th>pregordr</th>
      <th>howpreg_n</th>
      <th>howpreg_p</th>
      <th>moscurrp</th>
      <th>nowprgdk</th>
      <th>pregend1</th>
      <th>pregend2</th>
      <th>nbrnaliv</th>
      <th>multbrth</th>
      <th>...</th>
      <th>laborfor_i</th>
      <th>religion_i</th>
      <th>metro_i</th>
      <th>basewgt</th>
      <th>adj_mod_basewgt</th>
      <th>finalwgt</th>
      <th>secu_p</th>
      <th>sest</th>
      <th>cmintvw</th>
      <th>totalwgt_lb</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3410.389399</td>
      <td>3869.349602</td>
      <td>6448.271112</td>
      <td>2</td>
      <td>9</td>
      <td>NaN</td>
      <td>8.8125</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3410.389399</td>
      <td>3869.349602</td>
      <td>6448.271112</td>
      <td>2</td>
      <td>9</td>
      <td>NaN</td>
      <td>7.8750</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>5.0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>7226.301740</td>
      <td>8567.549110</td>
      <td>12999.542264</td>
      <td>2</td>
      <td>12</td>
      <td>NaN</td>
      <td>9.1250</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>7226.301740</td>
      <td>8567.549110</td>
      <td>12999.542264</td>
      <td>2</td>
      <td>12</td>
      <td>NaN</td>
      <td>7.0000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>7226.301740</td>
      <td>8567.549110</td>
      <td>12999.542264</td>
      <td>2</td>
      <td>12</td>
      <td>NaN</td>
      <td>6.1875</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 244 columns</p>
</div>




```python
live['totalwgt_lb'].head()
```




    0    8.8125
    1    7.8750
    2    9.1250
    3    7.0000
    4    6.1875
    Name: totalwgt_lb, dtype: float64




```python
first_babies = live[live.birthord == 1]
other_babies = live[live.birthord != 1]
```


```python
first_babies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>caseid</th>
      <th>pregordr</th>
      <th>howpreg_n</th>
      <th>howpreg_p</th>
      <th>moscurrp</th>
      <th>nowprgdk</th>
      <th>pregend1</th>
      <th>pregend2</th>
      <th>nbrnaliv</th>
      <th>multbrth</th>
      <th>...</th>
      <th>laborfor_i</th>
      <th>religion_i</th>
      <th>metro_i</th>
      <th>basewgt</th>
      <th>adj_mod_basewgt</th>
      <th>finalwgt</th>
      <th>secu_p</th>
      <th>sest</th>
      <th>cmintvw</th>
      <th>totalwgt_lb</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3410.389399</td>
      <td>3869.349602</td>
      <td>6448.271112</td>
      <td>2</td>
      <td>9</td>
      <td>NaN</td>
      <td>8.8125</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>5.0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>7226.301740</td>
      <td>8567.549110</td>
      <td>12999.542264</td>
      <td>2</td>
      <td>12</td>
      <td>NaN</td>
      <td>9.1250</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>4870.926435</td>
      <td>5325.196999</td>
      <td>8874.440799</td>
      <td>1</td>
      <td>23</td>
      <td>NaN</td>
      <td>8.5625</td>
    </tr>
    <tr>
      <th>8</th>
      <td>7</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3409.579565</td>
      <td>3787.539000</td>
      <td>6911.879921</td>
      <td>2</td>
      <td>14</td>
      <td>NaN</td>
      <td>7.5625</td>
    </tr>
    <tr>
      <th>10</th>
      <td>12</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3612.781968</td>
      <td>4146.013572</td>
      <td>6909.331618</td>
      <td>1</td>
      <td>31</td>
      <td>NaN</td>
      <td>7.8125</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 244 columns</p>
</div>




```python
other_babies.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>caseid</th>
      <th>pregordr</th>
      <th>howpreg_n</th>
      <th>howpreg_p</th>
      <th>moscurrp</th>
      <th>nowprgdk</th>
      <th>pregend1</th>
      <th>pregend2</th>
      <th>nbrnaliv</th>
      <th>multbrth</th>
      <th>...</th>
      <th>laborfor_i</th>
      <th>religion_i</th>
      <th>metro_i</th>
      <th>basewgt</th>
      <th>adj_mod_basewgt</th>
      <th>finalwgt</th>
      <th>secu_p</th>
      <th>sest</th>
      <th>cmintvw</th>
      <th>totalwgt_lb</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>3410.389399</td>
      <td>3869.349602</td>
      <td>6448.271112</td>
      <td>2</td>
      <td>9</td>
      <td>NaN</td>
      <td>7.8750</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>7226.301740</td>
      <td>8567.549110</td>
      <td>12999.542264</td>
      <td>2</td>
      <td>12</td>
      <td>NaN</td>
      <td>7.0000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>7226.301740</td>
      <td>8567.549110</td>
      <td>12999.542264</td>
      <td>2</td>
      <td>12</td>
      <td>NaN</td>
      <td>6.1875</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>4870.926435</td>
      <td>5325.196999</td>
      <td>8874.440799</td>
      <td>1</td>
      <td>23</td>
      <td>NaN</td>
      <td>9.5625</td>
    </tr>
    <tr>
      <th>7</th>
      <td>6</td>
      <td>3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>4870.926435</td>
      <td>5325.196999</td>
      <td>8874.440799</td>
      <td>1</td>
      <td>23</td>
      <td>NaN</td>
      <td>8.3750</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 244 columns</p>
</div>




```python
CohensD(first_babies['totalwgt_lb'], other_babies['totalwgt_lb'])
```




    -0.088672927072602




```python
CohenEffectSize(firsts['totalwgt_lb'], others['totalwgt_lb'])
```




    -0.088672927072602




```python
# answers are the same
```


```python
first_babies['totalwgt_lb'].mean()
```




    7.201094430437772




```python
other_babies['totalwgt_lb'].mean()
```




    7.325855614973262




```python
other_babies['totalwgt_lb'].mean() - first_babies['totalwgt_lb'].mean()
```




    0.12476118453549034




```python
# so other babies are 0.125 pounds heavier than first babies.
# not much a difference
# also the Cohen's D is negative. what does this mean? this means that the effect lowers the mean.
# there is a lower difference when compared to pregnacy length

```


```python
"""This file contains code for use with "Think Stats",
by Allen B. Downey, available from greenteapress.com

Copyright 2014 Allen B. Downey
License: GNU GPLv3 http://www.gnu.org/licenses/gpl.html
"""

from __future__ import print_function

import sys
from operator import itemgetter

import first
import thinkstats2


def Mode(hist):
    """Returns the value with the highest frequency.

    hist: Hist object

    returns: value from Hist
    """
    p, x = max([(p, x) for x, p in hist.Items()])
    return x


def AllModes(hist):
    """Returns value-freq pairs in decreasing order of frequency.

    hist: Hist object

    returns: iterator of value-freq pairs
    """
    return sorted(hist.Items(), key=itemgetter(1), reverse=True)


def WeightDifference(live, firsts, others):
    """Explore the difference in weight between first babies and others.

    live: DataFrame of all live births
    firsts: DataFrame of first babies
    others: DataFrame of others
    """
    mean0 = live.totalwgt_lb.mean()
    mean1 = firsts.totalwgt_lb.mean()
    mean2 = others.totalwgt_lb.mean()

    var1 = firsts.totalwgt_lb.var()
    var2 = others.totalwgt_lb.var()

    print('Mean')
    print('First babies', mean1)
    print('Others', mean2)

    print('Variance')
    print('First babies', var1)
    print('Others', var2)

    print('Difference in lbs', mean1 - mean2)
    print('Difference in oz', (mean1 - mean2) * 16)

    print('Difference relative to mean (%age points)',
          (mean1 - mean2) / mean0 * 100)

    d = thinkstats2.CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)
    print('Cohen d', d)


# def main(script):
#     """Tests the functions in this module.

#     script: string script name
#     """
#     live, firsts, others = first.MakeFrames()
#     hist = thinkstats2.Hist(live.prglngth)

#     # explore the weight difference between first babies and others
#     WeightDifference(live, firsts, others)

#     # test Mode
#     mode = Mode(hist)
#     print('Mode of preg length', mode)
#     assert(mode == 39)

#     # test AllModes
#     modes = AllModes(hist)
#     assert(modes[0][1] == 4693)

#     for value, freq in modes[:5]:
#         print(value, freq)

#     print('%s: All tests passed.' % script)


# if __name__ == '__main__':
#     main(*sys.argv)

```


```python
WeightDifference(live, firsts, others)
```

    Mean
    First babies 7.201094430437772
    Others 7.325855614973262
    Variance
    First babies 2.0180273009157768
    Others 1.9437810258964572
    Difference in lbs -0.12476118453549034
    Difference in oz -1.9961789525678455
    Difference relative to mean (%age points) -1.7171423678372415
    Cohen d -0.088672927072602



```python

```
