# Introduction To Python

Python is an interpreted and easy to use language, that has object oriented features too. It's free software, which means you can install it for free as well as modify it to your own liking.

If the python is installed in your computer, you can fire it up by typing `python` in the command line.

This will open a read evaluate print loop (REPL). You can type python commands here and immediately get the results. Other ways of running python is to create a script and save it as `.py` file and run that using `python <filename>` command. You can also use IDLE which is an easy to use python IDE.

## Indentation And Blocks

Python, like other programming languages relies on blocks of code for sequence of execution, however, these blocks of code are not separated by parenthesis. Python uses indentation to denote blocks of code. 

These blocks often start with `:`, which denotes a new block of code with some indentation. These are used in blocks such as conditionals, loops, etc. 

## Data Types

Like most languages, python has mostly 4 major data types.

* Numbers
* Strings
* Floats
* Boolean

You can concatenate strings using the `+` operator.

## Variables

You don't need any keywords to declare variables. You can assign values to them right away.

```python
age = 29
```

You can get the variables data type by using the `type()` function.

## Special Operators In Python

Apart from normal operations such as `+, -, *, /, %`, python also supports exponentiation `**` and integer division `//`.

## Boolean Operators

You can compare boolean values using operators `<, >, ==` as well as combine them using `and, or, not`.

## Reference Operators

You can use the `id()` function to know if two variables have the same reference. You can also use the `is` keyword to know that. 

```python
a = 123
b = a
a is b # True
```

## Comments

Comments start wth the # pound character.

```python
# this is a comment
```

## Printing And Inputting Stuff

You can use the `print` function in python3 to print to stdout. Likewise, you can use `input` to read from stdin.

```python
print('Hello, Whats Your Name?')
name = input()
```

## Finding Length

`len()` is a very common function to find length of common python objects. It works on strings as well as lists.

## Parsing Data Types

Likewise, you can use `str()`, `int()`, `str()` and `float()` to parse data types from one form to their respective form. You can also parse boolean values to int. If they are true, it returns 1, else 0. Empty strings, lists and tuples also return zero.

## Importing Modules

You can import modules using the import keyword. For e.g. to import the random module

```python
import random
for i in range(5):
    print(random.randint(1, 10))
```

You can also use the from import keyword, which will add all the functions and objects of that module to context, so you will not need to add the module name before each function call.

```python
from random import *
```

## Exiting Programs

You can use `sys.exit()` to exit programs programmatically during execution.

```python
import sys

sys.exit()
```

## Calling OS commands

You can use pipes for that.

```python
import os

pipe = os.popen('ls -l')
print(pipe.read())
pipe.close()
```

## Command Line Arguments

You can use the `sys.argv` variable to know the arguments a program has been passed if it has been run from the command line.

```python
import sys

def main():
    for (i, arg) in enumerate(sys.argv):
        print(f'{i} - {arg}')

if __name__ == '__main__':
    main()
```
