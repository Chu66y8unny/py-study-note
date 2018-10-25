# Iterable, Iterator, Generator

## Iterable

A Python object is **iterable** if it has an `__iter__` or a `__getitem__`
method. `__iter__` returns an **iterator** and `__getitem__` takes an index
(key) and returns the value for the index (key).

What's the difference between `__iter__` and `__getitem__`? The `__getitem__`
is a legacy before Python had modern iterators. The idea was that any
sequence (something that is indexable and has a length) would be automatically
iterable using series s[0], s[1], s[2], ... until `IndexError` or
`StopIteration` is raised. For example, in Python 2.7, `str` is iterable
because it defines an `__getitem__` method but it does not have an `__iter__`
method.

To see how `__iter__` and `__getitem__` actually work:

```Python
# make an iterable class using the legacy style for sequences
class A:
    def __getitem__(self, index):
        if index >= 10:
            raise IndexError
        return index
for i in A():
    print(i)

print(list(A()))

# make an iterable class using the __iter__
class B:
    def __iter__(self):
        for i in range(10):
            yield i

for i in B():
    print(i)

print(list(B()))

b = B()
for i in b:
    print(i)

ib = iter(b)
print(next(ib))
```

### Questions

- What is an **sequence type** then?
- What are the return types of `iter(list())`, `iter(tuple())`, `iter(dict())`?

## Iterator

An iterator is an object which has an `__next__` method defined (Python 3,
`next` in Python 2.7). Generally `iter(obj)` returns the iterator for the `obj`.

```Python
>>> next(str())
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: str object is not an iterator
>>> iter(str())
<iterator object at 0x10bbac090>
```

An iterable is not an iterator but an iterator can be obtained by call `iter()`
on the iterable.

## Generator

```Python
def foo_gen():
    for i in range(3):
        yield i

for i in foo_gen():
    print(i)

# Output:
# 0
# 1
# 2

def bar_gen():
    for i in range(3):
        yield i

bg = bar_gen()
print(next(bg)) # 0
print(next(bg)) # 1
print(next(bg)) # 2
print(next(bg)) # raise StopIteration
```

The `for` loop automatically catches `StopIteration` and stops calling `next`.

```Python
def fibonacci(n):
    a = b = 1
    for i in range(n):
        yield a
        a, b = b, a + b

fgen = fibonacci(10)
for f in fgen:
    print(f)
```

## References

- <https://stackoverflow.com/questions/20551042/whats-the-difference-between-iter-and-getitem/20551346#20551346>
- <https://stackoverflow.com/questions/926574/why-does-defining-getitem-on-a-class-make-it-iterable-in-python>
- <https://www.python.org/dev/peps/pep-0234/>
