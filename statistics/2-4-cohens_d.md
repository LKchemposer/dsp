[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

```
preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1]
f_lb = live[live.birthord == 1].totalwgt_lb
o_lb = live[live.birthord != 1].totalwgt_lb

def CohenEffectSize(group1, group2):
    diff = group1.mean() - group2.mean()
    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)
    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / np.sqrt(pooled_var)
    return d

CohenEffectSize(f_lb, o_lb)
```
The Cohen's D of `-0.088672927072602` indicates that first baby is less than 0.1 pound lighter than non-first babies. The difference is thereby not significant, considering the fact that babies are typically 7 lbs; a difference in 0.1 pound correponds to only 1.4% of the baby's total weight.
