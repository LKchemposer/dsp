[Think Stats Chapter 6 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2007.html#toc60) (household income)

```
import thinkstats2
sample.mean(), Median(sample), Skewness(sample), PearsonMedianSkewness(sample)

cdf.Prob(sample.mean()) * 100

log_sample = InterpolateSample(income_df, log_upper=7.0)
sample = np.power(10, log_sample)
Skewness(sample), PearsonMedianSkewness(sample)
```

The sample's mean, median, sample's skewness, and Pearson's sknewness are `74278.7075311872`, `51226.45447894046`, `4.949920244429583`, and `0.7361258019141782`, respectively. The positive skewnesses confirm that the sample skews right. `66.0005879566872`% of the households report a below-the-mean income.

If the upperbound income of the interpolated sample were $10 million, the new sample's skewness and Pearson's skewness are `11.603690267537793` and `0.39156450927742087`, respectively, suggesting that the skewness is sensitive to the upperbound of the sample.
