# Deep Copy v/s Shallow Copy

In Python, when you assign an object to a new variable, the new variable is a reference to the original object, rather than a copy of the original object. This means that if you modify the object through the new variable, the original object will also be modified.

In some cases, you may want to create a true copy of an object, rather than just a reference to the original object. This is where shallow and deep copying come into play.

Shallow copying in Python is done using the `copy` module's `copy` function. Shallow copying creates a new object with a new reference, but the new object contains references to the original objects contained within the original object.

Deep copying in Python is done using the `copy` module's `deepcopy` function. Deep copying creates a new object with a new reference, and all objects contained within the original object are recursively copied.

Here's an example of shallow and deep copying in Python:

```python
import copyddd

# Shallow copy example
original_list = [[1, 2], [3, 4]]
shallow_copy = copy.copy(original_list)

print("Original list:", original_list)
print("Shallow copy:", shallow_copy)

# Modifying original list
original_list[0][0] = 10

print("Original list after modification:", original_list)
print("Shallow copy after modification:", shallow_copy)

# Deep copy example
original_list = [[1, 2], [3, 4]]
deep_copy = copy.deepcopy(original_list)

print("Original list:", original_list)
print("Deep copy:", deep_copy)

# Modifying original list
original_list[0][0] = 10

print("Original list after modification:", original_list)
print("Deep copy after modification:", deep_copy)
```

The output of the above code will show the difference between shallow and deep copying. It is below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675824448308/89b85556-5cb6-484b-a50f-5c834c6ba0df.png align="center")