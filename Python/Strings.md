# Strings

Strings are another data type in Python. They can be declared in a number of ways.

```python
strng = 'Hello, World!\n' # with escape chars
strng = r'Hello \'world' # raw strings
strng = """
Hello world!
I am
learning
Python
"""
# multiline strings
```

## Check a substring exists in a string

You can do that using the `in` operator.

```python
print('Hello' in strng)
```

Python strings also support slicing like lists.

## String Interpolation

Python 3 uses f-strings

```python
name = 'Saurav'
age = 28
str = f'Hello {name}, your age is {age}.'
print(str)
```

You can also use format function:

```python
name = 'Saurav'
age = 29
print('Hi, my name is {name} and age is {age}'.format(name, age))
```

This will output

`Hi, my name is Saurav and age is 29`

## Other String Methods

There are various other string methods. Some of them are below

* `upper()` converts to upper case
* `lower()` converts to lower case
* `startsWith()` check whether string starts with
* `join()` join strings in a list
* `split()` split strings to list
* `partition()` partition a string
