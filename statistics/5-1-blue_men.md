[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

```
import scipy.stats

mu = 178
sig = 7.7
d = scipy.stats.norm(loc=mu, scale=sig)

six_one = 185.42
five_ten = 177.8
d.cdf(six_one)-d.cdf(five_ten)
```

The output `0.3427468376314737` shows that only 34% of the US male population is qualified to join the Blue Man Group.
