[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

```
import numpy as np
import thinkstats2 as ts2
import thinkplot as tp

num = np.random.random(1000)
pmf = ts2.Pmf(num, label='PMF')
cdf = ts2.Cdf(num, label='CDF')

tp.Pmf(pmf)
tp.Config(xlabel='#', ylabel='PMF')
```

![alt text](https://github.com/LKchemposer/dsp/blob/master/img/PMF_random.png)

```
tp.Cdf(cdf)
tp.Config(xlabel='#', ylabel='CDF')
```

![alt text](https://github.com/LKchemposer/dsp/blob/master/img/CDF_random.png)

The PMF shows the distribution of the random number generator, and the CDF shows its cummulative distribution function. The PMF looks extremely dense (as it is uniform), peaks and valleys are not visible. The CDF, on the other hand, looks clean, and is almost perfectly linear, indicating that the distribution is indeed uniform.
