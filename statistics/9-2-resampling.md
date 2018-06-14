[Think Stats Chapter 9 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2010.html#toc90) (resampling)

```
class DiffMeansResample(DiffMeansPermute):
    
    def RunModel(self):
        pool_res = thinkstats2.Resample(self.pool)
        data = pool_res[:self.n], pool_res[self.n:]
        return data
    
live, firsts, others = first.MakeFrames()
lengths = firsts.prglngth.values, others.prglngth.values
weights = firsts.totalwgt_lb.values, others.totalwgt_lb.values

hypt_l = DiffMeansResample(lengths)
pval_l = hypt_l.PValue(iters=10000)
print('p-value (preg length)', pval_l)

hypt_w = DiffMeansResample(weights)
pval_w = hypt_w.PValue(iters=10000)
print('p-value (weight)', pval_w)
```
```
p-value (preg length) 0.1679
p-value (weight) 0.0
```

Compared to the p-values produced by `DiffMeansPermute` (0.17 and < 0.001 for pregnancy length and birth weight, respectively), the conclusions are not different. The difference in pregnancy lengths between first and non-first babies are not statistically significant, whereas that of birth weight is.
