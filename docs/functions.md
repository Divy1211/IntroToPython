# Functions

## 1. What are functions and why do we need them?

Lets say that you are watching TV. Every time you want to change the channel, you will use the same remote control. It would be quite inconvenient if you had to make a new remote control each time you wanted to change the channel. Similarly, in programming, you might want to write a piece of code that you need to re-use multiple times in different parts of your program.

For example, lets say that you write a program to find the largest number in a list:
```py
list_of_numbers = [32, 88, 3, 48, 87, 22]
maximum = list_of_numbers[0]

for number in list_of_numbers:
    if maximum < number:
        maximum = number
print(maximum)
```

But what if you need to find the largest value in 10 different lists? Would it be feasable to rewrite the same code again 10 different times? This is where functions come into the picture. They allow you to re-use the same piece of code again and again, however many times you might want.

More formally, A function is a block of code that allows you to to perform a specific action. It is modular, and re-usable as many times as you want. Some functions might even give you back a value.

For example, the same code written using functions would look something like:

```py
# this line is known as the function prototype.
# the variables inside the brackets are known as formal parameters or formal arguments
def max_value(list_of_numbers):

# the word 'def' is short for define. It means you are defining a function called 'max_value'

# In python, it is a convention to write function names in 'snake case'
# snake case means that the each word is in lower case, and separated by underscores.
# Example: this_is_snake_case

    maximum = list_of_numbers[0]

    for number in list_of_numbers:
        if maximum < number:
            maximum = number

    # the word 'return' here tells python that this function needs to give you back the value of 'maximum'
    return maximum
list1 = [32, 88, 3, 48, 87, 22]
list2 = [44, 26, 56, 90, 12, 35]
list3 = [96, 43, 30, 12, 37, 26]


# this is known as a function call and the variables passed to the function are called actual parameters or actual arguments
max1 = max_value(list1)
max2 = max_value(list2)
max3 = max_value(list3)

print(max1)
print(max2)
print(max3)
```

A function does not have to necessarily return a value:

```py
def display_elements(a_list):
    for element in a_list:
        print(element)

list1 = [32, 88, 3, 48, 87, 22]
list2 = [44, 26, 56, 90, 12, 35]
list3 = [96, 43, 30, 12, 37, 26]

print(display_elements(list1))
print(display_elements(list2))
print(display_elements(list3))
```
Output:
```py
32
88
3
48
87
22
None
44
26
56
90
12
35
None
96
43
30
12
37
26
None
```

Why does it print a `None` between the elements of the lists? Remember, these functions don't return any values! Thus, `print(displayElementsOf(list1))` doesn't actually have something to print!

Note: A function does not execute the rest of its code if a return statement is encountered

```py
def function(number):
    return number*2
    print(number/2)

print(function(5))
```
Output:
```
10
```

=== "Practise"

    Write a function to calculate the factorial of a number.
    Use the function to then find the factorials of all the numbers from 1 to 20

    Note: The factorial of a number n, represented by n! is given by: $n! = n\cdot(n-1)\cdot(n-2)...1$. For example, $5! = 5\cdot4\cdot3\cdot2\cdot1 = 120$ and $0! = 1$.

=== "Answer"
    Write a function to calculate the factorial of a number.
    Use the function to then find the factorials of all the numbers from 1 to 20

    Note: The factorial of a number n, represented by n! is given by: $n! = n\cdot(n-1)\cdot(n-2)...1$. For example, $5! = 5\cdot4\cdot3\cdot2\cdot1 = 120$ and $0! = 1$.

    ```py
    def factorial(a):
        facto = 1
        for i in range(1, a+1):
            facto*=i
        return facto

    for number in range(1, 21):
        print("the factorial of", number, "=", factorial(number))
    ```

## 2. Type Hints

When writing functions with a lot of parameters and variable names that might be unintuitive, it is a good idea to use type hints! type hints allow the person writing the function to tell the user what the expected data types of all the arguments being passed into it are

For example:

```py
# this tells the user than height is a float, weight
# is an int and that this function is meant to return a float as well
def calculateBMI(height: float, weight: int) -> float:
    return weight/((height/100)**2)

print(calculateBMI(182, 80))
```

## 3. What is recursion, and why do we need it?

Lets take the factorial from the previous excersie as an example.

We have learnt that n! = n\*(n-1)\*(n-2)\*...\*1

Similarly, (n-1)! = (n-1)\*(n-2)\*...\*1

But, notice that from these two equations we can actually write that n! = n\*(n-1)!

So if you were being introduced to the factorial for the first time, and you were just told that n! = n\*(n-1)! would this be enough information to find out the factorial of any number? Try computing 3! just by using the definition that n! = n*(n-1)!.

If you actually tried to do that, you would realise that its actually not possible because with that definition, you don't know when to stop!

3! = 3*2!

2! = 2*1!

1! = 1*0!

0! = 0*(-1)!

...

This means that other than the fact that n! = n*(n-1)! we also need a point to stop at. Lets say that you are now told that 0! = 1. With that information in mind, we can actually compute 3!

3! = 3*2!

2! = 2*1!

1! = 1*0!

and now, we know that 0! = 1, so now we use that in the last equation and work our way back up!

1! = 1 and then using this, 2! = 2, and then using this, it is found that 3! = 6

This process of defining a process in its own terms is known as recursion! The "stopping point" at which we stop going down and start to work back up is known as the base case! So can we do something like this with functions? Yes!

```py
def factorial(number):

    # remember to write a base case!
    # If you forget, you're program will be stuck
    # in an infinite loop of recursion!
    if number == 0:
        return 1
    # the recursive case:
    return number*factorial(number-1)
```

=== "Practise"

    What does the following piece of code output? You are not allowed to type this into an IDE and run the code. Try to work it out by hand!

    ```py
    def function(number):
        if number >= 1:
            print(number)
            function(number-1)
        print(number)

    function(3)
    ```

    If you need help, but don't want to see the full solution immediately, click "Hint"


=== "Hint"

    What does the following piece of code output? You are not allowed to type this into an IDE and run the code. Try to work it out by hand!

    ```py
    def function(number):
        if number >= 1:
            print(number)
            function(number-1)
        print(number)

    function(3)
    ```

    If you need help, but don't want to see the full solution immediately, click "Hint"

    Hint: A function will always execute ALL of its code UNLESS a return statement is encountered. If another function call is encountered inside a function, it will first complete the code of that function before continuing with the rest of its own code.

=== "Answer"

    What does the following piece of code output? You are not allowed to type this into an IDE and run the code. Try to work it out by hand!

    ```py
    def function(number):
        if number >= 1:
            print(number)
            function(number-1)
        print(number)

    function(3)
    ```

    If you need help, but don't want to see the full solution immediately, click "Hint"

    Hint: A function will always execute ALL of its code UNLESS a return statement is encountered. If another function call is encountered inside a function, it will first complete the code of that function before continuing with the rest of its own code.

    Output:

    ```py
    3
    2
    1
    0
    1
    2
    3
    ```