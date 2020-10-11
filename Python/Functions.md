# Functions

You can define functions in python using the def keyword. All functions can take zero to some required and optional arguments. All functions return a value. If you don't add a `return` statement, they return `None`.

```python
def sayHello(name):
    print('Hello ' + name)

sayHello('Saurav')
```

You can give optional values to functions using the `=` sign. These are also known as keyword arguments.

```python
print('Hello', end='')
```

Functions can have optional arguments too. You can use = with a default value to denote an optional argument.

```python
def fun(a, b = 10):
    return a * b
```

## Docstrings In Functions

You can add docstrings in function, just after the function header. They act as minimal documentation for the function you are going to write.

```python
def sum(*n):
    """Calculates sum from a list of arguments
    *n - list of arguments
    """
    sumOfNumbers = 0
    for i in n:
        sumOfNumbers += i
    return sumOfNumbers
```

## Functions As Arguments

You can also supply function as argument in python.

```python
def sayHello(times=5):
    if times > 5:
        print('hello ' * times)
    else:
        print('hello ' * 5)

def callFn(fn, arg):
    fn(arg)

callFn(sayHello, 2)
```