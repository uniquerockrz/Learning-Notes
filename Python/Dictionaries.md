# Dictionaries

Dictionaries are used to store unordered data in python. They can be defined as follows

```python
dic = { 'name': 'Saurav', 'age': 28 }
dic['name'] # get the value of name in dic
```

You can use the `in` keyword to loop over keys in a dictionary. They keys in a dictionary has to be immutable. So you can use strings, integers and tuples as keys. However, you cannot use lists.

## Dictionary Methods

Some of the methods dictionaries have are:

```python
dic.keys() # get all keys
dic.values() # get all values
dic.items() # get all items as tuples
```

You can use `get()` to check whether a key exists in a dict.

```python
dic.get('name') # True
```

You can use `setdefault()` to set a default value if the key doesn't exists.