# Flow Control

There are two types of flow control statements supported by Python:

## 1. Conditionals

There are times in life when you need to make decisions, and these decisions depend on certain conditions. For example, suppose that you are in a class, then a decision that you might have to make would be:

$\color{red} \text{if} \; \color{yellow} \text{you have a pen,} \; \color{red} \text{then} \; \color{white} \text{you can write on a piece of paper,} \; \color{red} \text{else} \; \color{white} \text{you borrow a pen}$

Similarly, when writing a program, you might need to make decisions at some points in your code. Conditionals are decision making statements that can be used to chose which set of instructions to execute depending on given conditions.

### 1.1. The `#!py if else if` statement

An `#!py if else` statement is used whenever you need your program to make decisions. It executes one set of instructions `#!py if` a conditon is true or `#!py else` it executes another set of instructions.

Syntax:
```py
a = 10
b = 20
# if(boolean expression / variable / constant)
if b > a:
    # if the above condition is true do:
    print("does one thing")
    print("b > a confirmed!")
else:
    # if the above condition is not true do:
    print("does another thing")
    print("b <= a confirmed!")
```

when writing if else statements, an indentation, usually 4 spaces, is required. Python uses these indentations to understand what part of the code is inside the if/else.

An `#!py if` statement does not need to be followed by an `#!py else` statement everytime

```py
a = 10
b = 20
if b > a:
    print("doesn't do anything if the conditon is false")
```

What if you need to check multiple conditions and do separate things for each case? this is when you use an `#!py if else if` statement!

```py
a = 10
b = 20
if b > a:
    print("b > 20")
elif b == 20: # elif is short for else if
    print("b == 20")
else:
    print("no condition is true")
```

!!! question "What happens when multiple conditions are true?"
    In the above example, both the `#!py (b > a)` and `#!py (b == 20)` conditions are true. However, in an `#!py if else if` statement, only one branch of instructions is ever executed. Which condition takes proiority is decided by what order you write them in. So in this case, `#!py "b > 20"` will be printed to the screen because that is the first condition which is true.

    Technically, whenever a condition becomes true and its branch of instructions are executed, all of the remaining conditions are skipped, and not even evaluated.

=== "Practise"
    Now that you are armed with the power of `#!py if else if`, can you:
    
    Write a program that would print the maximum of 3 given variables.
    
    When you're ready, click the "Answer" to view the solution.

=== "Answer"
    Now that you are armed with the power of `#!py if else if`, can you:
    
    Write a program that would print the maximum of 3 given variables.
    
    When you're ready, click the "Answer" to view the solution.
    ```py
    a = 10
    b = 20
    c = 30
    if a > b and a > c:
        print("the maximum is a:", a)
    else if b > c and b > a:
        print("the maximum is b:", b)
    else:
        print("the maximum is c:", c)
    ```

## 2. Loops

There are times in life when you need to repeatedly keep doing something under certain conditions. For example, suppose that you are playing a game and you are stuck on a boss fight where you keep dying, something that you are doing might be:

$\color{red} \text{while} \; \color{yellow} \text{you have not defeated the boss,} \; \color{white} \text{try again}$

If you wanted to write out the times two table, you might do:

$\color{red} \text{for} \; \color{yellow} \text{every} \; \color{green} \text{number} \; \color{red} \text{between 1 and 10} \; \color{white} \text{write }2\times \color{green} \text{number}$

Similarly, when writing a program, it might be needed to repeat certain parts of your code multiple times. Loops are statements that can be used to repeatedly execute a block of code given a condition is true.

Sometimes the need arises to repeatedly execute the same statement or a statement where only a few things are changing.
Loops are statements that allow us to do exactly that! There are two types of loops suported by Python:

### 2.1. The `#!py while` loop

A `#!py while` statement repeatedly executes a block of code as long as (while) something is `#!py True`. This process of repeatedly executing the same block of code is known as iteration!
For example:

```py
a = 0
while a < 10:
    print("a =", a)
    a+=1
```

=== "Practise"
    Now that you are armed with the power of `#!py while`, can you:
    
    Write a program that would print the following pattern:

    `1, 2, 4, 7, 11, 16... up to 15 terms?`
    
    If you need help, but don't want to see the full solution immediately, click "Hint"

    When you're ready, click "Answer" to view the solution.

=== "Hint"
    Now that you are armed with the power of `#!py while`, can you:
    
    Write a program that would print the following pattern:

    `1, 2, 4, 7, 11, 16... up to 15 terms?`
    
    If you need help, but don't want to see the full solution immediately, click "Hint"

    When you're ready, click "Answer" to view the solution.

    Hint: Notice that the pattern here is that each time, the increase of the terms is also going up by one. The 2nd term is the first term + 1, the 3rd term is the 2nd term + 2, and so on.

=== "Answer"
    Now that you are armed with the power of `#!py while`, can you:
    
    Write a program that would print the following pattern:

    `1, 2, 4, 7, 11, 16... up to 15 terms?`
    
    If you need help, but don't want to see the full solution immediately, click "Hint"

    When you're ready, click "Answer" to view the solution.

    Hint: Notice that the pattern here is that each time, the increase of the terms is also going up by one. The 2nd term is the first term + 1, the 3rd term is the 2nd term + 2, and so on.

    ```py
    number = 1
    increase = 1
    while increase <= 15:
        print("number =", number)
        number = number + increase
        increase+=1
    ```

### 2.2. The `#!py for` loop

A `#!py for` statement is specifically used to loop over a range of values, say `#!py 5` to `#!py 23`

For example:
```py
for a in range(2, 23):
    print("a =", a)
# prints numbers from 3 to 22

# what if you wanted to go down from 10 to 0?
# that is also possible:
for a in range(10, 0):
    print("a =", a)

# you can also define a step size:
for a in range(10, 0, 3):
    print("a =", a)
# similar to slicing
```

For loops can also be used to loop through all the elements of a list, tuple or a dict:

With lists:
```py
ls = [5, 3, 56, 23]

for number in ls:
    print(number)
```

With tuples:
```py
my_tuple = (17, 32, 11, 64)

for number in my_tuple:
    print(number)
```

With dicts:
```py
my_dict = {3.14: "pi", "pie": "is tasty!", "spongebob": "squarepants"}

for key in my_dict:
    print(key, my_dict[key])
```

### 2.3. The `#!py break` statement

`#!py break` forces a loop to terminate earlier, even if its condition is still `#!py True`:

```py
a = 0
while a < 10:
    print("a =", a)
    a+=1
    if a == 5:
        break
```

This will just print:
```
0
1
2
3
4
```

Notice that the loop's condition is still `#!py True` at the end of this program

### 2.4. The `#!py continue` statement

`#!py continue` makes the loop immediately jump to its next cycle and skip any code after the `#!py continue`

```py
a = 0
while a < 5:
    if a == 2:
        continue
    print("a =", a)
    a+=1
```

This outputs:

```
0
1
3
4
```

Notice that printing the value `2` was skipped, but the others were still printed

### 2.5. The `#!py while else` statement

This is a unique feature of python that is not found in other programming languages. You can add an else block at the end of a while loop as follows:

```py
i = 0
while i < 3:
    print("while")
    i += 1
else:
    print("else")
```

What does this mean? If the condition of the while loop evaluates to `#!py False`, then the code in the `#!py else` block is executed. This is just like an `#!py if else` statement! So the above code will output:

```
while
while
while
else
```

But wait, doesn't that mean that an else block will ALWAYS run at the end of a loop when the loop condition eventually becomes `#!py False` for it to terminate? Yep! Now you might be asking, how is it any different from:

```py
i = 0
while i < 3:
    print("while")
    i += 1

print("else")
```

And the answer is, for this specific piece of code, there is no difference, and it should be written without the `#!py else`

The difference is when we terminate our loop by other methods, remember the `#!py break` statement?

```py
a = 0
while a < 10:
    print("a =", a)
    a+=1
    if a == 5:
        break
else:
    print("else")
```

This outputs:

```
0
1
2
3
4
```

### 2.6. The `#!py for else` statement

This works exactly like the `#!py while else` statement, where the `#!py else` block is only executed when the loop terminates without a `#!py break`

```py
for i in range(10):
    print(i)
    if i == 5:
        break
else:
    print("else")
```

This outputs:

```
0
1
2
3
4
5
```
