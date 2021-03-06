[Think Stats Chapter 8 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2009.html#toc77) (scoring)

```
def Simulate(n, iters=1000):
    lam = 2
    Ls = []
    for _ in range(iters):
        vals = np.random.exponential(1/lam, n)
        L = 1 / np.mean(vals)
        Ls.append(L)
    cdf = thinkstats2.Cdf(Ls)
    thinkplot.Cdf(cdf, label=n)
    thinkplot.Config(xlabel='L',
                    ylabel='CDF',
                    legend=True)
    thinkplot.Vlines([cdf.Percentile(5), cdf.Percentile(95)], 0, 1, linewidth=2)
    print('SE(L)', RMSE(Ls, lam))
    print('CI(L)', cdf.Percentile(5), cdf.Percentile(95)) 

Simulate(10)
```
```
SE(L) 0.806767119533259
CI(L) 1.2787201893441824 3.7027434543496995
```

![alt text](https://github.com/LKchemposer/dsp/blob/master/img/SE_vs_L_expo.png)

```
def SimulateSE(n, iters=1000):
    lam = 2
    Ls = []
    for _ in range(iters):
        vals = np.random.exponential(1/lam, n)
        L = 1 / np.mean(vals)
        Ls.append(L)
    return RMSE(Ls, lam)

for i in range(4, 21, 2):
    thinkplot.Scatter(i, SimulateSE(i), alpha=1)
    thinkplot.Config(xlabel='n',
                ylabel='SE',
                legend=False)
```

![alt text](https://github.com/LKchemposer/dsp/blob/master/img/SE_vs_n_expo.png)

SE and CI are `0.806767119533259` and 2.5, respectively. SE decreases as sample size increases, which makes sense because the more samples there are in each simulation, the smaller the variability from the assumed population's mean.
