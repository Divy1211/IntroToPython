# Operators

Now that we know how to store and change the values of a variable, what can we actually do with them?

## 1. Arithmetic Operators

The most obvious thing that we can do with numbers, is do arithmetic with them. Python supports the following arithmetic operations:


| **Operator**  | **Name**         | **Example**  |
| :-:           | :-:              | :-:          |
| `#!py +`      | Addition         | `a+b`        |
| `#!py -`      | Subtraction      | `a-b`        |
| `#!py *`      | Multiplication   | `a*b`        |
| `#!py /`      | Division         | `a/b`        |
| `#!py //`     | Integer Division | `a//b`       |
| `#!py %`      | Modulo           | `a%b`        |
| `#!py **`     | Exponentiation   | `a**b`       |

!!! question "What is integer division?"
    Integer division gives you the quotient of the division. For example: `17/6 = 2.833` but `17//6 = 2`. Modulo on the other hand, gives you the remainder of a division.

## 2. Relational Operators

Relational operations allow us to compare variables with one another. With these, you can find out if one variable is greater than another, if two variables are equal, and much more.

If you have two numbers
$\color{yellow} \text{A}$ and $\color{yellow}\text{B}$,
and are asked
"$\text{if} \; \color{yellow}\text{A} \; \color{red} \text{is greater than} \; \color{yellow}\text{B} \color{white}$?"
then you can have only two possible answers, it will either be yes or no. Similarly, if you are asked
"$\text{if} \; \color{yellow}\text{A} \; \color{red} \text{is equal to} \; \color{yellow}\text{B} \color{white}$?"
then this question also has only two answers, yes or no.

Whenever you use a relational operator, it is like asking one of these questions above. Then how does a computer answer a question like this? Do you remember the data type that can only store one of two different values?

A `boolean` data type can either be `True` or `False`, it does exactly this! Thus, the answers to all relational operations give you boolean values.

| **Operator**   | **Name**                 | **Example**   |
| :-:            | :-:                      | :-:           |
| `#!py <`       | Less Than                | `a<b`         |
| `#!py >`       | Greater Than             | `a>b`         |
| `#!py <=`      | Less Than or Equal to    | `a<=b`        |
| `#!py >=`      | Greater Than or Equal to | `a>=b`        |
| `#!py ==`      | Equal to                 | `a==b`        |
| `#!py !=`      | Not Equal to             | `a!=b`        |

1. `a < b` This checks if the number `a` is lesser than `b`. If it is, then the expression evaluates to `True`, else it evaluates to `False`.
2. `a > b` This checks if the number `a` is greater than `b`. If it is, then the expression evaluates to `True`, else it evaluates to `False`.
3. `a <= b` This checks if the number `a` is lesser than or equal to `b`. If it is, then the expression evaluates to `True`, else it evaluates to `False`.
4. `a >= b` This checks if the number `a` is greater than or equal to `b`. If it is, then the expression evaluates to `True`, else it evaluates to `False`.
5. `a == b` This checks if the number `a` is equal to `b`. If it is, then the expression evaluates to `True`, else it evaluates to `False`.
6. `a != b` This checks if the number `a` is not equal to `b`. If it is, then the expression evaluates to `True`, else it evaluates to `False`.

!!! info "String comparisons"
    These relational operators also work on `String` values, for example `a < b` checks if `a` would alphabetically preceed `b`.

For Example:

```py
# with numbers:
 a = 10
 b = 20.0
 c = 30
    
# this would print True
print("a < b is", a < b)

# this would print False
print("b > c is", b > c)

# this would print True
print("(a+b) == b is", (a+b) == b)

# this would print True
print("(a+b) >= c is", (a+b) >= c)

# this would print True
print("b <= c is", b <= c)


# With Strings:
str1 = "ball"
str2 = "apple"
str3 = "cat"
str4 = "cat"

# this would print False
# this is because alphabetically, str1 does not come before str2
print("str1 < str2 is", str1 < str2)

# this would print False
# this is because alphabetically, str2 comes before str3
print("str3 > str2 is", str3 > str2)

# this would print True
print("str3 == str4 is", str3 == str4)

# this would print True
print("str1 != str2 is", str1 != str2)
```

## 3. Boolean Operators

If two or more things are required to do a task, we can say that "this AND that are required to do the task". For example:

To write an email to someone, you must
"$\color{yellow} \text{have a computer} \; \color{red} \text{and} \; \color{yellow} \text{have active internet}$"
To paint something, you must
"$\color{yellow} \text{have a paper} \; \color{red} \text{and} \; \color{yellow} \text{have paint} \; \color{red} \text{and} \; \color{yellow} \text{have a paint brush}$"

Similarly, if only one, or more things are required to do a task we say that "this OR that is needed to do the task". For example:

To play a video game, you need to
"$\color{yellow} \text{own a computer} \; \color{red} \text{or} \; \color{yellow} \text{own a gaming console}$"
Note that you can still play video games if you own both!

To draw something you must
"$\color{yellow} \text{have a pencil} \; \color{red} \text{or} \; \color{yellow} \text{have a pen} \; \color{red} \text{and} \; \color{yellow} \text{have a paper}$"

Boolean operations allow us to ask these sorts of questions but with boolean values instead. For example, if you wanted to ask "is A greater than B and C?" then you require boolean operations.

### 3.1. The Boolean AND

Boolean AND: This is used to check if two or more boolean values are simultaneously `True`.

Usage: `#!py a and b` (Here, `a` and `b` are boolean variables)

This checks if both `a` **AND** `b` are `True`. If they are, the expression evaluates to `True`, otherwise it evaluates to `False`.

Every combination of inputs and outputs for `a and b` can be written in a table:

| **a** | **b** | **a and b** |
| :---: | :---: | :---:       |
| False | False | False       |
| False | True  | False       |
| True  | False | False       |
| True  | True  | True        |

!!! info "AND with more than two values"
    AND is not limited to just two variables. Any number of variables may be AND-ed together.
    For Example: `#!py a and b and c and d`. For this expression to evaluate to True, ALL of `a`, `b`, `c` and `d` must be True.

    Can you write a table for all possible combinations of inputs and output for this expression?

### 3.2. The Boolean OR

Boolean OR: This is used to check if one or more booleans are `True`.

Usage: `#!py a or b` (Here, `a` and `b` are boolean variables)

This checks if either `a` **or** `b` is `True`. If one of them is, then the expression evaluates to `True`, else it evaluates to `False`.

Every combination of inputs and outputs for `a or b` can be written in a table:

| **a** | **b** | **a \|\| b** |
| :---: | :---: | :---:        |
| False | False | False        |
| False | True  | True         |
| True  | False | True         |
| True  | True  | True         |

!!! info "OR with more than two values"
    OR is not limited to just two variables. Any number of variables may be OR-ed together.
    For Example: `#!py a or b or c or d`. For this expression to evaluate to True, only one of `a`, `b`, `c` and `d` needs to be True.

    Can you write a table for all possible combinations of inputs and output for this expression?

!!! info "Combining ANDs and ORs"
    ANDs and ORs can be used together in the same expression. For example:
    
    `#!py (a or b) and c`: for this expression to be `#!py True`, either `a` or `b` and `c` must be `#!py True`.
    
    `#!py a or (b and c)`: for this expression to be `#!py True`, either `a` must be `#!py True`or `b` and `c` must be `#!py True` simultaneously.
    
    !!! danger "ANDs are always evaluated before ORs"
        What does this expression mean? `#!py a or b and c`

        1. a or b... and c?
        2. a or... b and c?

        If no brackets are used when writing these expressions, the AND parts of an expression are evaluated first. Thus, the above expression means the second statement in English!

        In that example, it might be easy to remember but what if we have something more complicated? `#!py a or b and c or d and e`. It's the same as `#!py a or (b and c) or (d and e)`.

        To make it absolutely clear as to what you mean when writing a boolean expression, you should ALWAYS use brackets appropriately for clarity, even when it is not necessary to do so.

For example:
```py
a = 10
b = 20
c = 30

# this would print True on the screen
# because both a < b and c > d are True
print((a < b) and (c > b))

# this would print False on the screen
# because c < b is False
print((a < b) and (c < b))

# this would print True on the screen
# because a < b is True
print((a < b) or (c < b))

# this would print False on the screen
# because neither a > b nor  c < b is True
print((a > b) or (c < b))
```

## 4. Membership Operators

These are used to test if a certain sequence is present in an object. For example:

```py
print("water" in "this is a waterbottle")
print("water" not in "this is a waterbottle")
print("spongebob" in "squarepants")
print("spongebob" not in "squarepants")

# they also work on lists, tuples and dicts:

print(5 in [5, 3, 1, 2, 7])
print(11 not in [1, 2, 6, 7])

print(17 in (15, 12, 16, 19, 17))
print(16 not in (14, 17, 11, 21))

# for dicts, it checks if a certain key is present in the dict
print(3.14 in {3.14: "pi"})
print(5 in {3.14: "pi"})
```

## 5. The Assignment Operation

When we use the `=` sign in programming, it is not a mathematical equality statement. It actually tells us that we are assigning a value to a variable. So when you see something like `#!py a = a+1;`, this means that you are simply adding `#!py 1` to the value of `a`. you are assigning the value `#!py a+1` to `a`. Once again, it is not a mathematical equality statement, it is an assignment.

## 6. Shorthand Assignment Operators

Shorthand assignment operators allow us to assign values to variables:

| **Operator**   | **Name**         | **Example** | **Non Short Hand Equivalent** |
| :-:            | :-:              | :-:         | :-:                           |
| `#!py +=`      | Addition         | `a+=b`      | `a = a+b`                     |
| `#!py -=`      | Subtraction      | `a-=b`      | `a = a-b`                     |
| `#!py *=`      | Multiplication   | `a*=b`      | `a = a*b`                     |
| `#!py /=`      | Division         | `a/=b`      | `a = a/b`                     |
| `#!py //=`     | Integer Division | `a//=b`     | `a = a//b`                    |
| `#!py %=`      | Modulo           | `a%=b`      | `a = a%b`                     |
| `#!py **=`     | Exponentiation   | `a**=b`     | `a = a**b`                    |


!!! info "Identity and Bitwise operators"
    There are two more types of operators, Identity Operators and Bitwise Operators. They are out of the scope of today's session, but if you are curious, you can look them up!