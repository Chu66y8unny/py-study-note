# Ternary Operators

```Python
value_if_condition_true if condition else value_if_condition_false
```

Alternatively

```Python
(value_if_test_false, value_if_test_true)[test] # Not Pythonic
```

Note in the above both the elements of the tuple are evaluated.

```Python
condition = True
print(2 if condition else 1/0)

print((1/0, 2)[condition])
```

```Python
>>> True or "Some"
True
>>> False or "Some"
'Some'
```
