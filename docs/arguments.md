
# Different types of arguments

In python, there are 6 different types of arguments that a function can take. They are:

## 1. Required Arguments
These are arguments that MUST ALWAYS be passed to the function.

```py
def add(a, b):
    # a and b are required arguments
    return a+b

print(add(3, 5))
# prints 8
```

## 2. Optional Arguments
These are arguments that may not be passed to the function.

```py
def add(a, b, c = 0):
    # a and b are required arguments while c is an optional argument. All arguments initialised with a default value are optional
    return a+b+c

print(add(3, 5))
# prints 8

print(add(3, 5, 5))
# prints 13
```

Note: All optional arguments are always written after the positional arguments in the function prototype

## 3. Positional Arguments
These are arguments that are passed using their position to the function.

```py
def simple_interest(principle, rate, time):
    # principle, rate and time are all required arguments
    return principle*rate/100*time

# since they are passed to the function by their position, i.e. principle is 1000, rate is 15 and time is 5 
print(simple_interest(1000, 15, 5))
# prints 750.0
```

Note: In the example in point 2, the variable `c` is a positional argument that is optional!

## 4. Keword Arguments
These are arguments that are passed using their name to the function.

```py
def simple_interest(rate, time, principle = 100):
    # rate and time are all required arguments while principle is an optional argument with a default value of 100
    return principle*rate/100*time

# since they are passed to the function 
print(simple_interest(rate = 15, principle = 1000, time = 5))
# prints 750.0

print(simple_interest(15, 5))
# prints 75.0

print(simple_interest(15, principle = 1000, time = 5))
# prints 750.0
```

Note1: Keyword arguments are always passed to the function after positional arguments!

Thus, `simple_interest(15, time = 5, 1000)` isn't allowed, but `simple_interest(15, 5, principle = 1000)` is

Note2: An argument cannot be called as both a positonal and a keyword argument IN THE SAME function call! `simple_interest(15, 5, rate = 15)` would not be valid since it calls rate as both a positional and a keyword argument

## 5. Arbitrary Arguments(*args)
When an unknown or "arbitrary" number of arguments are passed to a function, they are known as Arbitrary Arguments

```py
def add_multiply(*nums, multiply = 1):
    # nums is a required argument. the * denotes that it will accept an arbitrary number of arguments.
    # nums will be a list of all the arguments provided
    sum = 0
    for num in nums:
        sum+=num
    return sum*multiply

# add up all these numbers
print(add_multiply(5, 6, 2, 4, 2))
# prints 19

# add up all these numbers and also multiply by 2
print(add_multiply(5, 6, 2, 4, 2, 3, 5, multiply = 2))
# prints 54
``` 

Note1: Other arguments may follow an arbitrary argument but then that argument MUST ALWAYS be called as a keyword argument

Note2: Other positional arguments may preceed an arbitrary argument

Note3: An arbitrary argument CANNOT be called as a keyword argument!

## 6. Arbitrary Keyword Arguments(**kwargs)
When an unknown or "arbitrary" number of keyword arguments are passed to a function, they are known as Arbitrary Keyword Arguments

```py
def display_works(author, **works):
    # works is a required argument. the ** denotes that it will accept an arbitrary number of keyword arguments.
    # works will be a dictionary of all the keyword arguments and their values provided.
    for key in works:
        print(f"({key}, {works[key]})")
    print(author)

display_works("Roald Dahl", book1="Charlie and the Chocolate Factory", book2="Matilda")
``` 

Note1: No arguments can follow arbitrary keyword arguments.

Note2: Any number of keyword or positional arguments can preceed arbitrary keyword arguments.

```py
def add_multiply(*nums, multiply = 1):
    # nums is a required argument. the * denotes that it will accept an arbitrary number of arguments.
    # nums will be a list of all the arguments provided
    sum = 0
    for num in nums:
        sum+=num
    return sum*multiply

# add up all these numbers
print(add_multiply(5, 6, 2, 4, 2))
# prints 19

# add up all these numbers and also multiply by 2
print(add_multiply(5, 6, 2, 4, 2, 3, 5, multiply = 2))
# prints 54
```