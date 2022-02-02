![](https://github.com/davidrol6/2021-2022-PNE/raw/master/s3-practicing/Cover/Cover.png)

# Session 3: Practicing with the TOOLs

* **Time**: 2h
* **Date**: Wednesday, Feb-02th-2022
* **Goals**:
  * Practice by doing
  * Practicing with Github
  * Practicing with Pycharm
    * Running programs
    * Debugging programs

## Contents

* [Introduction](#introduction)  
* [Exercises](#exercises)
  * [Exercise 1: Finding the bug](#exercise-1-finding-the-bug)  
  * [Exercise 2: Counting DNA bases](#exercise-2-counting-dna-bases)
  * [Exercise 3: Counting DNA bases from a file](#exercise-3-counting-dna-bases-from-a-file)
* [End of the session](#end-of-the-session)
* [Author](#author)
* [Credits](#credits)
* [License](#license) 

## Introduction

It is very important that you learn to use the tools: **Github** + **pycharm**. You should get confident with them. In this session you will have **time to practice** by your own. There are some proposes exercises for you to work

If you have not finished the exercises proposed in the previous sessions do it now, and when finished, continue with the exercises proposed in this session. It is very important that you try to do all the exercises

## Exercises

All these exercises should be stored in your **working repo** in the **Session-03** folder. Do not forget to upload them to Github


### Exercise 1: Finding the bug!
* **Filename**: Session-03/debug_me.py. Create the python with this content:
```python
# --- Find the error!


def g(a, b):
    return a - b


def f(a, b, c, d):
    t0 = a + b - g(a, 0)
    t1 = g(c, d)
    t3 = 2 * (t0 / t1)
    return t0 + 2*t1 + t3*t3


# -- Main program
print("Result 1: ", f(5, 2, 5, 0))
print("Result 2: ", f(0, 2, 3, 3))
print("Result 3: ", f(1, 3, 2, 3))
print("Result 4: ", f(1, 9, 22.0, 3))
```

* Execute the program. What happens?
* Execute it step by step. Could you find where is the problem!

### Exercise 2: Counting DNA Bases

* **Filename**: Session-03/dna_count.py
* **Description**: Create a program for counting the number of **bases** presented in a **DNA sequence**. The user introduces a sequence of letter representing the DNA chain. For example: CATGTAGACTAG. Our program should calculate the **total length**, and the number of bases that compound the sequence. In the previous example sequence, the **output** of our program should be like this:

```
Introduce the sequence: CATGTAGACTAG
Total length: 12
A: 4
C: 2
T: 3
G: 3
```
* **Considerations**: 
  * You **must** use a *loop* for counting the bases
  * Suppose that the user always introduce **correct sequences** (you do not have to manage any error yet)

### Exercise 3: Counting DNA bases from a file

* **Filename**: Session-03/dna_count_file.py
* **Filename**: Session-03/dna.txt. Text file with the **DNA sequence**. It can have sequences in separated lines. This is an example of the DNA text file: 
```
AGTACACTGGT
ACCAGTGTACT
ATGGCCATTGTAATGGGCCGCTGAAAGGGTGCCCGATAG
```
* **Description**: Write a program that opens the **dna.txt** file and calculates the **total number of bases**, and the **number** of the **different bases**
* **Considerations**: 
  * You **must** use a *loop* for counting the bases
  * Suppose that the DNA files always contains **correct sequences** (you do not have to manage any error yet)

## END of the session

The session is finished. Make sure, during this week, that everything in this list is checked!

* [ ] You have all the items of the session 2 checked!
* [ ] Your working repo contains the **Session-03** Folder with the following files:
  * [ ] debug_me.py
  * [ ] dna_count.py
  * [ ] dna_count_file.py
  * [ ] dna.txt

# Credits
* [Juan González-Gómez](https://github.com/Obijuan) (Obijuan)
* [Alvaro del Castillo](https://github.com/acs). He designed and created the original content of this subject. Thanks a lot :-)

# License

![](https://github.com/Obijuan/digital-electronics-with-open-FPGAs-tutorial/raw/master/wiki/portada/attribution-share-alike-creative-commons-license.png)

# Links

* [Universidad Rey Juan Carlos de Madrid](https://www.urjc.es/)
* [Escuela Técnica Superior de Ingeniería de Telecomunicaciones (URJC)](https://www.urjc.es/universidad/facultades/escuela-tecnica-superior-de-ingenieria-de-las-telecomunicaciones/content/etsit-escuela-tecnica-superior-de-ingenieria-de-telecomunicacion)