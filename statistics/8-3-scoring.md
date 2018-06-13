[Think Stats Chapter 8 Exercise 3](http://greenteapress.com/thinkstats2/html/thinkstats2009.html#toc77)

```
def SimulateGame(lam): #existing code
    goals = 0
    t = 0
    while True:
        time_between_goals = random.expovariate(lam)
        t += time_between_goals
        if t > 1:
            break
        goals += 1

    L = goals
    return L
    
def GoalRate(lam, n_g=10000):
    lams = []
    for i in range(n_g):
        lams.append(SimulateGame(lam))
    cdf = thinkstats2.Cdf(lams)
    thinkplot.Cdf(cdf, label=lam)
    thinkplot.Vlines([cdf.Percentile(5), cdf.Percentile(95)], 0, 1, linewidth=2)
    thinkplot.Config(xlabel='λ (goals per game)',
                    ylabel='CDF',
                    legend=True)
    print('MSE', MeanError(lams, lam))
    print('SE/RMSE', RMSE(lams, lam))
    print('CI', cdf.Percentile(95) - cdf.Percentile(5))

GoalRate(10)
```

![alt text](https://github.com/LKchemposer/dsp/blob/master/img/CDF_game_sims.png)

```
def GR_SECI(lam, n_g=10000):
    lams = []
    for i in range(n_g):
        lams.append(SimulateGame(lam))
    SE = RMSE(lams, lam)
    cdf = thinkstats2.Cdf(lams)
    CI = cdf.Percentile(95)-cdf.Percentile(5)
    return SE, CI

for i in range(1, 16):
    thinkplot.Scatter(i, GR_SECI(i)[0], alpha=1)
    thinkplot.Config(xlabel='λ (goals per game)',
                    ylabel='SE (goals per game)',
                    legend=False)
```

![alt text](https://github.com/LKchemposer/dsp/blob/master/img/SE_vs_lam_game_sims.png)

```
for i in range(1, 16):
    thinkplot.Scatter(i, GR_SECI(i)[1], alpha=1)
    thinkplot.Config(xlabel='λ (goals per game)',
                    ylabel='CI (goals per game)',
                    legend=False)
```

![alt text](https://github.com/LKchemposer/dsp/blob/master/img/CI_vs_lam_game_sims.png)
