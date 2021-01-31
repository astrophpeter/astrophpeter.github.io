---
title:  "Writing better python for research"
date:   2020-05-03
description: Two ways I've improved my python
draft: false
---

[![hits](https://hitcounter.pythonanywhere.com/count/tag.svg)]

Writing readable high-quality code is key to being able to carry out efficient and effective research. Whilst in lockdown over the past six weeks I've been trying to improve my python skills and learn about better ways to write my research code. I want to share two things I've found particularly useful for improving the quality of my own code, in the hope that they will help you too.

This post has had many sources of inspiration, my main one has been from watching videos of Raymond Hettinger, in particular [this one](https://www.youtube.com/watch?v=OSGv2VnC0go), which is packed full of amazing python tips. Also, I've learned many things from reading other blog posts like [this one](https://medium.com/the-andela-way/idiomatic-python-coding-the-smart-way-cc560fa5f1d6) and [this one](https://docs.python-guide.org/writing/style/).

## List comprehension

In lots of my research code, I'm always collecting and monitoring values from an experiment I'm running. For simplicity let's just assume our experiment is collecting the numbers from 0 to 9, the common pattern I use for this sort of thing is the following for loop:


```python
results = []
for i in range(10):
    results.append(i)
print(results)
```

```python    
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

Instead of doing this, we can use list comprehension to achieve exactly the same thing, which would look like this:

```python
results = [i for i in range(10)]
print(results)
```

```python
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

So much more clean right? The first thing to notice is that we decreased the amount of code needed **and** retained its readability. The second thing to notice is that this way of doing things is also faster than the for loop. We can see this by timing each of the methods, let's also increase the number we want to count to 10000 so we can see the speed up:


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

We can see that the list comprehension was about twice as fast as the for loop! List comprehension can also be combined with conditional expressions. To show this let’s just count the even numbers from 0 to 9 for example:


```python
results = [i for i in range(10) if i % 2 == 0]
print(results)
```

```python
[0, 2, 4, 6, 8]
```

We can also use list comprehension to build dictionaries in a similar way by replacing \[ \] with \{ \}.

## Named tuples for model parameter vectors

Another common thing I have to do is fitting models to data. This procedure often requires passing vectors of parameters between functions. For example, let's assume we are fitting a straight line to some data, we will need a function that takes the input value (x) and predicts an output value (y) for given values of our model parameters (slope = 1.0 and intercept = 2.0). Let's say for the vector of parameters for this model the first element is the intercept and the second element is the slope. Then the predict function would look something like this:


```python
params = [1.0, 2.0]

def predict_y(params, x):
    return params[0] + params[1] * x
```

OK, this code doesn't look too bad. But you can imagine if we have a more complicated model with say 10 parameters then this could get messy. Moreover using this method requires remembering the order of the parameters and if we were to change the order this function would break. Having to access the parameters by indexing also makes the code harder to understand. 

Instead of using a list or array, we could use a namedtuple as the parameter vector:


```python
from collections import namedtuple

Parameters = namedtuple('Parameters', 'intercept slope')
params = Parameters(intercept=1.0, slope=2.0)
```

What's really cool about named tuples is that in addition to being able to access its elements with indexing we can also access them by the class style '.' syntax. 


```python
print(params[0], params[1])
print(params.intercept, params.slope)
```

```python
1.0 2.0
1.0 2.0
```

Also if we print out params we get a descriptive representation compared to printing an array or list.


```python
print(params)
```

```python
Parameters(intercept=1.0, slope=2.0)
```

If we use the Parameters namedtuple we can then rewrite our predict_y function as:


```python
def predict_y(params, x):
    return params.intercept + params.slope * x
```

Which is far more readable than the previous version. In addition to this if we decide to change the order of our parameter vector this function will not break!

The code in this post can be run in your browser by clicking one of the badges below.

[![Binder](https://mybinder.org/badge_logo.svg#badge)](https://mybinder.org/v2/gh/astrophpeter/astrophpeter.github.io/master?filepath=notebooks/2020-05-03-writing-better-python-for-research.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg#badge)](https://colab.research.google.com/github/astrophpeter/astrophpeter.github.io/blob/master/notebooks/2020-05-03-writing-better-python-for-research.ipynb)
