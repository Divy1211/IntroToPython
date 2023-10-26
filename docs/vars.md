# Python Basics

## 1. Constants

To do anything in a program, we need constants. Any value that remains the same throughout the execution of the program is known as a constant. Quite literally, it is a constant. For example, `#!py 10` is a constant. Every number is a constant.

## 2. Variables

Variables are like boxes that are used to store constants. Variables are values that can change during the execution of the program! Think about it this way, if a variable is a box that stores a constant, that constant can be taken out and another one can be put in. Quite literally, it is a variable (it may change!). For example:

```py
# creating and storing a value in a variable
# is known as variable initialisation

a = 10
b = 20.5
c = a+b

# a, b and c are the names of the variables here.

# to be able to see the value of a variable,
# we need to print it to the screen
print(c)

# you can change a variable simply by re-assigning another value to it:
c = a-b
print(c)
```

You can also store sentences, words:

```py
a = "this is a string"
print(a)
```

You can store lists as well:

```py
ls = [1, 4.5, "python is awesome!"]
print(ls)
```

## 3. Data Types

Remember, variables are like boxes/containers that are used to store constants. For every different kind of constant, a different type of contanier/box is required! Think about it this way, you cannot store water in a paper bag. you need a water bottle to store water. Similarly, in python, each different kind of constant must be stored in a different type of variable. The type of the variable is known as its data type. So how many kinds of boxes, or data types are there? The following are the most commonly used data types in python:

### 3.1. Integer (`#!py int` )

An `#!py int` quantity may be negative, positive, or zero. It never has any fractional or decimal parts (for example, an integer never has `#!py 0.5`).
Syntax: `#!py a = 10` This declares a variable of type `#!py int` called `a` with a value of `#!py 10`

### 3.2. Floating Point (`#!py float`)

A `#!py float` is a data type that can store values with fractional parts or decimals. For example `#!py 1.5` is a floating point value.

Syntax: `#!py a = 3.14159` This declares a variable of type `#!py float` called `a` with a value of `#!py 3.14159`

### 3.3. Boolean (`#!py bool`)

A `#!py bool` is a data type, that can only store one of two different values, `#!py True` or `#!py False`. Any yes or no question is a boolean question in some sense, because there are only two answers, yes or no (true or false). Boolean variables are super important for conditions, which we will be looking at later.

Syntax: `#!py a = True` This declares a variable of type `bool` called `a` with a value of `#!py True`

!!! info
    A value of `True` can also be indicated by `#!py 1` and a value of `False` can also be indicated by `#!py 0`.

### 3.4. String (`#!py str`)

An `#!py str` is a word, a phrase or a sentence. A string is always enclosed by double quotes.

Syntax: `#!py a = "this is a string! yay"` This declares a variable of type `str` called `a` with a value of `#!py "this is a string! yay"`.
You can also use single quotes for declaring strings:
`#!py a = 'this is a string! yay'`

!!! question "String with multiple lines?"
    You might be tempted to do something like this:
    ```py
    a = "this is\na multiple line\nstring"
    # \n is a special character that represents a new line or an "enter" press in a string
    ```

    But there is a better way:
    ```py
    a = """this is
    a multiple line
    string"""

    print(a)
    
    b = '''this is
    another multiple line
    string'''
    
    print(b)
    ```

what if you want to obtain the letter in a particular position in a string?

```py
a = "python is awesome"
print(a[0])
# this will give you the first letter of the string
# in any programming language in general,
# when we number items, we always start at 0 and not 1


# in python, you can actually use a negative index:
print(a[-1])
# and this gives you the last character of a.
```

What if you want to obtain a particular part of the string?

```py
b = "this is known as slicing"
print(b[4:8])
# this will give you a string that starts from the
# 5th character of b and ends at the 9th character.
# Note that the 9th letter is not included in this new sliced string
# result: " is k"

print(b[3:])
# this will give you a string that starts from the 4th character of b
# result: "s is known as slicing"

print(b[:5])
# this will give you a string that ends at the 6th character of b.
# Note that the 6th character is not included in this new sliced string
# result: "s is known as slicing"

print(b[2:10:3])
# this will give you a string that starts from the 
# 3rd character of b and ends at the 11th character.
# Note Only the every 3rd character is selected, starting from the first.
# result: "iik"

print(b[::-1])
# this will give you a string that is the reverse of the original!
# result: "gnicils sa nwonk si siht"

print(len(b))
# gives you the length of the string
```

You can also join two or more strings togethere:
```py
a = "this is "
b = "known as string"
c = " concatenation!"
print(a+b+c)
```

What would happen if you tried to access a poition of the string that is greater than its length?

```py
a = "this is a string"
print(a[20])
# the string does not have a 21st character,
# you will get an error if you try this!
```

### 3.5. List (`#!py list`)

A `#!py list` is an ordered collection of different constants. Each member of a list is formally called an element of that list.

Example: 
```py
a = [2, 3.4, "this is a list", True, ["this list is inside the first one", ":O"]]
```

This declares a variable of type `list` called `a` with the following values:

| Index | Value                                              |
| :-:   | :-:                                                |
| 0     | `#!py 2`                                           |
| 1     | `#!py 3.4`                                         |
| 2     | `#!py "this is a list"`                            |
| 3     | `#!py True`                                        |
| 4     | `#!py ["this list is inside the first one", ":O"]` |

Also, in general when initialising a list, if the list is too long to fit in one line, it is common to break it up over multiple lines to increase visibility, like so:

```py
a = [
        2,
        3.4,
        "this is a list",
        True,
        ["this list is inside the first one", ":O"]
    ]
```

To obtain an element from a list, the same syntax as a string is used:
```py
a = [1, 2, 3, 4, 5, 6, 7, 8, 9, [10, 20, 30]]
print(a[0])
# this will give you the first element of the list

print(a[-1])
# and this gives you the last element of this (this is a list in itself)

print(a[4:8])
# slicing also works exactly like strings.
# this will give you a list starting from the
# 5th element all the way to the 9th element.

print(len(a))
# this gives you the number of elements in a list.

# you can change any element of the list like so:
a[2] = 55

# change the 2nd element of the last element of the list
a[-1][1] = 22
```

you can combine lists as follows:

```py
a = [1, 2]
b = [3, 4]
c = [5, 6]

print(a+b+c)
```

you can add an element to a list using the append function:

```py
a = [1, 2]
a.append(3)
print(a)
```

you can extend a list using another list by using the extend function:

```py
a = [1, 2]
b = [3, 4]
a.extend(b)
print(a)
```

What would happen if you tried to access an element of the list whoes index is greater than the length?

```py
a = "this is a string"
print(a[20])
# the string does not have a 21st character,
# you will get an error if you try this!
```

### 3.6. Tuple (`#!py tuple`)

A `#!py tuple` is exactly like a list. The only difference is that once a tuple is initialised, its elements cannot be altered. Technically, we say that a tuple is immutable.

Example:
```py
a = (2, 3.4, "this is a tuple", True, ("this tuple is inside the first one", ":O"), ["this is a list inside the tuple", "o.O"])
```

Similar to a list, it is common to break up a long tuple over multiple lines:

```py
a = (
        2,
        3.4,
        "this is a tuple",
        True,
        ("this tuple is inside the first one", ":O"),
        ["this is a list inside the tuple", "o.O"]
    )
```

This declares a variable of type `tuple` called `a` with the following values:

| Index | Value                                               |
| :-:   | :-:                                                 |
| 0     | `#!py 2`                                            |
| 1     | `#!py 3.4`                                          |
| 2     | `#!py "this is a tuple"`                            |
| 3     | `#!py True`                                         |
| 4     | `#!py ("this tuple is inside the first one", ":O")` |
| 5     | `#!py ["this is a list inside the tuple", "o.O"]`   |

To obtain an element from a tuple, the same syntax as a list/string is used:

```py
a = (1, 2, (3, 4, 5), [1, 2, 3])
print(a[0])
# this will give you the first element of the tuple

print(a[-1])
# and this gives you the last element of this tuple

print(a[0:3])
# slicing also works on tuples.
# this will give you a tuple starting from the 
# first element all the way to the 3rd element.

# note that you cannot change the elements of a tuple.
# trying to do that will get you an error

# however, you CAN change a list inside a tuple.
a[-1][2] = 10
```

### 3.7. Dictionary (`#!py dict`)
A `#!py dict` is a data type that can store "key-value" pairs. It essentially creates a map between specifed values.

The constants to the left are called keys, and the constants to the right are called values.

Example:
```py
a = {
    "this is a key": "this is it's value",
    3.14: "pie",
    4: "2x2",
    (2, 3): "a tuple!",
}
```

!!! note "Best Practice"
    like a list or a tuple, you could write the above out in one line:

    ```py
    a = {"this is a key": "this is it's value", 3.14: "pie", 4: "2x2", (2, 3): "a tuple!"}
    ```

    But that is so much worse for readability! Dicts are conventionally almost always never written like that, its always a good idea to write each key-value pair of a dict out on a separate line

So how do you actually use a dictionary?

```py
a = {
    "this is a key": "this is it's value",
    3.14: "pie",
    4: "2x2",
    (2, 3): "a tuple!",
}
print(a["this is a key"])
print(a[3.14])
print(a[4])
print(a[(2, 3)])

# Similar to a list or tuple, you will get an
# error from python if you try to access a key
# that is not present in a dictionary

# you can also use the get function to get values:
print(a.get(3.14))

# you can actually specify a default value when using get
# this is, in case the key is not in the dictionary,
# then use the default value instead!

print(a.get(22, "not found"))
```

```py
a = "this is a string"
print(type(a))

a = 2.2
print(type(a))

a = [1, 2]
print(type(a))

a = 2
print(type(a))

a = (4, 5)
print(type(a))

a = True
print(type(a))
```

Remember that your variable names can be almost anything! However, this does not mean that you should just use single letters or alphabets for variable names. Variable names should be chosen such that they represent, or hint to what the purpose of the variable is. Naming your variables such that they make intuitive sense is a good programming practise.


## 4. Variable Naming Rules and Conventions:

There are some rules that must be followed when naming a variable. They are:

1. You can only use letters, numbers and underscores to name your variables.

2. A variable name cannot start with a number.

3. Variable names are `CaSe SeNsItIvE`. This means that `a` and `A` are two different variable names!

4. Variable names must not be keywords. A keyword is a reserved word in any programming language that has a special meaning! For example, `#!py int` is a keyword in Python because it is the name of a data type.

While these are the only *laws* that you absolutely must follow, there are some conventions or *unwritten rules* that all programmers agree to follow to make their code more readable, and more clear.

1. When you are writing a variable name that is just one word, it is conventional to write it in all small letters. For example `#!py radius = 10` or `#!py name = "John Cena"`.

2. When you are writing a variable name that consists of more than one word, then it is conventional to write it in a special case known as "snake case". Snake case is where the every word is written in small letters separated by underscores. For Example: `#!py gear_ratio = 2.2` or `#!py first_name = "Bruce"` or `#!py last_name = "Wayne"`.

3. When you are writing a variable that is supposed to just store the value of a constant, one which you never intend to change, it is conventional to use capital letters and words are separated by underscores. For example: `#!py PI = 3.14159` or `#!py GOLDEN_RATIO = 1.61803`.

4. Variable names should be precise and mnemonic. That is, they should indicate to a casual programmer their purpose. Usage of single letter variable names is discouraged unless it is a throwaway or temporary variable.