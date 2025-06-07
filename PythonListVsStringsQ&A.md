# Python Lists Vs Strings: Mutable vs Immutable

🧑‍🎓 Student:
I'm learning Python and I noticed that lists are mutable but strings aren't. Could you explain how they are stored in memory and why one can be changed while the other can't?

👨‍🏫 Mentor:
Great question! This is fundamental to understanding how Python works under the hood.

Let’s break it down step by step.

🧑‍🎓 Student:
Okay, let’s start with storage. How are lists and strings stored in memory?

👨‍🏫 Mentor:
In Python, everything is an object — both strings and lists included. But they differ in how they store their contents.

🧑‍🎓 Student:
What about strings?

👨‍🏫 Mentor:
A string like:

`python s = "hello"`

is stored as a contiguous block of memory, holding the characters 'h', 'e', 'l', 'l', 'o'.

But here's the key part: strings are immutable — once created, their contents can't be changed.

So if you try:

`python s[0] = 'H'`
Python will throw an error:

```
TypeError: 'str' object does not support item assignment
```

🧑‍🎓 Student:
Why are strings made immutable?

👨‍🏫 Mentor:
Good question. Strings are immutable for a few solid reasons:

✅ They can be hashable, which is necessary when using them as dictionary keys or in sets.

🧠 Python can optimize performance and memory by reusing identical string objects (a technique called interning).

🔐 It’s safer to share strings across the program without worrying they’ll be changed somewhere else.

🧑‍🎓 Student:
Got it! Now what about lists?

👨‍🏫 Mentor:
A list like:

```python
mylist = ['a', 'b', 'c']
```

is stored differently. The list itself is a container that holds references (pointers) to its elements — not the elements directly.

These references are stored in an internal array, very much like a dynamic array in C.

🧑‍🎓 Student:
So that means I can change elements in a list?

👨‍🏫 Mentor:
Exactly. You can easily do:

```python
mylist[0] = 'z'
```

This doesn’t change the string 'a' — it just updates the pointer at index 0 to now refer to 'z'.

That’s why lists are mutable.

🧑‍🎓 Student:
Can I see how this looks in memory?

👨‍🏫 Mentor:
Absolutely! Try this:

```python

s = "hello"
print(id(s))
s = "world"
print(id(s))  # Different object

lst = ['a', 'b']
print(id(lst))
lst[0] = 'z'
print(id(lst))  # Same object
```

When you assign a new value to s, a new string object is created (with a new memory address).

But when you modify a list item, the list object stays the same — only the reference inside changes.

🧑‍🎓 Student:
And how do Python lists work internally?

👨‍🏫 Mentor:
Python lists are like dynamic arrays:

They start with a fixed capacity.

When you append or remove items, Python may resize the array internally.

This gives you both flexibility and speed, at the cost of a bit more memory.
