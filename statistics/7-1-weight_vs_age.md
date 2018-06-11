[Think Stats Chapter 7 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2008.html#toc70) (weight vs. age)

```
import first

live, firsts, others = first.MakeFrames()
live = live.dropna(subset=['agepreg', 'totalwgt_lb'])

age, wgt = live.agepreg, live.totalwgt_lb

thinkplot.Scatter(age, wgt, alpha=0.1, s=10)
thinkplot.Config(xlabel='Mother\'s age',
                ylabel='Birth weight (lb)')
```

![alt text](https://github.com/LKchemposer/dsp/blob/master/img/Weight_vs_age_scatter.png)

```
age_b = np.arange(10, 45, 2)
ind = np.digitize(live.agepreg, age_b)
age_g = live.groupby(ind)
age_m = [g.agepreg.mean() for i, g in age_g]
wgt_cdf = [thinkstats2.Cdf(g.totalwgt_lb) for i, g in age_g]
for i in [75, 50, 25]:
    percs = [cdf.Percentile(i) for cdf in wgt_cdf]
    thinkplot.Plot(age_m, percs, label=i)

thinkplot.Config(xlabel='Mother\'s age',
                ylabel='Birth weight (lb)',
                legend=True)
```

![alt text](https://github.com/LKchemposer/dsp/blob/master/img/Weight_vs_age_percentiles.png)

```
Corr(age, wgt), SpearmanCorr(age, wgt)
```

The sample's Pearson's and Spearman's correlations are `0.06883397035410906` and `0.09461004109658226`, respectively. Pearson's correlation suggests either (1) little/no correlation or (2) non-linear relationship between the mother's age and the child's birth weight. Spearman's correlation suggests a slightly stronger correlation.

On the scatter plot, the weight looks constant against the mother's age, densely populated around 6-8 lbs. The percentile plot (1) confirms the observed density, and (2) somewhat reveals the complicated correlation: a slight postive (linear) correlation for younger mothers (15 to 25 years) but the correlation falls off for older mother (> 25 years). Nonetheless, the difference in birth weight (< 0.5 lbs between 15- and 25-year-old mothers) should the correlation exists at all does not seem to be detectable or useful.

However, for the sake of practice, I pulled the data in which the mothers are within 15-25 years of age, and recalculated the correlations.

```
yg_mothers = live[(live['agepreg']<=25) & (live['agepreg']>=15)]
age, wgt = yg_mothers.agepreg, yg_mothers.totalwgt_lb

thinkplot.Scatter(age, wgt, alpha=0.1, s=10)
thinkplot.Config(xlabel='Mother\'s age',
                ylabel='Birth weight (lb)',
                legend=False)

Corr(age, wgt), SpearmanCorr(age, wgt)
```

![alt text](https://github.com/LKchemposer/dsp/blob/master/img/Weight_vs_age_scatter_youngmoms.png)

The new Pearson's and Spearman's correlations are `0.0767434753623417` and `0.07871592334924693`, respectively. They are in better agreement, still suggesting little to no correlation between the variables.
