![](https://github.com/davidrol6/2020-2021-PNE/raw/master/s7-Practice-1/Cover/Cover.png)

# Session 7: Practice 1

* **Time**: 2h
* **Date**: Wednesday, Mar-03rd-2020
* **Goals**:
  * Creating our first Class Module for working with DNA sequences

## Contents

* [Introduction](#introduction)  
* [Finish your previous practices](#finish-your-previous-practices) 
* [Exercises](#exercises)  
  * [Exercise 1: Creating the Seq1 module](#exercise-1-creating-the-seq1-module)  
  * [Exercise 2: Null sequences](#exercise-2-null-sequences)
  * [Exercise 3: Null, valid and invalid sequences](#exercise-3-null-valid-and-invalid-sequences)  
  * [Exercise 4: Len() method](#exercise-4-len-method)
  * [Exercise 5: count_base() method](#exercise-5-count_base-method)
  * [Exercise 6: count() method](#exercise-6-count-method)
  * [Exercise 7: reverse() method](#exercise-7-reverse-method) 
  * [Exercise 8: complement()](#exercise-8-complement-method) 
  * [Exercise 9: read_fasta method()](#exercise-9-read_fasta-method)
  * [Exercise 10: Processing the genes](#exercise-10-processing-the-genes)  
* [End of the session](#end-of-the-session)
* [Author](#author)
* [Credits](#credits)
* [License](#license) 

## Introduction

The goal of this practice is to developt the **Seq Class** for working with **DNA sequences**. This library will be in a module called **Seq1** (The python file should be called Seq1.py). It is quite similar to **Seq0**, developed in the previous practice, but using an **Object Oriented approach**. We will also include several improvements

These are all the normal **methods** that should be implemented in the **Seq Class**

|  Method  | Parameters  | Return value | Description |
|-----------------|-------------|--------------|--------------|
| **len**  | None | integer | Calculate the total number of bases in the sequence |
| **count_base**(base) |  base: character | Integer | Calculate the number of the given base in the Sequence |
| **count**   | None | A dicctionary | Calculate the number of all the bases in the sequence. A dicctionary with the results is returned. The keys are the bases and the values their number |
| **reverse** | None | String | Return the reverse sequence  |
| **complement** | None | String | Return the complement sequence |
| **read_fasta**(filename) | filename: string |  String | Open a DNA file in FASTA format and stored it inside the object |

In addition, the **Class Seq** will have the **special method**s that we already know: **\_\_init\_\_()** for initializing the object and **\_\_str\_\_()** for printing the object as a sequence

##  Finish your previous practices

**Before** starting Practice 1, spend time **finishing** the **previous practices**. This practice is based on this previous work

## Exercises

We will develop the **Seq class** **incrementally**, starting from your work on the Session 6

### Exercise 1: Creating the Seq1 module

Create a new python file, called **Seq1.py** in the **P1 folder**. This file is our **module**, that we will import from our exercises. Remember that for doing so, you have first to **mark** the P1 folder as **Sources Root**

Copy the **Seq Class** that you have already developed in the exercises of **Session 6** in the **Seq1.py** file

* **Filename:** P1/Seq1.py
* **Description**: This file where the Seq Class for working with DNA sequences is stored. It is our Seq1 module

The goal of this first exercise is making sure that you can access to the Seq class from **external files**
 
* **Filename:** P1/Ex1.py
* **Description**: Write a python program that creates an object with the sequence "ACTGA" and prints its length and the sequence itself. The output should be like this:

```
-----| Exercise 1 |------
New sequence created!
Sequence 1: (Length: 5) ACTGA

Process finished with exit code 0
```
* **Considerations**: 
The first thing you have to do is to **import** the **Seq Class** from the **Seq1 module**

```python3
from Seq1 import Seq
```

### Exercise 2: Null sequences

We will manage **three types** of sequences: **Valid**, **Invalid** and **Null**:
* **Null**: Empty sequence "".It has no bases
* **Valid**: A sequence compose of the union of only the four valid bases: 'A', 'T', 'C', 'G'. Example: "ATTACG"
* **Invalid**: A sequence that has one or more characters that are not valid bases. Example: "ATTXXG"
 
In this exercise we will implement the **Null sequences**

The **null sequences** are created by calling the **Seq() class** with **no** arguments:

```python3
# -- Creating a Null sequence
s = Seq()
# -- Creating a valid sequence
s = Seq("TATAC")
```
The difference between the creation of the previous two object is that the first one has no arguments when calling Seq, and the second one has one. This means that the **argument** passed to the **\_\_init()\_\_** method  is **optional**

For creating Null sequences the definition of the **\_\_init()\_\_** method should be like this:

```python3
def __init__(self, strbases="NULL"):
```

It is used in python for creating **optional arguments**. If no argument is given, python automatically will create one with the default value to "NULL". This is the value we will use to identify the **null sequences**

When a Null sequence is created, the **\_\_init()\_\_** method will print the message: "NULL Seq Created"

* **Filename:** P1/Ex2.py
* **Description**: Write a python program that creates first a null sequence and then a valid sequence. It should prints the objects. The output of the program should be:

```
-----| Practice 1, Exercise 2 |------
NULL Seq created
New sequence created!
Sequence 1: NULL
Sequence 2: ACTGA
```
* **Considerations**: The first  you should do in the **\_\_init()\_\_** method is checking if it is a null sequence. If so, print the message on the console,  assign the value to the **self.strbases** attribute and return. If it is not null, continue with the other checks 

### Exercise 3: Null, valid and invalid sequences

In this exercise we will make sure that our Seq class works ok with the **three types** of sequences. We will create this **three sequences**:

```python3
# -- Create a Null sequence
s1 = Seq()

# -- Create a valid sequence
s2 = Seq("ACTGA")

# -- Create an invalid sequence
s3 = Seq("Invalid sequence")
```

* **Filename:** P1/E3.py
* **Description**: Write a python program that creates three sequences: null, valid and invalid. Then it prints the objects in the console. This is what we should see on the **console:**

```
-----| Practice 1, Exercise 3 |------
NULL Seq created
New sequence created!
INVALID Seq!
Sequence 1: NULL
Sequence 2: ACTGA
Sequence 3: ERROR
```

### Exercise 4: len() method

The **len()** method should works with the **three types** of sequences. In case the sequence is **Null** or **invalid**, the length should be always **0**. Implement this behaviour in the Seq Class

* **Filename**: P0/Ex4.py
* **Desription**: Write a python program that creates three sequences: null, valid and invalid. Then it prints their lengths and sequences on the console. This is what we should see on the **console:**
```
-----| Practice 1, Exercise 4 |------
NULL Seq created
New sequence created!
INVALID Seq!
Sequence 1: (Length: 0) NULL
Sequence 2: (Length: 5) ACTGA
Sequence 3: (Length: 0) ERROR

Process finished with exit code 0
```

### Exercise 5: count_base() method

Implement the **count_base(base)** method. If the sequence is Null or invalid, the return value should be 0

* **Filename**: P0/Ex5.py
* **Desription**: Write a python program that creates three sequences: null, valid and invalid. Then it prints their lengths, sequences and the number of bases on the console. This is what we should see on the **console:**

```
-----| Practice 1, Exercise 5 |------
NULL Seq created
New sequence created!
INVALID Seq!
Sequence 0: (Length: 0) NULL
  A: 0,   C: 0,   T: 0,   G: 0, 
Sequence 1: (Length: 5) ACTGA
  A: 2,   C: 1,   T: 1,   G: 1, 
Sequence 2: (Length: 0) ERROR
  A: 0,   C: 0,   T: 0,   G: 0, 

Process finished with exit code 0
```

### Exercise 6: count() method

Implement the **count()** method. If the sequence is Null or invalid, the returned dictionary should have all its values to 0

* **Filename**: P0/Ex6.py
* **Desription**: Write a python program that creates three sequences: null, valid and invalid. Then it prints their lengths, sequences and dictionary returned by the count() method. This is what we should see on the **console:**

```
-----| Practice 1, Exercise 6 |------
NULL Seq created
New sequence created!
INVALID Seq!
Sequence 0: (Length: 0) NULL
  Bases: {'A': 0, 'T': 0, 'C': 0, 'G': 0}
Sequence 1: (Length: 5) ACTGA
  Bases: {'A': 2, 'T': 1, 'C': 1, 'G': 1}
Sequence 2: (Length: 0) ERROR
  Bases: {'A': 0, 'T': 0, 'C': 0, 'G': 0}

Process finished with exit code 0
```

### Exercise 7: reverse() method

Implement the **reverse()** method. If the sequence is Null or invalid, it should return the string "NULL" or "ERROR" respectively (and not its reverse!)

* **Filename**: P0/Ex7.py
* **Desription**: Write a python program that creates three sequences: null, valid and invalid. Then it prints their lengths, sequences, the dictionary with the bases and the reverse sequence. This is what we should see on the **console:**

```
-----| Practice 1, Exercise 7 |------
NULL Seq created
New sequence created!
INVALID Seq!
Sequence 0: (Length: 0) NULL
  Bases: {'A': 0, 'T': 0, 'C': 0, 'G': 0}
  Rev:   NULL
Sequence 1: (Length: 5) ACTGA
  Bases: {'A': 2, 'T': 1, 'C': 1, 'G': 1}
  Rev:   AGTCA
Sequence 2: (Length: 0) ERROR
  Bases: {'A': 0, 'T': 0, 'C': 0, 'G': 0}
  Rev:   ERROR
```

### Exercise 8: complement() method

Implement the **complement()** method. If the sequence is Null or invalid, it should return the string "NULL" or "ERROR" respectively (and not its complement!)

* **Filename**: P0/Ex8.py
* **Desription**: Write a python program that creates three sequences: null, valid and invalid. Then it prints their lengths, sequences, the dictionary with the bases, the reverse sequence and the complement. This is what we should see on the **console:**

```
-----| Practice 1, Exercise 8 |------
NULL Seq created
New sequence created!
INVALID Seq!
Sequence 0: (Length: 0) NULL
  Bases: {'A': 0, 'T': 0, 'C': 0, 'G': 0}
  Rev:   NULL
  Comp:  NULL
Sequence 1: (Length: 5) ACTGA
  Bases: {'A': 2, 'T': 1, 'C': 1, 'G': 1}
  Rev:   AGTCA
  Comp:  TGACT
Sequence 2: (Length: 0) ERROR
  Bases: {'A': 0, 'T': 0, 'C': 0, 'G': 0}
  Rev:   ERROR
  Comp:  ERROR

Process finished with exit code 0
```

### Exercise 9: read_fasta() method

We have been creating sequences by passing a string with the bases to the object. We also want to create sequence from **files** in **fasta format**. That is the purpose of the read_fasta() method

For using the read_fasta() method we need first to create a **Null sequenc**e. And then we call the read_fasta() method

```python3
# -- Create a Null sequence
s = Seq()

# -- Initialize the null seq with the given file in fasta format
s.read_fasta(FILENAME)
```
After that, you can use the sequence s exactly in the same way than the other sequences initialized manually

* **Filename**: P0/Ex9.py
* **Desription**: Write a python program that reads a sequence from the U5.txt file. Then it should print its lengths, the sequence, the dictionary with the bases, the reverse sequence and the complement. This is what we should see on the **console:**

```
-----| Practice 1, Exercise 9 |------
NULL Seq created
Sequence : (Length: 1314) ATAGACCAAACATGAGAGGCTGTGAATGGTATAATCTTCGCCGT...(not shown)...
  Bases: {'A': 360, 'T': 491, 'C': 229, 'G': 234}
  Rev:   ATAATGACAAGTTTAAAATAATGCCAGACTCTATTACGATTACTACATTCAAGGTAAATAC...(not shown)...
  Comp:  TATCTGGTTTGTACTCTCCGACACTTACCATATTAGAAGCGGCAAGCTGTCCATTCCAATA...(not shown)...

Process finished with exit code 0
```
As the U5 is very long, only the first characters are shown in this figure (but the exercise will show all the bases)

### Exercise 10: processing the genes

Write a python program that automatically calculate the answer to this question:

* Which is the most frequent base in each gene?

This exercise is the same than the exercise 8 of practice 0, but we are using the **Seq Class** instead of the functions developed in the Seq0 module

* **Filename**: P0/Ex10.py
* **Output**: This is what should be seen on the console after the execution

```
-----| Practice 1, Exercise 10 |------
NULL Seq created
Gene U5: Most frequent Base: T
NULL Seq created
Gene ADA: Most frequent Base: G
NULL Seq created
Gene FRAT1: Most frequent Base: C
NULL Seq created
Gene FXN: Most frequent Base: T
NULL Seq created
Gene RNU6_269P: Most frequent Base: A

Process finished with exit code 0
```

## END of the session

The session is finished. Make sure, during this week, that everything in this list is checked!

* [ ] You have all the items of the session 6 checked!
* [ ] Your working repo contains the **P1 Folder** with the following files:
  * [ ] Ex1.py
  * [ ] Ex2.py
  * [ ] Ex3.py
  * [ ] Ex4.py
  * [ ] Ex5.py
  * [ ] Ex6.py
  * [ ] Ex7.py
  * [ ] Ex8.py
  * [ ] Ex9.py
  * [ ] Ex10.py
  * [ ] Seq0.py
* [ ] All the previous files have been pushed to your remote Github repo

# Credits
* [Juan González-Gómez](https://github.com/Obijuan) (Obijuan)
* [Alvaro del Castillo](https://github.com/acs). He designed and created the original content of this subject. Thanks a lot :-)

# License

![](https://github.com/Obijuan/digital-electronics-with-open-FPGAs-tutorial/raw/master/wiki/portada/attribution-share-alike-creative-commons-license.png)

# Links

* [Universidad Rey Juan Carlos de Madrid](https://www.urjc.es/)
* [Escuela Técnica Superior de Ingeniería de Telecomunicaciones (URJC)](https://www.urjc.es/universidad/facultades/escuela-tecnica-superior-de-ingenieria-de-las-telecomunicaciones/content/etsit-escuela-tecnica-superior-de-ingenieria-de-telecomunicacion)