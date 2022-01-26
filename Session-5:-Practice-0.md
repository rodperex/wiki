![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s5-Practice-0/Cover/Cover.png)

# Session 5: Practice 0

* **Time**: 2h
* **Date**: Wednesday, Feb-12th-2020
* **Goals**:
  * Creating our first python Module for working with real DNA sequences
  * Learn how to import our own modules in our programs
  * Learn how to write program divided in two or more files
  * Install the tools on our own laptop for working at home

## Contents

* [Introduction](#introduction)   
* [Working in separate files](#working-in-separate-files-import)  
* [Installing the tools on your Laptop](#installing-the-tools-on-your-laptop)  
  * [Installing python](#installing-python)
  * [Installing Git](#installing-git)
  * [Installing Pycharm Community Edition](#installing-pycharm-community-edition)
  * [Testing your tools](#testing-your-tools)  
* [Exercises](#exercises)
  * [Exercise 1: seq_ping()](#exercise-1-seq_ping)
  * [Exercise 2: seq_read_fasta()](#exercise-2-seq_read_fasta)
  * [Exercise 3: seq_len()](#exercise-3-seq_len)
  * [Exercise 4: seq_count_base()](#exercise-4-seq_count_base)
  * [Exercise 5: seq_count()](#exercise-5-seq_count)
  * [Exercise 6: seq_reverse()](#exercise-6-seq_reverse)  
  * [Exercise 7: seq_complement()](#exercise-7-seq_complement)  
  * [Exercise 8: Processing the genes](#exercise-8-processing-the-genes)  
* [End of the session](#end-of-the-session)
* [Author](#author)
* [Credits](#credits)
* [License](#license) 

## Introduction

The goal of this practice is to create a **library of functions** for working with **DNA sequences**. We will call this initial library as **Seq0**

These are all the functions that should be **implemented**. They all will be stored in the file **Seq0.py**

|  Function name  | Parameters  | Return value | Description |
|-----------------|-------------|--------------|--------------|
| **seq_ping()**     |   none      | none         | Test function. It just prints the "OK" message on the console  |
|  **seq_read_fasta**(filename) | filename: string |  String | Open a DNA file in FASTA format and return the sequence as a string (It should only contains the characters 'A', 'T', 'G' or 'C |
| **seq_len**(seq) | seq: String | integer | Calculate the total number of bases in the sequence |
| **seq_count_base**(seq, base) |  seq:String; base: character | Integer | Calculate the number of the given base in the Sequence |
| **seq_count**(seq) | seq: String | A dicctionary | Calculate the number of all the bases in the sequence. A dicctionary with the results is returned. The keys are the bases and the values their number |
| **seq_reverse**(seq) | seq: String | String | Return the reverse sequence  |
| **seq_complement**(seq) | seq: String | String | Return the complement sequence |

## Working in separate files: import

All the programs we have created so far have been located in their own **python files**: one file per program. In that file we placed both the main code and the functions

When working in more **complex projects**, the python code is divided in **small pieces of code** and placed in **different files**. In this practice we will place all the functions for working with DNA sequences into the **Seq0.py** file, and we will create additional files for the application programs that will use that library

For **accessing to the functions** defined in the **Seq0 module**, you should **write this line** in the beginning of your programs:

```python3
from Seq0 import *
```
In addition, as the **Seq0 module** will be located in the **P0 Folder**, you have to tell it to Pycharm by **right clicking** on the P0 folder and selecting the **Mark directory as/Sources Root** 

* Make sure you have the **P0 folder**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s5-Practice-0/import-01.png)

* Right click on it and select **Mark directory as/Sources Root**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s5-Practice-0/import-02.png)

* Notice how the **P0 folder** now have a **different color**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s5-Practice-0/import-03.png)

## Installing the tools on your laptop

From **practice 0**, you can use **your own laptop** for working if you want. What is important is that you **push** all your code into your **remote repository** at **Github**. Remember: the more commits, the better

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s5-Practice-0/install-01.jpg)

**Some exercises** will be **mandatory** to test them **in the lab**, because we will communicate with some computers in the **lab network**. But many others, including the **final project**, could be done in your **own laptop**

All the tools we are using are **Open Source** and **Multiplatform**: You can install them on **Linux**, **Mac** or **Windows**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s5-Practice-0/install-02.png)

You will need to **install** these three tools: [Python](https://www.python.org/downloads/) (3.6 or higher), [Git](https://git-scm.com/download) and [Pycharm Community Edition](https://www.jetbrains.com/es-es/pycharm/download)

### Installing python

Very likely you will have python (3.6 or higher) already installed. For checking that, **open a terminal** in your computer (in windows it is called "Símbolo del sistema") and **type** python. You should see how the python interpreter is opened. The exact output depends on your operating system and python version. This is what I can see in my laptop with Ubuntu/Linux 18.04:

```
$ python
Python 3.6.9 (default, Nov  7 2019, 10:44:02) 
[GCC 8.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

If you cannot open the python console, install it from here:  [Python installation](https://www.python.org/downloads/). Download the installer and execute them. **WINDOWS users**: It is very important that you **check** the option **Add python 3.x to Path** 

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s5-Practice-0/install-03.png)

### Installing Git

**Git** is the tool to allow us to have a **local repository** in our computer and connect it to our **remote repository** located in **Github**

* **Linux users**: open a terminal and write this command:

```
sudo apt install git
```

* **Mac/Windows users**: You have to manually install git from here: [Install Git](https://git-scm.com/download)
  * Download the Installer
  * Run the installer and chose the default options (click on next, next, next....)

Once installed, check that it is working correctly. Open a Terminal an type **git --version**. You will see something like this:

```
$ git --version
git version 2.17.1
```
(Your version may be different. It does not matter)

### Installing Pycharm Community Edition

You have to download the installer from this page: [Pycharm Community Edition](https://www.jetbrains.com/es-es/pycharm/download). **Execute the installer** and chose the **default options**

**Ubuntu/Linux users**, you install it directly from the **Ubuntu Store**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s5-Practice-0/install-04.png)

### Testing your tools

Once everything is installed, you can proceed with the instrucctions given in the [Session 2: Working with Pycharm and Github](https://github.com/myTeachingURJC/2019-2020-PNE/wiki/Session-1:-Tools-I#working-with-pycharm-and-github)

**I will help you** during the **Lab sessions** (and after the session if you want to stay). **Remember**: There are many of you, but I am only one, so be patience :-) If I do not have time to help you in this session, wait for the next (or after the class). In the meanwhile you can work in the lab

## Exercises

**Practice 0** will be **guided**. Every exercise will teach you something. The goal is to have a **working Seq0 module** for processing **DNA sequences** and to test it with some example programs. In the final exercises you will have to write some programs for answering the questions 

### Exercise 1: seq_ping()

The **seq_ping()** functions is just for testing. It prints the "OK" string on the console
* **Filename:** P0/Seq0.py
* **Description**: This file is the library for the DNA functions. In this first exercise you should write in there the seq_ping() function
* **Filename:** P0/Ex1.py
* **Description**: This is the **main program**. It should import the module Seq0. When this program is executed, you should see this on the **console**:

```
Testing the seq_ping() funcion
OK

Process finished with exit code 0
```

**Congrats!** You have created your **first python module**!

### Exercise 2: seq_read_fasta()

Implement the **seq_read_fasta(filename)** function. It should **open** a file, in FASTA format, and **return** a **String** with the **DNA sequence**. The head is removed, as well as the '\n' characters. This function should be written in the **Seq0.py** file

* **Filename**: P0/Ex2.py
* **Description**: Write a python program for opening the U5.txt file and writing into the console the first 20 bases of the sequence
* **Output**: This is what should be printed on the **Console**:

```
DNA file: U5.txt
The first 20 bases are:
ATAGACCAAACATGAGAGGC

Process finished with exit code 0
```
* **Considerations**:
  * Have in mind that the **DNA files** are stored in the **Session-04** folder and you are working now on the **P0 folder**. Create a constant with the path to the file:
  ```
  FOLDER = "../Session-04/"
  ```
  * Then another for the DNA filename:
  ```
  FILENAME = "U5.txt"
  ```
  * The full filename passed to the seq_read_fasta() should be the string **FOLDER + FILENAME**
 
### Exercise 3: seq_len()

Implement the **seq_len(seq)** function, that calculates the **total number of bases** in the sequence. It should be written in the **Seq0.py** file

* **Filename**: P0/Ex3.py
* **Desription**: Write a python program for calculating the total length of the 5 Genes: U5, ADA, FRAT1, FXN and U5. The program should call the seq_len() function
* **Output**: This is what should be seen on the console after the execution:
```
-----| Exercise 3 |------
Gene U5 ---> Length: 1314
Gene ADA ---> Length: 33912
Gene FRAT1 ---> Length: 3845
Gene FXN ---> Length: 25615

Process finished with exit code 0
```

* **Considerations**: 
  * Create a **list** with the names of the Genes
  * The **filename** can be obtained by adding the ".txt" string to the gene name
  * Use a **for loop** for iterating over the 5 genes and calculating their lengths

### Exercise 4: seq_count_base()

Implement the **seq_count_base(seq, base)** function, that calculates the **number** of times the **given base** appears on the sequence. It should be written in the **Seq0.py** file

* **Filename**: P0/Ex4.py
* **Desription**: Write a python program for calculating the number of each bases located on each of the five genes
* **Output**: This is what should be seen on the console after the execution:
```
-----| Exercise 4 |------

Gene U5:
  A: 360
  C: 229
  T: 491
  G: 234

Gene ADA:
  A: 7446
  C: 9011
  T: 8394
  G: 9061

Gene FRAT1:
  A: 746
  C: 1138
  T: 823
  G: 1138

Gene FXN:
  A: 6246
  C: 6422
  T: 6652
  G: 6295

Gene U5:
  A: 360
  C: 229
  T: 491
  G: 234

Process finished with exit code 0
```

* **Considerations**: 
  * Create a **list** with the four bases
  * For every gene, iterate over the bases, printing its number

### Exercise 5: seq_count()

Implement the **seq_count(seq)** function, that calculates the **number** of times all the bases appears on the sequence. It returns a dictionary with all the information. The keys of the dictionary are the bases: 'A', 'T', 'C' and 'G'. It should be written in the **Seq0.py** file

* **Filename**: P0/Ex5.py
* **Desription**: Write a python program for calculating the number of each bases located on each of the five genes. It similar to the exercise 4, but what is printed on the console is the **dictionary** returned by the seq_count() function
* **Output**: This is what should be seen on the console after the execution:
```
-----| Exercise 5 |------
Gene U5: {'A': 360, 'T': 491, 'C': 229, 'G': 234}
Gene ADA: {'A': 7446, 'T': 8394, 'C': 9011, 'G': 9061}
Gene FRAT1: {'A': 746, 'T': 823, 'C': 1138, 'G': 1138}
Gene FXN: {'A': 6246, 'T': 6652, 'C': 6422, 'G': 6295}
Gene U5: {'A': 360, 'T': 491, 'C': 229, 'G': 234}

Process finished with exit code 0
```

* **Considerations**: 
  * A dictionary in python is created using the curly brackets {} and placing inside the pairs key:value
  ```python3
  d = {'A':0, 'T':0, 'C':0, 'G':0}
  ```
  * In this example the d dictionary is created, which has the four bases as keys, and they all have been initialized to 0. You can access to any value by writing the key inside the brackets:
  ```python3
  d['A']  # -- Accesing the value of the 'A' base
  ``` 
### Exercise 6: seq_reverse()

Implement the **seq_reverse(seq)** function, that calculates the **reverse** of the given sequence. Imaging we have this sequence: "ATTCG". Its reverse is: "GCTTA". It should be written in the **Seq0.py** file

* **Filename**: P0/Ex6.py
* **Desription**: Write a python program for creating a new fragment composed of the first 20 bases of the U5 gene. This fragment should be printed on the console. Then calculate the reverse of this fragment by calling the seq_reverse() function. Finally print it on the console
* **Output**: This is what should be seen on the console after the execution:
```
------| Exercise 6 |------
Gene U5:
Frag: ATAGACCAAACATGAGAGGC
Rev : CGGAGAGTACAAACCAGATA

Process finished with exit code 0
```

* **Considerations**: 
  * The reverse of any string can be easily calculated by using the brackets [] with the correct values inside


### Exercise 7: seq_complement()

Implement the **seq_complement(seq)** function, that calculates a new sequence composed of the **complement** base of each of the original bases. The bases work in pairs. A and T are complement, as well as C and G. Therefore, the complement sequence of "ATTCG" is "TAAGC". It should be written in the **Seq0.py** file

* **Filename**: P0/Ex7.py
* **Desription**: Write a python program for creating a new fragment composed of the first 20 bases of the U5 gene. This fragment should be printed on the console. Then calculate the complement of this fragment by calling the seq_complement() function. Finally print it on the console
* **Output**: This is what should be seen on the console after the execution:
```
-----| Exercise 7 |------
Gene U5:
Frag: ATAGACCAAACATGAGAGGC
Comp: TATCTGGTTTGTACTCTCCG

Process finished with exit code 0
```

* **Considerations**: 
  * It is very easy to calculate the complement of the bases by defining a dictionary which store the complement of any base

### Exercise 8: processing the genes

Write a python program that automatically calculate the answer to this question:

* Which is the most frequent base in each gene?
----
* **Filename**: P0/Ex8.py
* **Output**: This is what should be seen on the console after the execution. The X letter is the answer for that gene (The value is not shown in this output, you should calculate it)
```
-----| Exercise 7 |------
Gene U5: Most frequent Base: X
Gene ADA: Most frequent Base: X
Gene FRAT1: Most frequent Base: X
Gene FXN: Most frequent Base: X
Gene U5: Most frequent Base: X

Process finished with exit code 0
```

## END of the session

The session is finished. Make sure, during this week, that everything in this list is checked!

* [ ] You have all the items of the session 4 checked!
* [ ] Your working repo contains the **P0 Folder** with the following files:
  * [ ] Ex1.py
  * [ ] Ex2.py
  * [ ] Ex3.py
  * [ ] Ex4.py
  * [ ] Ex5.py
  * [ ] Ex6.py
  * [ ] Ex7.py
  * [ ] Ex8.py
  * [ ] Seq0.py
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