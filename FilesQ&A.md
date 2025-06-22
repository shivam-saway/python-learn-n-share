# Files in Python

### 🎓 Student: 
Hey, I have just started with files but it is not clear to me. Can you help me to clear my concepts of files in python ?

### 👨‍🏫 Mentor:
Hey, I am glad you are still continuing with your journey of learning python. Yes, I can help you with files concept in python. Ask what are your doubts.

### 🎓 Student:
Ok, So tell what exactly a file is in python ? What purpose they serve ?

### 👨‍🏫 Mentor:
In Python, a file is an external resource — a place to store data permanently on your disk. Unlike variables, which disappear when the program ends, files let your data live on.

We use files to:

- Save reports, logs, or results

- Load datasets and configuration files

- Store user data or program outputs

They’re essential when you want your program to remember information or exchange data with the outside world.

### 🎓 Student:
Got it! So how do we actually use files in Python? How can we read or write data in them?

### 👨‍🏫 Mentor:
This is where File I/O (Input/Output) comes in.

Python gives you a built-in open() function to interact with files. You open a file, read from it or write to it, and then close it — or better, use a with statement that closes it automatically.

**Basic file I/O flow,**

```python

    with open('filename.fileextentsion', mode = 'r') as f:
        #read , write or append to the file.

```

### 🎓 Student:
Ok, I understand the basic code syntax, what could you please explain what is mode here ?

### 👨‍🏫 Mentor:
Ah, great observation! The mode tells Python what kind of access you want for the file — like whether you want to read, write, or append.

***📘 File Modes in Python***

Here's a full list of modes you can use:

Basic Modes:

| Mode | Action  | File Must Exist? | Truncates File? |
|------|---------|------------------|-----------------|
| `'r'` | Read    | ✅ Yes           | ❌ No           |
| `'w'` | Write   | ❌ No            | ✅ Yes          |
| `'a'` | Append  | ❌ No            | ❌ No           |
| `'x'` | Create-only | ❌ No       | ❌ No (Error if exists) |

Combined Modes:

| Mode  | Action           | Truncates? | Notes          |
|-------|------------------|------------|----------------|
| `'r+'` | Read and write   | ❌ No      | Cursor at start |
| `'w+'` | Write and read   | ✅ Yes     | Overwrites      |
| `'a+'` | Append and read  | ❌ No      | Cursor at end   |

Binary Modes:

Add `'b'` for binary files like images, audio, video:

like `rb`, `wb`, `ab` etc


### 🎓 Student:
I noticed that in different modes, like 'a+' or 'r+', you mentioned the cursor position is at the start or end. What is this cursor exactly? Can I control it? And how does this relate to how Python reads and writes files?

### 👨‍🏫 Mentor:
Brilliant question! You're thinking like a real developer now. 😄

Let’s break it down and understand it step by step:

So, let me answer your first question,

***What is a cursor ?***

When you open a file, Python maintains an internal pointer (called the cursor) that tells it where in the file to read from or write to.

- It starts at position 0 by default (beginning of the file) — unless you're using append mode ('a'/'a+'), where it's placed at the end.

- Every time you read or write, the cursor moves automatically.

```python
    with open('test.txt', 'r') as f:
        print(f.tell())     # ➝ 0 (start)
        print(f.read(5))    # ➝ reads 5 characters
        print(f.tell())     # ➝ 5 (cursor moved)
```

***Can you control the cursor ?***

You can move the cursor manually using .seek(offset, whence):

| Usage           | Meaning                                  |
|-----------------|------------------------------------------|
| `f.seek(0)`     | Move to the start of the file            |
| `f.seek(10)`    | Move to byte 10                          |
| `f.seek(0, 2)`  | Move to the end of the file              |
| `f.seek(-5, 1)` | Move 5 bytes backward from current position |

You can also use .tell() to find out where the cursor is:

```python
   with open('file.txt', mode='a') as f:
    postion = f.tell()
```

***How Does Python Handle File Content Internally?***

Python treats files as streams of bytes under the hood:

- Even in text mode ('r', 'w'), it converts characters to bytes using encoding (like UTF-8).

- That’s why cursor positions are in byte offsets, not necessarily characters.

In binary mode ('rb', 'wb'), you deal directly with raw bytes — no encoding/decoding happens.

### 🎓 Student:
You know, while testing .read(), I realized something...
If I read the entire file at once using f.read(), and the file is very large, won’t that consume a lot of memory — maybe even crash the program?

### 👨‍🏫 Mentor:
That’s exactly the kind of thinking that separates a beginner from a smart developer.

***So, Why Reading Large Files All At Once Can Be Dangerous***

- f.read() loads the entire file into memory.

- If you're working with a small file — no problem.

- But for large files (hundreds of MBs or GBs), this can:

  - Slow down the program

  - Cause memory errors

  - Even crash your application on low-resource systems

***Best Practice: Read Files Line-by-Line***

Instead of this:

```python
    f.read()
```

Do this:

```python
    with open('file.txt', mode='r') as f:
        for line in f:
            processLine(line)
```

This way you safegurads your program from

- Memory Limits

***Additional Best Practices for File Handling in Python***

- Use  `with` statments
- Use `seek` and `tell` for control.
- Use os.path.exists() if using read modes ('r', 'r+') to avoid crashing:

```python
    import os
    if os.path.exists('data.txt'):
        with open('data.txt') as f:
            #read write or append file
```

- Python doesn't "know" if a file is JSON, CSV, or XML — you must use the appropriate parser ( like csv.reader for csv files, ijson for json objects etc).

- Use Binary Modes for Non-Text Files (video, images etc)


### 🎓 Student:
Now its great. I have got so much understanding. But still I have one question. Most of the time, I have seen data comes in format of .xlsx for .xls file.
Do we have any special parser for that ?


### 👨‍🏫 Mentor:
When you use Python's default open() function:

- It reads raw text or bytes.

- Excel files (.xlsx, .xls) are binary spreadsheet formats, not plain text.

- You’d just get unreadable gibberish if you try to open Excel files like this:

```python
    with open('data.xlsx', 'r') as f:
        print(f.read())
```

***How to Handle Excel Files in Python***

You need to use external libraries built to understand Excel’s structure:

| File Type | Recommended Library | Description                       |
| --------- | ------------------- | --------------------------------- |
| `.xlsx`   | `openpyxl`          | Read/write modern Excel files     |
| `.xls`    | `xlrd`              | Read older Excel files (pre-2007) |
| Both      | `pandas`            | Powerful tool for structured data |

***Example using pandas***

```python
    import pandas as pd
    df = pd.read_excel('data.xlsx')
    print(df.head())
```