[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

```
resp = nsfg.ReadFemResp()
pmf_actual = thinkstats2.Pmf(resp.numkdhh, label='actual')
pmf_biased = pmf_actual.Copy(label='biased')
for i, p in pmf_biased.Items():
    pmf_biased.Mult(i, i)    
pmf_biased.Normalize()

thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf_actual, pmf_biased])
thinkplot.Config(xlabel='Number of children (under 18)', ylabel='PMF')

print('Biased mean', pmf_biased.Mean())
print('Actual mean', pmf_actual.Mean())
```

From the actual 
