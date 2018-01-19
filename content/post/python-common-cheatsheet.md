+++
date = "2018-01-11"
description = "Python cheat sheet for biology"
draft = true
tags = ["python", "cheat sheet"]
title = "Common python cheat sheet"
topics = ["Bioinformatics"]
+++

## Common things to remember

#### Lists:

Lists are represented simply between square brackets with each element within quotes.
```Python
# Example:
animals = ["deer", "buffalo", "donkey", "cat", "dog", "rat"]
numbers = ["23", "625", "123", "423"]
```

The lists can be sliced similar to regular variables (strings/numbers).

```Python
# Using the same example:

print(animals[0])
print(animals[2:4])
print(animals[3:])
print(numbers[2:])

# result
deer
['donkey', 'cat']
['cat', 'dog', 'rat']
['123', '423']
```

Adding elements to an existing list is done by using the method **.append()**
```Python
# Using the same list - animals
animals.append("mouse")
print(animals)

# result
['deer', 'buffalo', 'donkey', 'cat', 'dog', 'rat', 'mouse']
```
