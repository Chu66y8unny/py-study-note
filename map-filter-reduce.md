# Map, Filter and Reduce

## Map

Note that `map` returns an iterator.

```Python
items = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, items))

def square(x):
    return x * x

def double(x):
    return x + x

funcs = [square, double]
for i in range(5):
    value = list(map(lambda x: x(i), funcs))
    print(value)
```

## Filter

Note that `filter` returns an iterator.

```Python
numbers = range(-5, 5)
less_than_zero = list(filter(lambda x: x < 0, numbers))
not_zero = list(filter(None, numbers))
```

## Reduce

```Python
from functools import reduce
sum = reduce(lambda x, y: x + y, [1, 2, 3, 4], 47)
```
