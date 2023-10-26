# Classes and Objects

## 1. What is Object Oriented Programming, and why do we need it?

We come across a lot of different objects in our daily life. Each object has its own properties, some features that define it.

Lets take a pen for example. What are the properties of a pen? Its colour, its size, its kind (ball-point, fountain-point, gel-ink) and maybe the name of its owner.

Another example is a textbook. A textbook has a size, it has a subject, it has a length (the number of pages) and it has some information inside of it. Now the information inside a textbook is organised into named chapters.

For example, a maths text book might contain chapters like "sets", "trigonometery", "calculus" and so on, and if you want someone to read or go through a chapter, you'd say something like "go through the chapter on calculus".

Now imagine that you are a programmer who wants to write code that describes a pen, or a textbook... how could you go about writing code that expresses these properties discussed above?

You might try writing code that looks similar to this:

```py
pen_colour = "red"
pen_size = 0.5
pen_kind = "ball"
pen_owner = "John"

# wouldn't you want a way to see the info about your pen? Lets write a function to do that!
def display_information(colour, size, kind, owner):
    print("Colour :", colour)
    print("Size   :", size)
    print("Kind   :", kind)
    print("Owner  :", owner)
    print()

display_information(pen_colour, pen_size, pen_kind, pen_owner)
```
Sure, that would work for one pen, but some questions one might have are:

1. What if you wanted to make an unknown number of pens? How would someone know how many variables to declare?
2. What if you had a more complicated object with 100 properties? Would it be feasable to manually declare 100 variables for every object that you might need to create?

This is where classes come into the picture. So far we have learnt about the primitive data types in python, primitive meaning that they are in-built, simple data types which python provides to us. Now we are moving on to custom data types, data types that are defined by you, the programmer!

## 2. What are classes, and why do we need them?

So now, we want to create our own data types, a data type that would allow us to describe a pen, or any other object effectively, using code. This is exactly what a class allows us to do!

A class is basically a blue-print for creating an object, it tells us the defining properties of the object, and it also tells us what functions the object can perform. Following the class blue-print allows us to create "instances" of that class.

An object of a class, the realisation of the blueprint, is known as an instance of the class.

```py
class Pen:

    # remember the properties of the pen we discussed? A colour, a size, a kind, an owner
    
    def __init__(pen, col, sz, knd, own):
        pen.colour = col
        pen.size = sz
        pen.kind = knd
        pen.owner = own

    # This special function __init__ is known as a constructor, this is the "method" by which the object will be "constructed",
    # this is the essence of the blue-print!


    # wouldn't you want a way to see the properties of a pen you made as well?
    # you can write functions in a class that can work with the instances of the class. These functions are known as 'member
    # functions' of the class or 'methods'.

    # methods are always functions that work on objects of a specific class. A method cannot be used without an object

    # All methods of a class are unique to that class, and cannot be used on objects from other classes!
    # for example, you could have a method called read() that reads the contents of a text book but you
    # cannot use that method on a pen, because it doesn't make sense to read a pen!
    def display_information(pen):
        print("Colour :", pen.colour)
        print("Size   :", pen.size)
        print("Kind   :", pen.kind)
        print("Owner  :", pen.owner)
        print()

# But a class is just a blue-print for creating a pen, it tells us which properties a pen is supposed to have
# But it is NOT the pen itself!
# To actually create a pen, we need to use the blue-print and specify all the properties of the specifc pen we want to create:

A = Pen("red", 0.5, "marker", "John")
# When we do this, python calls the constructor and says, hey constructor,
# construct me a Pen with its colour as "red", its size as 0.5, its kind as "marker" and let its owner be "John"
# this process of creating an object from its class is known as instantiation

A.display_information()
# display this marker's information

# And now that we actually have a pen class, remember that we can make AS MANY pens as we want!
B = Pen("blue", 0.1, "ball", "John")
C = Pen("black", 0.2, "fountain", "Robin")
D = Pen("red", 0.1, "gel", "Joe")
E = Pen("green", 0.1, "gel", "Robert")

# since a method works on a particular instance of a class, it must be called by using the dot operator, on that specific object.
B.display_information()
C.display_information()
D.display_information()
E.display_information()
```

## 3. Classes, conventionally

All programmers mutually agree to follow some rules, called conventions that are not necessary, but nice to follow while writing classes and make your code more readable to a usual programmer:

```py
class Pen:

    # typically, the object is called "self" in the functions that work with it
    # it is also common to give the same names to the function parameters as the properties of the object itself
    def __init__(self, colour, size, kind, owner):
        self.colour = colour
        self.size = size
        self.kind = kind
        self.owner = owner

    def display_information(self):
        print("Colour :", self.colour)
        print("Size   :", self.size)
        print("Kind   :", self.kind)
        print("Owner  :", self.owner)
        print()
```

=== "Practise" 

    Write a class that describes a bicycle object

    Which properties should a bicycle object have?

    1. Colour (red, blue, white, etc)
    2. Material (steel, aluminum, plastic, wood, etc)
    3. Size (small, medium, large)
    4. Height of the seat (in m)
    5. Gear ratio (1, 2.5, 4, etc)
    6. Diameter of the wheels (in cm)
    7. Does it have a basket
    8. Does it have a Bell

    What functions should a bicycle have?

    1. Change gear ratio
    2. Adjust seat height

=== "Answer"

    Write a class that describes a bicycle object

    Which properties should a bicycle object have?

    1. Colour (red, blue, white, etc)
    2. Material (steel, aluminum, plastic, wood, etc)
    3. Size (small, medium, large)
    4. Height of the seat (in m)
    5. Gear ratio (1, 2.5, 4, etc)
    6. Diameter of the wheels (in cm)
    7. Does it have a basket
    8. Does it have a Bell

    What functions should a bicycle have?

    1. Change gear ratio
    2. Adjust seat height
    
    ```py
    class Bicycle:
        def __init__(
            self,
            colour,
            mat,
            size,
            height,
            gear_ratio,
            diameter,
            has_basket,
            has_bell
        ):
            self.colour = colour
            self.mat = mat
            self.size = size
            self.height = height
            self.gear_ratio = gear_ratio
            self.diameter = diameter
            self.has_basket = has_basket
            self.has_bell = has_bell
        
        def change_gear(self, new_ratio):
            self.gear_ratio = new_ratio
        
        def change_height(self, new_height):
            self.height = new_ratio
    ```


## 4. What makes classes so good?

1. Reusability: The same class can be used to make as many objects as you want
2. Modularity: The code becomes incredibly modular, and it is easy for a programmer to debug the code in case there are any bugs
3. Clarity of code: Due to the code being modular, it is easier for others to read and understand the code
4. Better organisation: The data can be clearly and neatly organised for more complex objects
5. Data Abstraction: This is the process of hiding the implementation details from the user, allowing them to focus on the functionality instead.

    Example: you don't need to know a smartphone works internally to be able to use it. The details about its circuits, its workings are hidden from you, the user! Instead, the smartphone provides you with functions (call, message, surf the internet) only.

    Example in python:
    The functions like `math.sin()` and `math.cos()` can be used to find out the sine or cosine of an angle, but they do not tell you how the calcualtion is actually done. Those implementation details are hidden from you, the user and you only need to focus on the functionality!

## 5. An object can also have other objects as its properties

```py
class Pen:
    def __init__(self, colour, size, kind, owner):
        self.colour = colour
        self.size = size
        self.kind = kind
        self.owner = owner
    def display_information(self):
        print("Colour :", self.colour)
        print("Size   :", self.size)
        print("Kind   :", self.kind)
        print("Owner  :", self.owner)
        print()
class Pencil:
    def __init__(self, colour, shade, owner):
        self.colour = colour
        self.shade = shade
        self.owner = owner
    def display_information(self):
        print("Colour :", self.colour)
        print("Shade  :", self.shade)
        print("Owner  :", self.owner)
        print()

class Stationary:
    def __init__(self, pen, pencil):
        self.pen = pen
        self.pencil = pencil
    def display_information(self):
        print("The Pen: ")
        self.pen.display_information()
        print("The Pencil: ")
        self.pencil.display_information()

A = Stationary(
    Pen("blue", 0.1, "ball", "John"),
    Pencil("black", "HB", "John")
)
A.display_information()
```