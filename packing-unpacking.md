# Packing, Unpacking

## Packing

`*args` and `**kwargs` are mostly seen in function definitions which allow
the callers to pass a variable number of arguments to a function. In function
definitions, `args` collects all the positional arguments as a `tuple`,
`kwargs` collects all the named arguments as a `dict`.

```Python
def foo(*args, **kwargs):
    print(type(args))
    for x in args:
        print(x)
    print(type(kwargs))
    for k, v in kwargs.items():
        print(k, v)

foo(1, 2, 3, a='Chubby', b='Bunny')
```

`*args` and `**kwargs` are very useful for define functions taking arbitrary
arguments when making function decorators.

## Unpacking

Essentially unpacking by `*` or `**` is used to unpack tuple, list, or dict
and provide arguments for function calls.

```Python
def foo(a, b, c):
	print(f'{a} {b} {c}')

args = ['Tom', '&', 'Jerry']

# unpacking the list into 3 arguments
foo(*args)

kwargs = {'a': 'Chubby', 'b': 'M', 'c': 'Bunny'}

# unpacking the dict into 3 named arguments
foo(**kwargs)
```
