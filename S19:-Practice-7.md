![](https://github.com/davidrol6/2021-2022-PNE/raw/master/s19-json-rest-II/Cover/Cover.png)

# Session 19: Practice 7

* **Time**: 2h
* **Date**: Wednesday, Apr-27th-2022
* **Goals**:
  * Practicing with JSON and the API REST
  * Reading information from the [Ensembl project](http://www.ensembl.org/index.html)

## Contents

* [Introduction](#introduction)  
* [Exercises](#exercises)  
  * [Exercise 1: Ping](#exercise-1-ping)
  * [Exercise 2: Gene identification string](#exercise-2-gene-identification-string)  
  * [Exercise 3: Getting a remote gene](#exercise-3-getting-a-remote-gene)  
  * [Exercise 4: Processing the information of a gene](#exercise-4-processing-the-information-of-a-gene)  
  * [Exercise 5: Information of all the genes](https://github.com/myTeachingURJC/2019-2020-PNE/wiki/Session-19:-Practice-7#exercise-5-information-of-all-the-genes)  
* [End of the session](#end-of-the-session)
* [Author](#author)
* [Credits](#credits)
* [License](#license) 

## Introduction

The goal of this practice is to develop a **python application** that reads **10 genes** from the [Ensembl database](http://www.ensembl.org/index.html) and perform some **calculations** on them: total number of bases, number of every base and its percentage and most frequent base

These are the **genes** that we want to get from the **remote database**: FRAT1, ADA, FXN, RNU6_269P, MIR633, TTTY4C, RBMY2YP, FGFR3, KDR, ANK2 

This practice is **guided**. On every exercise we will implement new functionalities in our application

I recommend you to read again the information on the **Session-4**: [The Ensembl genome browser](https://github.com/myTeachingURJC/2019-2020-PNE/wiki/Session-4:-The-ensembl-genome-browser)

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s19-json-rest-II/architecture-01.png)

Recall that the **ensembl database** can be accessed in two ways. The first one is by means of a **browser**. We write the **ensembl URL** in the brower and we get a web page, provided by the emsembl server. This interface is meant for humans

The second one is an **interface for applications**. The applications can get objects directly from the server by means of its **API REST**. Therefore, the first step is to **know** this API: what objects can we get from the databse and what are the names we should use for accessing to that resources. These names are called **endpoints**

Here you can find the [API REST of the ensembl project](https://rest.ensembl.org/). You should have a look at it to get familiar with the terminology and names

## Exercises

Let's create our first application that receives information directly from a remote application

### Exercise 1: PING

Go to the [API REST of the ensembl project](https://rest.ensembl.org/) and try to find an **endpoint** for checking if the **service is alive** (try searching for ping)

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s19-json-rest-II/exercises-01.png)

**Click** on the ping endpoint. You will see the **documentation**. As a Engineer is your work to read all the provided information and understand how this endpoint works. I will help you a litlte bit

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s19-json-rest-II/exercises-02.png)

The **name** of the endpoint is **info/ping** and it should be accessed using the HTTP **GET method**. On the top right we can see **all the formats** in which the information can be received: json, xml and jsonp. We are using json

In the bottom there is an **example** on how to use this endpoint. Click on the [given URL](https://rest.ensembl.org/info/ping?content-type=application/json): 

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s19-json-rest-II/exercises-03.png)

Let's **analyze** the URL:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s19-json-rest-II/exercises-04.png)

It consist of three parts:

* **The server name**: rest.ensembl.org
* **The endpoint name**: /info/ping
* **The endpoint parameters**: content-type=application/json

The **parameter content-type** indicates the **format** in which the application wants to receive the data. In our case we should set it to "application/json", because we are using the **json format**

In the **browser** we can see that we have **received** one **object**, which has a **property** called **"ping"** and its values is **1**. It means that the **server is alive**

Try to receive the information in another format, for example in **XML**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s19-json-rest-II/exercises-05.png)

#### Ping test

Implement a **python client**, using the **http.client module**, for accesing to the ensembl's ping endpoint. It should print on the console the server name, the complete URL and a message telling the state of the server

* **File**: P7/EX01-ping.py
* **Description**:

The program should read the **object** provided by the server and store it in a **variable** called **response**. Then, it should check the **response['ping']** property and **print a message** if it is equal to 1

This is what it should be **printed on the console** after executing the client:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s19-json-rest-II/exercises-06.png)

### Exercise 2: GENE identification string

Every **sequence** on the ensembl database has an identifier, called **stable identifier** (id). If you want to get a **gene**, you can use the [/sequence/id](https://rest.ensembl.org/documentation/info/sequence_id) endpoint. You should pass the **stable identifier** as the **first argument**

As an example, the **identifier** for the [SRCAP](https://en.wikipedia.org/wiki/SRCAP) gene is **ENSG00000080603**

In this exercise you have to find the **stable identifiers** of the following genes: **FRAT1**, **ADA**, **FXN**, **RNU6_269P**, **MIR633**, **TTTY4C**, **RBMY2YP**, **FGFR3**, **KDR**, **ANK2**

* **File**: P7/EX02-gene-id.py
* **Description**: Create a **dictionary** called GENES that contains the name of the genes and their identifiers. The program should print all the entries in the dicctionary with their identifiers:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s19-json-rest-II/exercises-07.png)

If you want to get, for example, the identifier for the FRAT1 gene, you use: GENES['FRAT1']

### Exercise 3: Getting a remote gene

* **File**: P7/EX03-gene-MIR633.py
* **Description**: In this exercise you have to program a **client** for connecting to the [/sequence/id](https://rest.ensembl.org/documentation/info/sequence_id) endpoint and getting the **sequence** and **description** of the **MIR633 Gene**

Your program should print this information in the **console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s19-json-rest-II/exercises-08.png)

### Exercise 4: Processing the information of a gene

Now that we can **get genes** from the **server**, it is time to perform some **calculations** with them. We will use the **Seq1 Class** that we created in **Practice 1**

* **File**: P7/EX04-gene-process.py
* **Description**: The program should ask the user to **enter** the **gene name** and then get the gene from the server, print the **gene's name**, its **description** (same as exercise 3), the **total length**, then **number of bases**, the **base percentage** and the **most frequent Base** in the sequence

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s19-json-rest-II/exercises-09.png)

In this **animation** you can see the program running

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s19-json-rest-II/exercise-10.gif)


### Exercise 5: Information of all the genes

* **File**: P7/Ex05-gene-all.py
* **Description**: Create a python program for performing the same calculations than in exercise 4, but for ALL the genes, not only one. The gene's names should be obtained from the Dictionary and not from the user

In this **animation** you can see how it works:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s19-json-rest-II/exercises-11.gif)


## END of the session

The session is finished. Make sure, during this week, that everything in this list is checked!

* [ ] You have all the items of the session 18 checked!
* [ ] Your working repo contains the **P7 Folder** with the following files:
  * [ ] EX01-ping.py
  * [ ] EX02-gene-id.py
  * [ ] EX03-gene-MIR633.py
  * [ ] EX04-gene-process.py
  * [ ] EX05-gene-all.py
* [ ] All the previous files have been pushed to your remote Github repo

# Credits

* [Juan González-Gómez](https://github.com/Obijuan) (Obijuan)
* [Alvaro del Castillo](https://github.com/acs). He designed and created the original content of this subject. Thanks a lot :-)

# License

![](https://github.com/Obijuan/digital-electronics-with-open-FPGAs-tutorial/raw/master/wiki/portada/attribution-share-alike-creative-commons-license.png)

# Links

* [Universidad Rey Juan Carlos de Madrid](https://www.urjc.es/)
* [Escuela Técnica Superior de Ingeniería de Telecomunicaciones (URJC)](https://www.urjc.es/universidad/facultades/escuela-tecnica-superior-de-ingenieria-de-las-telecomunicaciones/content/etsit-escuela-tecnica-superior-de-ingenieria-de-telecomunicacion)