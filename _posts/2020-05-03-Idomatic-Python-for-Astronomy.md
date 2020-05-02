---
title:  "Idiomatric python for astronomy"
date:   2020-05-03
description: Testing a jupyter notebook
---

Whilst in lockdown over the past 6 weeks I've been trying to improve my python coding skills, and learn about more pythonic ways to write my research code. I wanted to share 3 things I've found useful for myself and will hopefully be useful for you too.

List comprehension

In lots of my research code I'm always collecting an mointoring values from an experiment I might be running. For simplicty let's just assume our experiment is collecting the numbers from 0 to 9, the common pattern I use for this sort of thing is the following. 


```python
results = []
for i in range(10):
    results.append(i)
print(results)
```

```python
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

Instead of doing this we can use list comprehension with a generator expression to achieve exactly the thing:


```python
results = [i for i in range(10)]
print(results)
```

```python
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

So much more clean right? The first think to note we decreased the amount of code and retained the readability. If you think couldn't get even better, the genreator expression is also faster than the for loop. We can see this by timing each of the methods, let's also increase the number we want to count to to 10000 so we can see the speed up:


```python
%%timeit
results = []
for i in range(10000):
    results.append(i)
```

```python
1.02 ms ± 175 µs per loop (mean ± std. dev. of 7 runs, 1000 loops each)
```


```python
%%timeit
results = [i for i in range(10000)]
```
```python
435 µs ± 56.5 µs per loop (mean ± std. dev. of 7 runs, 1000 loops each)
```

We can see that the list comphrhension was about twice as fast. We can also use this type of syntax to build dictionaries and tuples. 

Named tuple for model parameter vectors

Another common thing I have to is fitting models to data. This procedure often requires passing vectors of parameters between functions. For example let's assume we are fitting a straight line to some data, we will need a function that takes the and input value (x) and predicts a output value (y) for given values of our model parameters (slope and intercept). Let's say for the vector or parameters for this model the first element is the intercep and the second element is the slope, then the predict function would look something like this:


```python
params = [1.0, 2.0]

def predict_y(params, x):
    return params[0] + params[1] * x
```

Ok this code doesnt look too bad. But you can imagine if we have a more complicated model with say 10 parameters this could get messy. Using this method also have to remeber the ordering of the parameters and if i were to change the order this code would break.


```python
from collections import namedtuple

Parameters = namedtuple('Parameters', 'intercept slope')
params = Parameters(intercept=1.0, slope=2.0)
```


```python
def predict_y(params, x):
    return params.intercept + params.slope * x
```

[![Binder](https://mybinder.org/badge_logo.svg#badge)](https://mybinder.org/v2/gh/astrophpeter/astrophpeter.github.io/master?filepath=notebooks/2020-05-03-Idomatic-Python-for-Astronomy.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg#badge)](https://colab.research.google.com/github/astrophpeter/astrophpeter.github.io/blob/master/notebooks/2020-05-03-Idomatic-Python-for-Astronomy.ipynb)

