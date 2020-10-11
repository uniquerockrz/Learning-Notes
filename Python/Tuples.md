# Tuples

Tuples are just a list of comma separated values in python. You can use `()` to represent them. However, thats optional.

The best use case of tuples is to swap values without using a third variable.

```python
a, b = b, a
```

If you want to have a tuple with a single value, end it with a final comma.

## Tuples as variable length arguments of functions

If you don't know number of arguments a function will have, you can use tuples.

```python
def sum(*n):
    sum = 0
    for i in n:
        sum += i
    return sum
```

You can call the above function with a list of comma separated arguments and it will work. If you want to pass a variable though, you have to add `*` in front of variable name.

## zip function

Like `enumerate()`, `zip` is a function which combines two sequences and returns a tuple in each iteration. It can be used with strings, lists and tuples.

## Tuples as keys of Dictionaries

You can also use tuples as keys of dictionaries. This is useful if you need multiple reference to a value.

```python
students = { ('saurav', 'modek') = 28 }
```