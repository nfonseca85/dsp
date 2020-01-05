[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

# Ex 2.4


```python
import first
import nsfg
import thinkstats2
```


```python
preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1]

firsts = live[live.birthord == 1]
others = live[live.birthord != 1]
```


```python
preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1]

firsts = live[live.birthord == 1]
others = live[live.birthord != 1]
```


```python
print(thinkstats2.CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb))
```

    -0.088672927072602


the weights of first borns are .08 standard deviations lower than the weights of 
babies born later. This difference is insignificant, much like the difference
in pregnancy lengths.

# Ex 3.1


```python
import thinkplot
```


```python
def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label=label)

    for x, p in pmf.Items():
        new_pmf.Mult(x, x)
        
    new_pmf.Normalize()
    return new_pmf
```


```python
resp = nsfg.ReadFemResp()
```


```python
numkdhh = thinkstats2.Pmf(resp.numkdhh, label='actual')
biased_numkdhh = BiasPmf(numkdhh, label='observed')
```


```python
#look at the data
for x,y in numkdhh.Items():
    print (x,y)
```

    0 0.466178202276593
    1 0.21405207379301322
    2 0.19625801386889966
    3 0.08713855815779145
    4 0.025644380478869556
    5 0.01072877142483318



```python
#plot the PMF
thinkplot.PrePlot(2)
thinkplot.Pmfs([numkdhh, biased_numkdhh])
thinkplot.Config(xlabel='Num Children', ylabel='PMF')
```


![png](output_12_0.png)


the survey data is biased by the fact that families with more children are more likely to appear in the sample. Also, even though 46% of families have no children, the data is biased by the fact that children are being surveyed. This means that the 46% of households with no children are automatically being excluded.

# Ex 4.2


```python
first_cdf = thinkstats2.Cdf(firsts.totalwgt_lb, label='first')
first_cdf.PercentileRank(4.8)
```




    4.652761861104744



I was born prematurely. 4.65 percentile.

# Ex 5.1


```python
import scipy.stats
```


```python
mu = 178
sigma = 7.7
dist = scipy.stats.norm(loc=mu, scale=sigma)
```


```python
dist.cdf(185.4) - dist.cdf(177.8)
```




    0.3420946829459531



34% of U.S. males are between 5'10 and 6'1


```python

```


```python

```
