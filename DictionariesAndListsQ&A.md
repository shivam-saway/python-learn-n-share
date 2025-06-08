# Dictionaries in Python

### 🎓 Student: 
What exactly is a dictionary in Python? How is it different from a list?

### 👨‍🏫 Mentor: 
Great question! A dictionary in Python is an unordered, mutable collection of key-value pairs. Think of it like a real-world dictionary — you look up a key (like a word) to get its value (its meaning).

```python
person = {"name": "Alice", "age": 30}
```
A list, on the other hand, is an ordered, mutable sequence of items accessed via index — like a to-do list:

```python
fruits = ["apple", "banana", "cherry"]
```
### 🎓 Student: 
Cool! But what actually happens behind the scenes when I use a dictionary?

### 👨‍🏫 Mentor: 
Ah, time to lift the hood! 🔧

When you create a dictionary, Python creates a hash table.

Each key is passed through Python’s built-in hash() function, which determines where in memory the value is stored.

So when you access my_dict["name"], Python quickly finds the location using the hash — no need to scan the whole structure. That’s why dictionary lookups are super fast! 🚀

### 🎓 Student: 
And what about adding or deleting keys?

### 👨‍🏫 Mentor: 
Great follow-up!

➕ Adding a key-value pair:

```python
my_dict["city"] = "Delhi"
```

Python hashes the key "city" and stores it in a memory slot. If there's a collision (two keys hashing to the same place), it handles that internally using smart techniques like open addressing.

❌ Deleting a key-value pair:

```python
del my_dict["name"]
```
Python finds the location by the key’s hash and marks it as deleted — it doesn’t immediately erase it to preserve performance.

### 🎓 Student:
When should I use a list vs a dictionary? Are there pros and cons?

### 👨‍🏫 Mentor: 
Absolutely — here's a quick rundown:

|Feature|	List|	Dictionary|
|:---------:|:----------:|:----------:|
|Access type|	Index-based|	Key-based|
|Ordering|	Preserves insertion order|	Preserves insertion order (Py 3.7+)|
|Performance|	Fast iteration|	Fast lookup|
|Memory usage|	Less per item|	Higher (due to hashing, pointers)|
|Best use-case|	Sequential data|	Labeled data or mappings|

✅ Use a list when:

Order matters, and you don't need named access.

You want memory efficiency.

You need slicing or sorting.

✅ Use a dictionary when:

You want to associate names with values (e.g., name: age).

You care more about quick lookup than memory.

You want structure similar to real-world mappings.

### 🎓 Student: 
Last one — which is faster when fetching data?

### 👨‍🏫 Mentor: 
You're thinking like a pro now! ✅

📌 Dictionaries are generally faster when fetching by key — they use O(1) lookup time thanks to hashing.

📌 Lists also offer O(1) access — but only by index. If you’re searching for a value, it takes O(n) time.

🧠 In terms of memory, lists are more lightweight. Dictionaries trade extra memory for speed and flexibility.

### 🎓 Student: 
That’s brilliant! Thank you for breaking it down so clearly!

### 👨‍🏫 Mentor: 
You’re welcome! Keep exploring — Python has a lot of elegant design choices under the hood. 🚀