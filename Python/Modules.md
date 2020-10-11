# Modules

Any file can be a module. You can also import global functions and variables using the import keyword, if they reside in the same directory. However, to prevent function execution, you have to have a line at the end like this which means the module will only execute if it is getting directly getting executed from the command line.

```python
if __name__ == '__main__':
    # do the main task
```

## Importing modules

You can import modules and their functions in a number of ways.

```python
import math
import math as mt
```