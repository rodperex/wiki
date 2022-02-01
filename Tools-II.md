![](https://github.com/davidrol6/2021-2022-PNE/raw/master/s2-tool-2/Cover/Cover2.png)
# Session 2: Tools-II

* **Time**: 2h
* **Date**: Tuesday, Feb-1st-2022
* **Goals**:
  * Learn how to execute programs step by step
  * Learn the difference between step over, step into and step out
  * Practice with all the concepts introduced so far

## Contents

* [Introduction](#introduction)  
* [Step by Step execution](#step-by-step-execution)  
  * [Hello world step by step](#hello-world-step-by-step)  
    * [Setting our first breakpoint](#setting-our-first-breakpoint)  
    * [Entering the debug mode](#entering-the-debug-mode)  
    * [Our first step: Step OVER](#our-first-step-step-over)  
    * [Stepping over the next instructions](#stepping-over-the-next-instructions)  
  * [Count.py: Print the numbers from 1 to 20](#countpy-printing-numbers-from-1-to-20)  
  * [Sum20.py: Sum the 20 first integer numbers](#sum20py-sum-the-20-first-integer-numbers)  
* [Stepping into a function](#stepping-into-a-function)  
* [Exercises](#exercises)
  * [Exercise 1](#exercise-1)
  * [Exercise 2](#exercise-2)  
  * [Exercise 3](#exercise-3)  
* [End of the session](#end-of-the-session)
* [Author](#author)
* [Credits](#credits)
* [License](#license) 

## Introduction

Writing programs is not difficult. What is more complex is making them work as expected. When our programs do not work or generate strange errors, we say they have **bugs**. The process of **finding the errors** is called **debuging**: we want to remove all the bugs

In this session we will learn **how to debug** our programs by executing them **step by step**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/intro-01.jpg)

## Step by step Execution

The Pycharm IDE has an integrated tool for letting us to execute our programs line by line. This is what is called as **step by step execution**

### Hello world: step by step

Let's practice with the **hello.py** program that we already did in the **session 1**. It should be in the **Hello folder** in our **local working repository** (2019-2020-PNE-Practices)

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/hello-01.png)

As we have already execute it one time, there is an **existing configuration**. Therefore, we can execute again very easily just by **clicking on the green play button** (make sure that the selected configuration is hello)

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/hello-02.png)

A **new Run panel** is opened below. We can see there the **output** of the **print instructions**

#### Setting our first Breakpoint

As we are running the program, all the prints are executed one after another until the program finished. What we want to do now is executing them **step by step**

The **first step** is to select the line in which we want the program to stop. This is called a **breakpoint**. The program is executed until the breakpoint is reached. Then, the program is paused, and we can examine what has happend in the output console

Let's place a **Breakpoint** in the **first print** instruction. Go to the **right side** of the **line number** and doble click with the mouse. A new **red circle** will appear

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/hello-03.png)

We have placed a **Breakpoint** in the **line number 1** 

#### Entering the debug mode

once the Breakpoints are set (we can place more than one if we want) we press the **green bug button** on the right side of the run button

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/hello-04.png)

The program begins to execute until the first breakpoint is reached. In  our example, as the breakpoint is on the first line, none instruction is executed. The instruction on the breakpoint is **highlighted**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/hello-05.png)

A new **debug panel** opens in the bottom. The **debugger tab** is automatically selected. we can also notice a **green point** on the bug. This is for indicating that currently we are in **debug mode**

Click on the **Console Tab** right to the debugger tab

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/hello-06.png)

There is were the **printed messages** will appear

#### Our first step: STEP OVER

Let's execute the **current instruction**. Press on the small button that says **STEP OVER** (or press the F8 key)

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/hello-07.png)

We can see on the console the message printed by the first instruction. The line with the next instruction is **highlighted**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/hello-08.png)

**Congrats!!** You have executed your first instruction in debug mode!

### Stepping over the next instructions

We repeat the process for executing the other two remaining instructions: We click on the **STEP OVER** button again and the next **message** is shown in the **debug console**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/hello-09.png)

Finally, we click on **STEP OVER** again and the **last instruction** is executed and the program **finished**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/hello-10.png)

The **debug mode is finished**. We no longer see the green dot under the bug

In this **animation** all the process is shown

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/hello-11.gif)

### Count.py: Printing numbers from 1 to 20

Let's **debug our** second program. It is the **exercise number 2**, from the **session 1**. It prints the numbers from 1 to 20. This is the **code**:

```python
# Session 1. Exercise 2

for i in range(1, 21):
    print(i, end=' ')
```

Let's place a **breakpoint** in the print statement, in line 4. Chose the **count configuration** (or run the program if there is not a configuration yet) and press the **debug button**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/count-01.png)

The program is executed. It enters the for loop and reach the Breakpoint. Notice that inside the loop there is one variable i. Its value can be seen on the lower panel in the right. Currently i = 1

The **i** variable can also be seen on the right of the **for statement** ( i: 1). Click on the **Console TAB** and **STEP OVER** the print instruction

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/count-02.png)

The next instruction is **highlighted** (for) and the value of the **i variable** is printed on the **console**. **STEP OVER** again

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/count-03.png)

The **variable i** is **incremented to 2**, and the next print instruction is **highlighted**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/count-04.png)

Now, instead of Stepping over, let's resume the program clicking on the **resume button** (on the left) or by pressing the **F9 key**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/count-05.png)

The program is executed until the **next breakpoint** is reached:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/count-06.png)

We press the **resume button** again. We reach the same line, but the **variable i has been incremented**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/count-07.png)

We **repeat** this process until we reach the last value

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/count-08.png)

**The variable i is 20** (but it has not been printed yet on the console). We press the **resume button** for the last time. The execution is **completed** and the **debug mode ended**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/count-09.png)

It is easy to debug the programs, right? 🙂

In this **animation** the above execution can be seen

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/count-10.gif)

### Sum20.py: Sum the 20 first integer numbers

Let's debug the exercise 3 from the session 1: summing the first 20 integer numbers. This is the code:

```python
# Session 1. Exercise 3
# Calculate the sum of the 20 first integer numbers
# 1 + 2 + 3 + ... + 20
# Example working!

# -- Store the result
res = 0

for i in range(1, 21):
    res += i

print("Total sum: ", res)
```

Let's place the **Breakpoint** on the line number 10 (on the *res += i* sentence), chose the **sum20 configuration** and click on the **debug button**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/sum-01.png)

Now there are **two integer** variables: i and res. We see them in the **Variables tab** and in the **code window**. We press the **resume button** several time to see how the res variable is changed

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/sum-02.png)

We **repeat** the process. Then the **variable i** is 20 (last value) this is what we see:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/sum-03.png)

we press the resume button for the last time and see the result on the console. The debug is finished

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/sum-04.png)

## Stepping into a function

Let's create a **new program** for calculating the sum of the 20 first integers as well as the 100 first integers. We will call it as **sumN.py**

As this is a new program created during the **session 2**, we will store it in a new folder called **Session-02**

We need to convert the sum20.py program into a **function**, and then called it twice, using the arguments **n=20** and **n=100**. The code is this:


```python
# Function for calculating the sum of the
# N first integer numbers


def sumn(n):
    res = 0
    for i in range(1, n+1):
        res += i
    return res


# -- The main program starts here
print("Sum of the 20 first integers: ", sumn(20))
print("Sum of the 100, frist integers: ", sumn(100))
```
Before executing step by step, let's **run** it

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/sumN-01.png)

We see the results on the console. A **new configuration** called **sumN** has also been created

Place a **Breakpoint** in the first print sentence and execute **debug**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/sumN-02.png)

If we press the **STEP OVER** button, the **sumn** function is called, the result is calculated, printed on the console and the **next print instruction is highlighted**. Notice that we have **not executed** the instructions of the sumn function step by step

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/sumN-03.png)

If we press the **STEP OVER** button again, the same happens: the new value is calculated by calling to the sumn function, and the result value is printed on the console. Then the **program is finished**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/sumN-04.png)

Let's debug again. Click on the **debug button**. Now, click on the **Step into** button

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/sumN-06.png)

You can see that the **next instruction highlighted** is now the first **inside the sumn** function. Instead of moving to the next instruction in the main program, it has stopped in the first instruction inside the function

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/sumN-07.png)

If we press the **Step over** function, we can see what is going on **inside de function**, exactly in the same way than we did before. We can also see the **variables** used in the sumn function

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/sumN-08.png)

After executing some instruction, this is what we see:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/sumN-08.png)

If we want to finish the execution of the sumn function and stop in the upper level, were the function was previously called, we press the **STEP out** button

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/sumN-09.png)

After that, the instruction were the sumn function was called is **highlated**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/sumN-10.png)

We press the **STEP over** function and see the result on the console, just like the previous debugging. The next instruction is **highlighted**. Notice that now we **no longer see** the **n,res and i variables**. We are in an outer scope where that variables do not exists. They only exist in the sumn scope

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/sumN-11.png)

We can now **step over** or **step into** the sumn function. Let's step into again

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/sumN-12.png) 

As we are calling the sumn function with the parameter 100, the **n variables** equals **100** now (in the previous call it was n = 20)

We can finish the execution by clicking on the **resume button**. As there are no more Breakpoints, it will complete the execution until the end

The execution explained above can be seen in this **animation**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/sumN-13.gif)

## Exercises

Now it is your turn. The only way of learning how to debug a program, is debugging many programs!

Make sure that you have **upload all the exercises** form the **session 1** (that we have already solved in this session) in **Github**. The more you practice, the better. Then, continue with the exercises from the **session 2**:

### Exercise 1

* **Filename**: Session-02/fibonacci.py
* **Description**: Write a program (without creating any function) that prints on the console the first 11 terms of the [Fibonacci series](https://en.wikipedia.org/wiki/Fibonacci_number) (staring from 0)
* **Execute** the program **step by step**
* The output should be like this:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/ex1-01.png)

### Exercise 2

* **Filename**: Session-02/fiboN.py
* **Description**: Convert the previous program into the function fibon(n) that calculates the nth Fibonacci term and return it
* The main program should call the fibon() function and print the 5th, 10th and 15th terms in the console
* **Execute** the program **step by step**
* Use the step into button for watching how the fibon() function works. Try also the step out button
* The output should be like this:
![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/ex2-01.png)

### Exercise 3

* **Filename**: Session-02/fibo-sumN.py
* **Description**: Write a function called fibosum(n) that calculates the sum of the n first fibonacci terms. The main program should call this function twices, with the arguments n=5 and n=10
* **Execute** the program **step by step**
* Use the **step into** and **step out** buttons for debugging. Notice that now you have 2 functions at different levels (one function is calling the other). Use step into twice to enter into the fibon() function
* The output should be like this:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s2-tool-2/ex3-01.png)

## END of the session

The session is finished. Make sure, during this week, that everything in this list is checked!

* [ ] You have all the items of the session 1 checked!
* [ ] Your working repo contains the Session-01 Folder with the following files:
  * [ ] count.py
  * [ ] sum20.py
* [ ] Your working repo contains the Session-02 Folder with the following files:
  * [ ] sumN.py
  * [ ] fibonacci.py (Exercise 1)
  * [ ] fiboN.py (Exercise 2)
  * [ ] fibo-sumN.py (Exercise 3)

# Credits

* [Alvaro del Castillo](https://github.com/acs). He designed and created the original content of this subject. Thanks a lot :-)
* [Juan González-Gómez](https://github.com/Obijuan) (Obijuan)

# License

![](https://github.com/Obijuan/digital-electronics-with-open-FPGAs-tutorial/raw/master/wiki/portada/attribution-share-alike-creative-commons-license.png)

# Links

* [Universidad Rey Juan Carlos de Madrid](https://www.urjc.es/)
* [Escuela Técnica Superior de Ingeniería de Telecomunicaciones (URJC)](https://www.urjc.es/universidad/facultades/escuela-tecnica-superior-de-ingenieria-de-las-telecomunicaciones/content/etsit-escuela-tecnica-superior-de-ingenieria-de-telecomunicacion)