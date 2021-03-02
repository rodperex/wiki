![](https://github.com/davidrol6/2020-2021-PNE/tree/master/s6-OOP/Cover/Cover.png)

# Session 6: Object Oriented Programming

* **Time**: 2h
* **Date**: Tuesday, March-2nd-2020
* **Goals**:
  * Understand how the Classes work
  * Create our first Class
  * Working with objects
  * Learn to install libraries

## Contents

* [Introduction](#introduction)  
* [Working with sequences and functions](#working-with-sequences-and-functions)
* [Modelling the sequences with object oriented programming](#modelling-the-sequences-with-object-oriented-programming)  
  * [Classes](#classes)  
  * [The \_\_Init\_\_ method](#the-__init__-method)  
  * [Adding data: Atribute strbases](#adding-data-attribute-strbases)  
  * [The \_\_str\_\_ method](#the-__str__-method)  
  * [Adding methods: len()](#adding-methods-len)  
  * [Inheritance](#inheritance)  
    * [Expanding the Gene class](#expanding-the-gene-class)  
    * [Overriding the Seq methods](#overriding-the-seq-methods)  
* [Installing libraries: Termcolor](#installing-libraries-termcolor)  
* [Exercises](#exercises)
  * [Exercise 1](#exercise-1)  
  * [Exercise 2](#exercise-2)
  * [Exercise 3](#exercise-3)  
  * [Exercise 4](#exercise-4)  
* [End of the session](#end-of-the-session)
* [Author](#author)
* [Credits](#credits)
* [License](#license) 

## Introduction

All the python programs that you have developed so far use the **classical paradigm** of the [procedural programming](https://en.wikipedia.org/wiki/Procedural_programming). The main idea is to use **functions** that can be called at any point during the program's execution

The problem you have to solve is divided into smaller parts, implemented  using **functions**, **data structures** and **variables** 

On the contrary, the [object oriented paradigm](https://en.wikipedia.org/wiki/Object-oriented_programming) tries to model the problems by means of defining **objects** that interact between them. Each object has **attributes** and **methods**. The main advantages are the **encapsulation** and the **reusability** of the code

## Working with sequences and functions

In the previous session we developed our own **library of functions** (Seq0) for working with sequences. As an example let's use that library for performing some **simple calculations** on the sequence "ATTCCCGGGG". Save this example in the folder **Session-06** and call it **test-01.py**

```python3
from Seq0 import *

seq1 = "ATTCCCGGGG"

print(f"Seq:    {seq1}")
print(f"  Rev : {seq_reverse(seq1)}")
print(f"  Comp: {seq_complement(seq1)}")
print(f"  Length: {seq_len(seq1)}")
print(f"    A: {seq_count_base(seq1, 'A')}")
print(f"    T: {seq_count_base(seq1, 'T')}")
print(f"    C: {seq_count_base(seq1, 'C')}")
print(f"    G: {seq_count_base(seq1, 'G')}")
``` 

This is what you get in the **console** when the program is **executed**:

```
Seq:    ATTCCCGGGG
  Rev : GGGGCCCTTA
  Comp: TAAGGGCCCC
  Length: 10
    A: 1
    T: 2
    C: 3
    G: 4
```

This **paradigm** is based on defining the data (variables) on one hand, and creating s**eparated functions** for working with that data. When calling the function you should pass the **data as parameters**. The data and function are **separated things** 

Imagine that now we define a new sequence, but we make a mistake:

```python3
from Seq0 import *

# -- This sequence is invalid, as it as characteres
# -- different than the 4 bases: A,T, C,G
seq1 = "ATTXMMNXCCCGGGG"

print(f"Seq:    {seq1}")
print(f"  Length: {seq_len(seq1)}")
print(f"    A: {seq_count_base(seq1, 'A')}")
print(f"    T: {seq_count_base(seq1, 'T')}")
print(f"    C: {seq_count_base(seq1, 'C')}")
print(f"    G: {seq_count_base(seq1, 'G')}")

# -- But this program works normally. No error es detected

```

* How could you solve that problem? How could you guarantee that the sequence introduced is valid?

One solution is adding a **new function** for checking that a given sequence is ok. Something like this:


```python3
...
seq1 = ATTXMMNXCCCGGGG"

# -- Check that the sequence is valid
seq_check(seq1)
...
```

It is ok, but what happens if there are programmers that do not call this function for checking? It is **NOT possible** for you to **assure** that it is going to work in all the cases. It depends on the people using it. Some may call the seq_check() function, but other do not.

Is it possible to have a **better model** for organizing the data and the functions?

## Modelling the sequences with object oriented programming

Yes! There are better models. One is the **Object Oriented Programming**

In this model, the **data** and the **functions** are grouped together into what is called and **object**. They are no longer separated. You work with **objects.** Every object has a **well defined actions** that you can **perform** on then. These actions are called **methods**

In order to learn about this new paradigm, let's model the DNA sequences with it

We will think about the **sequences** as **objects**. This objects can have some **properties**, like their name, the chromosome to which they belog or any other information. We also refer to this properties as the object **attributes**

These object also have some **methods**: different actions that can be performed on them, such as calculating their length, the number of a certain bases, their complement, and so on

We will learn this model by defining **sequence objects** from **scratch**

### Classes

A [class](https://en.wikipedia.org/wiki/Class_(computer_programming)) is the **template** we use for **creating objects**. Inside the class we define all the **methods** of the objects of that class, and we program their **behaviour**. Let's create a minimum class for working with sequences. We start by defining an **empty class**:

```python
class Seq:
    """A class for representing sequences"""
    pass
```

When the class is defined, we can **create objects** of this class as shown here:

```python
# Main program
# Create an object of the class Seq
s1 = Seq()

# Create another object of the Class Seq
s2 = Seq()
```

Let's place a **breakpoint** in the line 7

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s6-OOP/oop-01.png) 

Press the **step over** option twice. On the variable panel we will see the **two new objects** created: **s1** and **s2**. Notice that they are of **type Seq**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s6-OOP/oop-02.png)

Contrats! You have created your first two **empty objects**!

### The \_\_init\_\_ method

The **methods** are the **actions** that the objects can perform. The first method we are implementing is the **initialization method**. It is a **special method** that is called every time a new object is created. All the methods have the **special parameter self** as the first parameter

```python
class Seq:
    """A class for representing sequences"""
    def __init__(self):
        print("New sequence created!")


# Main program
# Create an object of the class Seq
s1 = Seq()
s2 = Seq()
print("Testing...")
```

Run the program. When the s1 object is created, the string "New sequence created!" is printed. The same happens when the s2 object is also created. The **output** of the program is:

```
New sequence created!
New sequence created!
Testing....
```

* Execute it **step by step**, using the **step over** command

* Execute it **step by step** using the **step into** command every time. Check that the debugger **enters** into the **Class** and execute the** \_\_init\_\_** method

### Adding data: attribute strbases

For representing a **sequence** we will use a **string** that is store in every object. We will call this string as **strbases**. The data stored in the objects is referred as **attributes**

We modify the \_\_init\_\_ method to include a new parameter: the string for creating the object. That parameter will be stored in the object attribute: **self.strbases**

```python
class Seq:
    """A class for representing sequences"""
    def __init__(self, strbases):

        # Initialize the sequence with the value 
        # passed as argument when creating the object
        self.strbases = strbases
        print("New sequence created!")


# Main program
# Create objects of the class Seq
s1 = Seq("AGTACACTGGT")
s2 = Seq("CGTAAC")
```
If you **execute** it, you will see the **same output** than before. But now something has happened. The two objects created have their own **sequence string** stored in the **strbases** attribute. Let's debug it to see it

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s6-OOP/oop-03.png)

Each object has **its own sequence**! If you **debug** it using the **step into** option, you will see that the sequence is stored in the object when the **self.strbases = strbases** line is executed

### The \_\_str\_\_ method

There is another special method, called **\_\_str\_\_** that is invoked whenever the object is **printed**. Printing our objects means that we want to see the **sequence** on the **console**

```python3
class Seq:
    """A class for representing sequences"""

    def __init__(self, strbases):

        # Initialize the sequence with the value
        # passed as argument when creating the object
        self.strbases = strbases

        print("New sequence created!")

    def __str__(self):
        """Method called when the object is being printed"""

        # -- We just return the string with the sequence
        return self.strbases


# --- Main program
s1 = Seq("AGTACACTGGT")
s2 = Seq("CGTAAC")

# -- Printing the objects
print(f"Sequence 1: {s1}")
print(f"Sequence 2: {s2}")
print("Testing....")
```
After **running** it, we will see the following **messages** on the **console**:

```
New sequence created!
New sequence created!
Sequence 1: AGTACACTGGT
Sequence 2: CGTAAC
Testing....
```

In **debug mode**, if the **step into** option is pressed when the next instruction to be executed is the first print, you will see how the execution pointer moved into the **\_\_str\_\_ method**

###  Adding methods: len()

Let's add a new method: **len()** for calculating the **length of the sequence**. As it is a method, the first parameter must be **self**. For calculating the length, we will use the **len()** function (because in this example the type we are using for storing the bases is a string)

```python3
class Seq:
    """A class for representing sequences"""

    def __init__(self, strbases):

        # Initialize the sequence with the value
        # passed as argument when creating the object
        self.strbases = strbases

        print("New sequence created!")

    def __str__(self):
        """Method called when the object is being printed"""

        # -- We just return the string with the sequence
        return self.strbases

    def len(self):
        """Calculate the length of the sequence"""
        return len(self.strbases)


# --- Main program
s1 = Seq("AGTACACTGGT")
s2 = Seq("CGTAAC")

# -- Printing the objects
print(f"Sequence 1: {s1}")
print(f"  Length: {s1.len()}")
print(f"Sequence 2: {s2}")
print(f"  Length: {s2.len()}")
```

Once the objects have been created, their lengths can be calculated just by calling the **len() method**. For doing so, we have to write a **point** and the the **name** of the method:  **s1.len()**. The meaning of this is: "Execute the action for calculating the length on the s1 object"

**Run** the program. This is what you should see on the **console**:

```
New sequence created!
New sequence created!
Sequence 1: AGTACACTGGT
  Length: 11
Sequence 2: CGTAAC
  Length: 6
```

### Inheritance

New classes can be **derived** from others, reusing their methods and adding new ones. This is called **inheritance**. Just to present the concepts, Let's create the **Gene class** derived from the Sequence. It will not add anything

```python3
class Gene(Seq):
    """This class is derived from the Seq Class
       All the objects of class Gene will inherite
       the methods from the Seq class
    """
    pass
```

Now we can create objects from the **Gene class**. This objects will have the same methods than the **Seq objects**. We say that these methods have been inherited from the Seq class

```python3
# --- Main program
s1 = Seq("AGTACACTGGT")
g = Gene("CGTAAC")

# -- Printing the objects
print(f"Sequence 1: {s1}")
print(f"  Length: {s1.len()}")
print(f"Gene: {g}")
print(f"  Length: {g.len()}")
```

If we **run** the program this is what is shown in the **console**:

```
New sequence created!
New sequence created!
Sequence 1: AGTACACTGGT
  Length: 11
Gene: CGTAAC
  Length: 6
```

#### Expanding the Gene Class

The **Gene** is a kind of **specialized sequence**. Not all the sequences are Genes, but all the genes are sequences. We can **expand** the **Gene class** by adding more information that is not present in the general sequences. For example the **name**: usually the genes have a special name

Let's create a new \_\_init\_\_ file method that includes a new optional parameter: the name of the Gene

```python3
class Gene(Seq):
    """This class is derived from the Seq Class
       All the objects of class Gene will inheritate
       the methods from the Seq class
    """
    def __init__(self, strbases, name=""):

        # -- Call first the Seq initilizer and then the
        # -- Gene init method
        super().__init__(strbases)
        self.name = name
        print("New gene created")
```

As the Gene is also a Seq, for creating a Gene first we should call the **init** function from the **Seq class**. We do it by calling the **super().__init__(strbases)** method. And then we add the properties of the Gene. In this case its name

When creating the Gene in the main program, we specify its **name** as a parameter, for example FRAT1:

```python3
# --- Main program
s1 = Seq("AGTACACTGGT")
g = Gene("CGTAAC", "FRAT1")

# -- Printing the objects
print(f"Sequence 1: {s1}")
print(f"Gene: {g}")
```

When the program is **executed**, we can see this on the **Console**:

```
New sequence created!
New sequence created!
New gene created
Sequence 1: AGTACACTGGT
Gene: CGTAAC
```

Notice how the **init function** from the **Seq** has been **called twice**. The init function from the Gene only **once**

#### Overriding the Seq methods

In the new **Gene class**, we can create **new methods**, or we can **re-implement** method that were already implemeted in the Seq class. This operation of re-implementation is called overriding. For example, let's change the \_\_str\_\_ method for **printing** the **Gene name** along with the sequence

```python3
class Gene(Seq):
    """This class is derived from the Seq Class
       All the objects of class Gene will inheritate
       the methods from the Seq class
    """
    def __init__(self, strbases, name=""):

        # -- Call first the Seq initilizer and then the
        # -- Gene init method
        super().__init__(strbases)
        self.name = name
        print("New gene created")

    def __str__(self):
        """Print the Gene name along with the sequence"""
        return self.name + "-" + self.strbases
```

The **main program** remains the same:

```python3
# --- Main program
s1 = Seq("AGTACACTGGT")
g = Gene("CGTAAC", "FRAT1")

# -- Printing the objects
print(f"Sequence 1: {s1}")
print(f"Gene: {g}")
```

This is the result of the **execution**. We can see how the Gene object is printed diferently:

```
New sequence created!
New sequence created!
New gene created
Sequence 1: AGTACACTGGT
Gene: FRAT1-CGTAAC
```
If you have a look to the right side of the \_\_str\_\_ method in the **Gene Class**, you will notice a new icon: a **circle with an arrow** pointing upwards. This means that this methods is **overriding** another implemented in the super class (Seq)

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s6-OOP/oop-04.png)

On the other hand, if you have a look at the \_\_str\_\_ method in the **Seq Class**, you will see the previous icon and a **new one** with another circle and **arrow pointing downwards**  

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s6-OOP/oop-05.png)

This means that there is a **sub-clas**s that is overriding this methods, as we already know. And that the Seq \_\_str\_\_ method is also overriding another one from its **super class** 


## Installing libraries: termcolor

There are many **python libraries** available for you to use. You only have to **install** them. As an example of how to do it, let's install the [termcolor](https://pypi.org/project/termcolor/) library. It will allow us to **print messages in color** on the **console** 

Create a **new python file** in the **Session-06** folder and call it **test-color-py**. Write this code:

```python
import termcolor

termcolor.cprint("Hey! this is printed in green!", 'green')
```

 You will see that the word **termcolor** is underlined in **red**. This is because Pycharm does not know anything about the termcolor module. 

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s6-OOP/libraries-02.png)

Place the **mouse pointer** on termcolor and a **new window** will pop up:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s6-OOP/libraries-01.png)

Click on the **install package termcolor** option. The package start the installation. After some seconds it is ready and the termcolor is no longer in red

Now **run** the program. You will see a green message on the console

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s6-OOP/libraries-03.png)

You now have the power of printing in colors in the console. Use it wisely...

## Exercises

Let's practice with the objects!. Create the **Session-06 folder** if you already has not done it yet. Store there all the files create during this session (exercises and sequences)

**NOTE**: Theses exercises are independent one to each other. They do NOT import components from other modules. For modifying the Seq Class just copy & paste the older version into the new file

### Exercise 1

The current **Seq class** created as a example in this session does not check if the given string of bases is **valid*. Therefore, if we execute the following code in the the main program:

```python3
s1 = Seq("ACCTGC")
s2 = Seq("Hello? Am I a valid sequence?")
print(f"Sequence 1: {s1}")
print(f"Sequence 2: {s2}")
```

We see in the console that the two object have been created normally:

```
New sequence created!
New sequence created!
```

The goal of this exercise is to detect the **incorrect sequences**

* **Filename**: Session-06/Ex1.py
* **Description**: Modify the \_\_ini\_\_ methond of the Seq class so that it detects that the given string only have these four valid bases: 'A', 'C', 'G' and 'T'. If a different character is found, the sequence should be initilalized with the **"ERROR" string**, and the message **"INCORRECT Sequence detected"** printed on the console

When the previous **main program** is executed, this is what should be printed on the console:

```
New sequence created!
ERROR!!
Sequence 1: ACCTGC
Sequence 2: ERROR

Process finished with exit code 0
```

### Exercise 2

We can create **lists of sequences** very easily. For example, in this list there are three sequences:

```
seq_list = [Seq("ACT"), Seq("GATA"), Seq("CAGATA")]
```

We need to develop the function **print_seqs(seq_list)** that receives a **list of sequence**s and prints their **number** in the list, their **length** and the **sequence** itself. For ejemple, if we call the function with the previous list, the output in the console should be:

```
Sequence 0: (Length: 3) ACT
Sequence 1: (Length: 4) GATA
Sequence 2: (Length: 6) CAGATA
```

* **Filename**: Session-06/Ex2.py
* **Description**: Implement the print_seqs() function

### Exercise 3

We need to develop some **functions** for creating different sequences for **testing** the Seq objects. The function **generate_seqs(pattern, number)** has two parameters. It will create a **list** with the given *number* of sequences. All the sequences are created from the given **pattern**. This pattern is a string of one or more bases. The first sequence of the list will have only the pattern. In the second, the pattern is repeated twice. In the third, the patter is repeated three times, and so on

Therefore, if we call the function generate_seqs() with the parameters ("A", 3), a list of 3 sequences is returned. The bases in every sequence will be: "A", "AA" and "AAA"

* **Filename**: Session-06/Ex3.py
* **Description**: Implement the generate_seqs() function. Test the function with this main program:

```python3
seq_list1 = generate_seqs("A", 3)
seq_list2 = generate_seqs("AC", 5)

print("List 1:")
print_seqs(seq_list1)

print()
print("List 2:")
print_seqs(seq_list2)
```

When **executed**, the output in the console should be like this:

```
New sequence created!
New sequence created!
New sequence created!
New sequence created!
New sequence created!
New sequence created!
New sequence created!
New sequence created!
List 1:
Sequence 0: (Length: 1) A
Sequence 1: (Length: 2) AA
Sequence 2: (Length: 3) AAA

List 2:
Sequence 0: (Length: 2) AC
Sequence 1: (Length: 4) ACAC
Sequence 2: (Length: 6) ACACAC
Sequence 3: (Length: 8) ACACACAC
Sequence 4: (Length: 10) ACACACACAC
```

### Exercise 4

Let's play with the **termcolor** module. Modify the previous exercise for printing both lists in different color: print list 1 in **blue**, and list 2 in **green**

You should modify the **print_seqs()** function for including an additional parameter: the color

* **Filename**: Session-06/Ex4.py
* **Description**: The same output than Ex3.py, but in colors. This is how it should looks like:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s6-OOP/ex4-01.png)


## END of the session

The session is finished. Make sure, during this week, that everything in this list is checked!

* [ ] You have all the items of the session 5 checked!
* [ ] Your working repo contains the **Session-06 Folder** with the following files:
  * [ ] test-01.py
  * [ ] seq-01.py
  * [ ] test-color.py
  * [ ] Ex1.py
  * [ ] Ex2.py
  * [ ] Ex3.py
  * [ ] Ex4.py
* [ ] All the previous files have been pushed to your remote Github repo


# Author

* [Juan González-Gómez](https://github.com/Obijuan) (Obijuan)

![](https://github.com/Obijuan/digital-electronics-with-open-FPGAs-tutorial/raw/master/wiki/portada/logos-urjc-gsyc-peloto-jderobot.png)

# Credits

* [Alvaro del Castillo](https://github.com/acs). He designed and created the original content of this subject. Thanks a lot :-)

# License

![](https://github.com/Obijuan/digital-electronics-with-open-FPGAs-tutorial/raw/master/wiki/portada/attribution-share-alike-creative-commons-license.png)

# Links

* [Universidad Rey Juan Carlos de Madrid](https://www.urjc.es/)
* [Escuela Técnica Superior de Ingeniería de Telecomunicaciones (URJC)](https://www.urjc.es/universidad/facultades/escuela-tecnica-superior-de-ingenieria-de-las-telecomunicaciones/content/etsit-escuela-tecnica-superior-de-ingenieria-de-telecomunicacion)