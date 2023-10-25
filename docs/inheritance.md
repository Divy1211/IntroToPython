# Inheritance

## 1. What is inheritance, and why do we need it?

Lets say that there is a Person. Now each person has some defining properties, like their name, age, sex, height, weight. A person could be a student and in that case, they would have some additional defining properties, for example the school they attend, their id number, their year, their section and their seat number.

Now imagine that you are a programmer trying to describe a student using code... how could you go about writing code that expresses these properties discussed above? Keep in mind that a `class Person` with the properties name, age, sex, height and weight already exists.

You might think of a few different things that can be done here:

One option is to have a `person` object as a part of the `student` object, like so:

```py
class Person:
    def __init__(self, name, age, sex, height, weight):
        self.name = name
        self.age = age
        self.sex = sex
        self.height = height
        self.weight = weight

    def display_information(self):
        print("Name   : " + self.name)
        print("Age    : " + str(self.age))
        print("Sex    : " + self.sex)
        print("Height : " + str(self.height))
        print("Weight : " + str(self.weight))

class Student1:
    def __init__(self, person, school, id_no, seat_no, year, section):
        self.person = person
        self.school = school
        self.id_no = id_no
        self.seat_no = seat_no
        self.year = year
        self.section = section
    
    def display_information(self):
        self.person.display_information()
        print("School  : " + self.school)
        print("ID      : " + str(self.id_no))
        print("Seat    : " + str(self.seat_no))
        print("Year    : " + str(self.year))
        print("Section : " + self.section)
        print()
    
        
A = Student1(Person("John", 15, "male", 160, 60), "SUTD", 1024, 32, 2, "A")

print(A.person.name+"'s age: "+str(A.person.age))
A.display_information()
```

Another option might be to declare all of the properties of a `person` again along with the additional properties of a `student`
```py
# class Person here is unused, basically making the already existing class redundant
class Person:
    def __init__(self, name, age, sex, height, weight):
        self.name = name
        self.age = age
        self.sex = sex
        self.height = height
        self.weight = weight

    def display_information(self):
        print("Name   : " + self.name)
        print("Age    : " + str(self.age))
        print("Sex    : " + self.sex)
        print("Height : " + str(self.height))
        print("Weight : " + str(self.weight))

class Student2:
    def __init__(self, name, age, sex, height, weight, school, id_no, seat_no, year, section):
        self.name = name
        self.age = age
        self.sex = sex
        self.height = height
        self.weight = weight
        self.school = school
        self.id_no = id_no
        self.seat_no = seat_no
        self.year = year
        self.section = section

    def display_information(self):
        print("Name   : " + self.name)
        print("Age    : " + str(self.age))
        print("Sex    : " + self.sex)
        print("Height : " + str(self.height))
        print("Weight : " + str(self.weight))
        print("School  : " + self.school)
        print("ID      : " + str(self.id_no))
        print("Seat    : " + str(self.seat_no))
        print("Year    : " + str(self.year))
        print("Section : " + self.section)
        print()

# when there are a lot of function parameters, it is nice to specify which parameters correspond to what
# values for better readability and clarity and put them each on their own line
B = Student2(
    name = "Robert", 
    age = 14, 
    sex = "male", 
    height = 160, 
    weight = 65, 
    school = "SUTD", 
    id_no = 1025, 
    seat_no = 12, 
    year = 1, 
    section = "A",
)
print(B.name+"'s age: "+str(B.age))
B.display_information()
```
The first approach works, but the syntax looks a bit unintuitive, doesn't it?

This is because to create a student object, you have to first make a Person object and then provide that person object to the student constructor, like so `A = Student1(Person("John", 15, "male", 170, 70), "SUTD", 1024, 32, 2, "A")`

Also, to access a student's name and age, you have to do `A.person.name` and `A.person.age`... wouldn't `A.name` and `A.age` make more sense?

The 2nd approach fixes this issue but it is also a bit tedious because you have to manually declare all properties of a person inside the student constructor... What if there were not 5, but 100 different properties associated with a person? It would be too unfeasable to manually rewrite them.

This is where inheritance comes into the picture. Inheritance literally allows us to "inherit" the properties of one class (called the super or base class) into another class (called the sub or child class)

```py

# Super/Parent class
class Person:
    def __init__(self, name, age, sex, height, weight):
        self.name = name
        self.age = age
        self.sex = sex
        self.height = height
        self.weight = weight

    def display_information(self):
        print("Name   : " + self.name)
        print("Age    : " + str(self.age))
        print("Sex    : " + self.sex)
        print("Height : " + str(self.height))
        print("Weight : " + str(self.weight))

# Base/Sub class
class Student(Person):
    def __init__(self, name, age, sex, height, weight, school, id_no, seat_no, year, section):
        Person.__init__(self, name, age, sex, height, weight) # we can re-use functionality from the super class!
        self.school = school
        self.id_no = id_no
        self.seat_no = seat_no
        self.year = year
        self.section = section

    def display_information(self):
        Person.display_information(self) # we can re-use functionality from the super class!
        print("School  : " + self.school)
        print("ID      : " + str(self.id_no))
        print("Seat    : " + str(self.seat_no))
        print("Year    : " + str(self.year))
        print("Section : " + self.section)
    
# when there are a lot of function parameters, it is nice to specify which parameters correspond to what
# values for better readability and clarity and put them each on their own line
A = Student(
    name = "Robin", 
    age = 16, 
    sex = "male", 
    height = 180, 
    weight = 75, 
    school = "SUTD", 
    id_no = 1023, 
    seat_no = 3, 
    year = 3, 
    section = "A",
)
print(A.name+"'s age: "+str(A.age))
A.display_information()
```

!!! note "Best practice"
    The following usages of super class methods in the above example:
    ```py
    Person.__init__(self, name, age, sex, height, weight)

    Person.display_information(self)
    ```
    Are for educational purposes only, in real python programs, we should make use of the following syntax instead:

    ```py
    # notice that the self parameter has been omitted
    super().__init__(name, age, sex, height, weight)

    super().display_information()
    ```
    The reason for doing so is that `super()` in python does the work of figuring out which super class's function to call and if you end up changing the superclass, you don't have to change all your code everywhere (Also there can be multiple super classes, but that's a story for another day)

=== "Practise"
    Given a class computer, Write a subclass laptop and desktop with the given additional properties:

    A computer object has the following properties:

    1. CPU Type
    2. Storage Type
    3. Storage Quantity (in GB)
    4. RAM (in GB)
    5. GPU Type

    Write a class for laptop and desktop objects that have the above properties, and the additional properties listed below:

    Desktop:

    1. Monitor
    2. Monitor Resolution
    2. Keyboard
    3. Mouse

    Laptop:

    1. Monitor Resolution
    2. Is it a touchscreen?

    Also write a function that displays all this information

    ```py
    class Computer:
        def __init__(
            self,
            cpu: str,
            storage_type: str,
            storage: float,
            ram: float,
            gpu: str,
        ):

            # type hints can also be given to a class' data members
            self.cpu: str = cpu
            self.storage_type: str = storage_type
            self.storage: float = storage
            self.ram: float = ram
            self.gpu: str = gpu

        def display_information(self):
            print("The CPU type is     : "+self.cpu)
            print("The Storage type is : "+self.storage_type)
            print("The Stroage is      : "+str(self.storage))
            print("The RAM is          : "+str(self.ram))
            print("The GPU is          : "+self.gpu)
    ```

=== "Answer"
    Given a class computer, Write a subclass laptop and desktop with the given additional properties:

    A computer object has the following properties:

    1. CPU Type
    2. Storage Type
    3. Storage Quantity (in GB)
    4. RAM (in GB)
    5. GPU Type

    Write a class for laptop and desktop objects that have the above properties, and the additional properties listed below:

    Desktop:

    1. Monitor
    2. Monitor Resolution
    2. Keyboard
    3. Mouse

    Laptop:

    1. Monitor Resolution
    2. Is it a touchscreen?

    Also write a function that displays all this information

    ```py
    class Computer:
        def __init__(
            self,
            cpu: str,
            storage_type: str,
            storage: float,
            ram: float,
            gpu: str,
        ):

            # type hints can also be given to a class' data members
            self.cpu: str = cpu
            self.storage_type: str = storage_type
            self.storage: float = storage
            self.ram: float = ram
            self.gpu: str = gpu

        def display_information(self):
            print("The CPU type is     : "+self.cpu)
            print("The Storage type is : "+self.storage_type)
            print("The Stroage is      : "+str(self.storage))
            print("The RAM is          : "+str(self.ram))
            print("The GPU is          : "+self.gpu)
    ```

    Required Classes:

    ```py
    class Computer:
        def __init__(
            self,
            cpu: str,
            storage_type: str,
            storage: float,
            ram: float,
            gpu: str,
        ):

            # type hints can also be given to a class' data members
            self.cpu: str = cpu
            self.storage_type: str = storage_type
            self.storage: float = storage
            self.ram: float = ram
            self.gpu: str = gpu

        def display_information(self):
            print("The CPU type is     : "+self.cpu)
            print("The Storage type is : "+self.storage_type)
            print("The Stroage is      : "+str(self.storage))
            print("The RAM is          : "+str(self.ram))
            print("The GPU is          : "+self.gpu)

    class Laptop(Computer):
        def __init__(
            self,
            cpu: str,
            storage_type: str,
            storage: float,
            ram: float,
            gpu: str,
            resolution: str,
            is_touchscreen: bool,
        ):
            Computer.__init__(self, cpu, storage_type, storage, ram, gpu)
            self.resolution = resolution
            self.is_touchscreen = is_touchscreen

        def display_information(self):
            Computer.display_information(self)
            print("The resolution is   : "+self.resolution)
            print("Is it a touchscreen : "+str(self.is_touchscreen))

    class Desktop(Computer):
        def __init__(
            self,
            cpu: str,
            storage_type: str,
            storage: float,
            ram: float,
            gpu: str,
            monitor: str,
            resolution: str,
            keyboard: str,
            mouse: str,
        ):
            Computer.__init__(self, cpu, storage_type, storage, ram, gpu)
            self.monitor = monitor
            self.resolution = resolution
            self.keyboard = keyboard
            self.mouse = mouse

        def display_information(self):
            Computer.display_information(self)
            print("The monitor is      : "+self.monitor)
            print("The resolution is   : "+self.resolution)
            print("The keyboard is     : "+self.keyboard)
            print("The mouse is        : "+self.mouse)
    ```