There are several ways to get the iteration number in a for loop in Python. Here are the most common methods:

### 1. Using `enumerate()`

The `enumerate()` function is the most `Pythonic` way to get both the index and value of each item in an iterable. It returns a tuple containing the index (starting from 0) and the corresponding item.
```python
   my_list = ['a', 'b', 'c', 'd']
   for index, item in enumerate(my_list):
       print(f"Index: {index}, Item: {item}")
```

You can also specify a starting index for `enumerate()`:
```python
   for index, item in enumerate(my_list, start=1):
       print(f"Index: {index}, Item: {item}")
```

### 2. Using a counter variable

You can manually create a counter variable before the loop and increment it in each iteration. This approach is less common but can be useful in specific scenarios:
```python
   my_list = ['a', 'b', 'c', 'd']
   counter = 0
   for item in my_list:
       print(f"Index: {counter}, Item: {item}")
       counter += 1
```

### 3. Using `range()` with an index

If you are iterating through a list using indices, you can use `range()` to generate the indices and access the items using those indices:
```python
   my_list = ['a', 'b', 'c', 'd']
   for index in range(len(my_list)):
       print(f"Index: {index}, Item: {my_list[index]}")
```

When to use each method:

-  `enumerate()`:
     Use this when you need both the index and the item value while iterating over a sequence. It's generally the preferred method for most cases.
    
- **Counter variable:**
     Use this when you need more control over the counter, like incrementing by a different value or starting from a specific number.
    
-  `range()` with an index:
	This approach is useful when you need to work with indices explicitly, such as when modifying the list during iteration.