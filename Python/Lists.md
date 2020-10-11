# Lists

Lists are use to store a group of data together. They are mutable objects in python, unlike strings which are immutable. You can declare lists in a number of ways.

```python
lst = list()
lst = []
```

Like other programming languages, you can access list items from their index.

```python
lst[0] # get the first item
```

However, python offers a special way to access list using negative indexes, which start at the end.

```python
lst[-1] # access the last item
```

You can also loop over lists using a for loop.

```python
for i in lst:
    print(i)
```

## Slices

Slices are part of lists. There is a special format for accessing them. Remember, the second index in slices is exclusive of that index.

```python
lst[0, 4] # start from 0th item, end at 3rd in index
lst[2:] # start at 2nd index, get the rest of the list
lst[:4] # start at 0, get till 3rd index
```

## len and changing items

You can get the length of the list using `len()`. You can also change items by providing their index.

```python
lst[1] = 2 # change the second item
```

You can also have other operators on list, like concatenation `+` and multiply `*`.

You use `del` to delete an item from list

```python
del lst[0] # delete first item
```

The `in` operator is used to check whether a specific item exists in list or not.

You can also use `enumerate()` function to iterate over a list. The function returns two values, the index and the actual item of the list.

## List methods

Some of the list methods are

```python
lst.index() # get index where item is at
lst.append() # add at end
lst.insert(index, item)  # add item at index
lst.remove(item) # remove an item
lst.sort() # sort a list
lst.reverse() # reverse a list
```

You can also use `+` and `*` operators on lists, like strings. However, they return a new list instead of mutating the original list. 

You can also use some other python functions with lists, such as `len`, `sorted`, `max` and `sum`.

## Copy By Reference In Lists

Lists are always copied by reference, Which means, if you pass a list to a function and mutate it there, it will be also reflected in the callee function. This can pose a few problems. Thats where copy module comes in.

Copy module allows you to deep and shallow copy lists.

```python
import copy
copy.deepcopy(lst) # creates a new list
```

You can verify if its a new list by using the `id()` function.

## List Comprehensions

You can create cool list comprehensions in python, which can be a combination of loops, conditionals and other statements. List comprehensions always return a list. For example, the following returns a list of planets which have more than 4 characters in their name. 

```python
planets = ['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Neptune', 'Pluto']
[planet for planet in planets if len(planet) > 4]
```

You can also build dictionaries with it

```python
{planet: planet[0] for planet in planets}
```
