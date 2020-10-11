# Flow Control In Python

Python like other languages has excellent features for flow controls.

## If Statements

You can use `if, else, elif` to check conditions.

```python
if name == 'Saurav':
    print('Hello')
elif name == 'Sanjay':
    print('Hi')
else:
    print('Bye')
```

Anything except empty string is taken as a truthy value. Any number except zero is taken as a truthy value.

## While Loops

They are constructed as below

```python
i = 0
while i < 5:
    i = i + 1
    if i == 4:
        continue
    else:
        print('Hello ' + str(i))
print('Done')
```

## For Loops

```python
for i in range(100):
    if i == 4:
        continue
    elif i > 5:
        break
    print('Hello ' + str(i))
print('Done')
```

## Range

`range()` is an widely used function to generate an iterator. It accepts three arguments, the start, the stop and the step. Range can be used in for loops to loop through a generated list. Range starts from start number you give but stops at 1 number before end, e.g. end is not inclusive.
