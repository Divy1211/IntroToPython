
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

!!! info "Order, Order"
    All optional arguments are always written after the positional arguments in the function prototype. This is not a valid function:
    ```py
    def add(c = 0, a, b): ...
    ```

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

!!! note "Optional Positional Arguments"
    In the example in point 2, the variable `c` is a positional argument that is optional!

## 4. Keyword Arguments
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

!!! info "Order, Order"
    Keyword arguments are always passed to the function after positional arguments!

    Thus, `#!py simple_interest(15, time = 5, 1000)` isn't allowed, but `#!py simple_interest(15, 5, principle = 1000)` is

!!! warning "Duplicate Arguments"
    An argument cannot be called as both a positional and a keyword argument IN THE SAME function call! `#!py simple_interest(15, 5, rate = 15)` would not be valid since it calls rate as both a positional and a keyword argument

## 5. Arbitrary Arguments(*args)
When an unknown or "arbitrary" number of arguments are passed to a function, they are known as Arbitrary Arguments

```py
def add_multiply(*nums, multiply = 1):
    # nums is a required argument. the * denotes that it will accept an arbitrary number of arguments.
    # nums will be a tuple of all the arguments provided
    sum_ = 0
    for num in nums:
        sum_+=num
    return sum_*multiply

# add up all these numbers
print(add_multiply(5, 6, 2, 4, 2))
# prints 19

# add up all these numbers and also multiply by 2
print(add_multiply(5, 6, 2, 4, 2, 3, 5, multiply = 2))
# prints 54
``` 

!!! note "Order, Order"
    Other arguments may follow an arbitrary argument but then that argument MUST ALWAYS be called as a keyword argument

    Other positional arguments may precede an arbitrary argument

!!! warning "Arbitrary Argument is Always Positional"
    An arbitrary argument CANNOT be called as a keyword argument!

!!! warning "Arbitrary Argument is Always Unique"
    There can be only one arbitrary keyword argument in a function

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

!!! note "Order, Order"
    No arguments can follow arbitrary keyword arguments.

    Any number of keyword or positional arguments can precede arbitrary keyword arguments.


!!! warning "Arbitrary Argument is Always Unique"
    There can be only one arbitrary keyword argument in a function

```py
def add_multiply(*nums, multiply = 1):
    # nums is a required argument. the * denotes that it will accept an arbitrary number of arguments.
    # nums will be a list of all the arguments provided
    sum_ = 0
    for num in nums:
        sum_+=num
    return sum_*multiply

# add up all these numbers
print(add_multiply(5, 6, 2, 4, 2))
# prints 19

# add up all these numbers and also multiply by 2
print(add_multiply(5, 6, 2, 4, 2, 3, 5, multiply = 2))
# prints 54
```

## 7. Positional only arguments

Normal arguments of a function can be called either positionally or by name. If you wish to make an argument only callable by its position, you can do so

```py
def simple_interest(principle, /, rate, time):
    # any arguments preceding a / are ALL position only arguments
    # principle is now a position only argument
    return principle*rate/100*time

# the first argument is always the principle
print(simple_interest(1000, 15, 5)) # rate = 15 and time = 5
# prints 75.0

# this is a syntax error: 
simple_interest(rate = 15, principle = 1000, time = 5)

# rate and time can still be called by name
print(simple_interest(1000, time = 5, rate = 15))
# prints 75.0
```

## 8. Keyword only arguments

If you wish to make an argument only callable by its name, you can also do so

```py
def simple_interest(principle, /, rate, *, time):
    # any arguments after a * are ALL keyword only arguments
    return principle*rate/100*time

print(simple_interest(1000, 15, time = 5))
# prints 75.0

# this is a syntax error: 
print(simple_interest(1000, 15, 5)) # time cannot be called as a positional argument

# rate can be called anyhow:
print(simple_interest(1000, time = 5, rate = 15))
# prints 75.0
```

!!! note
    These can be mixed with optional parameters
    ```py
    def some_interest(principle = 1000, /, rate = 15, *, time, multiplier = 2): ...

    # valid calls:
    some_interest(time = 10)
    some_interest(rate = 10, time = 2)
    some_interest(10_000, 20, time = 10) # principle = 10k, rate = 20
    some_interest(time = 10, multiplier = 1)
    ```
