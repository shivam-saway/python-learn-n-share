# Tuples in Python

## 🧑‍🎓 Student:
What are tuples in Python?

## 👨‍🏫 Mentor:
A tuple is a data structure in Python that lets you store a collection of elements — of different or the same types — in a fixed and ordered sequence. Once a tuple is created, its elements can't be modified (that's what we call immutability).

```python
# Example of a tuple with different data types
my_tuple = (1, "apple", 3.14)
print(my_tuple)

# (1, "apple", 3.14)
```

## 🧑‍🎓 Student:
How are tuples different from lists?

## 👨‍🏫 Mentor:
While both tuples and lists store collections of elements, there are some key differences:

✅ Tuple — Immutable and ordered, with fixed size.
✅ List — Mutable and ordered, with variable size.
Additionally, tuples can be hashed and used as dictionary keys or set elements, while lists cannot.

```python
# List (mutable)
my_list = [1, 2, 3]
my_list[0] = 100  # This is fine

# Tuple (immutable)
my_tuple = (1, 2, 3)
# This would raise an error like item assignment in not supported in tuple:
# my_tuple[0] = 100
```

## 🧑‍🎓 Student:
How are tuples stored internally in memory?

## 👨‍🏫 Mentor:
Internally, tuples store their elements in a contiguous array of references to those elements. This lets you access elements efficiently by index, much like a list. The main difference is that tuples’ size and content are fixed after their creation.

```python
# This cannot grow or shrink after it's created
coordinates = (40.748817, -73.985428)
print(coordinates[0])  # Access by index
```

## 🧑‍🎓 Student:
Why are tuples immutable?

## 👨‍🏫 Mentor:
Because tuples are immutable, their content cannot be changed after they’re created. This guarantees their safety and predictability, lets them be used as dictionary keys or set elements, enable certain performance optimizations, and preserves data integrity — you can be assured their values remain consistent and trustworthy.

```python
# This will raise a TypeError
coordinates[0] = 100
# TypeError: 'tuple' object does not support item assignment
```

## 🧑‍🎓 Student:
When should I prefer to use tuples in my code?

## 👨‍🏫 Mentor:
You should prefer tuples when:

- ✅ The collection is fixed and should not be modified afterwards.
- ✅ The elements represent related but different items (like coordinates or color components).
- ✅ Hashability or immutability is desirable (for use in sets or as dictionary keys).
- ✅ The semantic structure is more important than adding or removing elements.
- ✅ Some small performance optimizations can be a consideration due to their lightweight structure.
- ✅ Maintaining data integrity — you want to make sure the data cannot be inadvertently changed.

```python
# Returning multiple values from a function
def get_coordinates():
    return (40.748817, -73.985428)

location = get_coordinates()
print(location)  # (40.748817, -73.985428)
```

## 🧑‍🎓 Student:
Could you give me some real-world examples where tuples are preferred?

## 👨‍🏫 Mentor:
Of course! Here are a few:

✅ Returning multiple values from a function:

```python
def get_name_and_age():
    return ("Alice", 30)

name, age = get_name_and_age()
print(name, age)
```

✅ Storing fixed data structures (like colors with RGB components):

```python
color = (255, 0, 0)  # Red
print(color)
```

✅ Using tuples as composite keys in dictionaries:

```python
population = {
    ("California", "Los Angeles"): 3980400,
    ("New York", "New York City"): 8492200,
}

print(population[("California", "Los Angeles")])  # Prints 3980400
```

✅ Database records or data transfer tuples:

```python
# Database row representation
user = (1, "Alice", "alice@example.com")
print(user)
# (1, "Alice", "alice@example.com")
```