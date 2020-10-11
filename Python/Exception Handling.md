# Exception Handling

You can catch runtime exceptions in python using `try except` blocks. One of the examples is shown below.

```python
print('How many cats do you own? ', end='')
numCats = input();

try:
    numCats = int(numCats)
    if numCats > 4:
        print('That\'s a lot of cats.')
    else:
        print('That\'s not many cats.')
except ValueError:
    print('You didn\'t enter a number.')
```
