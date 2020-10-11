# Persistent Storage

Some of the ways that you can store data persistently in Python are given below.

## Files

Its the simplest way to store data. They are created with the `open()` function. You also need to pass the mode you want to open the file as.

```python
import os
# Use open to open a file

fo = open('test.txt', 'w') # w deletes stuff incase file already present
fo.write('Hello, World!')
fo.close()

fo = open('test.txt', 'r')
print(fo.read())
fo.close()

print('Current Dir ' + os.getcwd())
os.remove('test.txt')
```

There is no straightforward way to delete a file. So we are using `os` module to do it.

## Simple Database - `dbm`

Python also provides a lightweight key value store called `dbm`. However, it can only store strings. If you want to store complex data types, you can use the pickle module to load and unload the objects to strings.

```python
import dbm
import pickle
import os

db = dbm.open('students', 'c')
db[ 'name' ] = 'Saurav'
print(db['name'])

db['students'] = pickle.dumps({ 'name': 'Saurav', 'age': 28 })
print(db['students'])
print(pickle.loads(db['students']))
db.close()

os.remove('students')
```