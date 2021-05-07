![](https://github.com/davidrol6/2020-2021-PNE/raw/master/s20-final-project/Cover/Cover.png)

# Session 20: Final project specification

* **Project tittle**:  Browsing human and vertebrates genome
* **Date**: Tuesday, May-7th-2021
* **Deadline**: Jun-2nd-2021


## Contents

* [Introduction](#introduction)  
* [Proyect structure](#project-structure)  
* [Project levels](#project-levels)  
* [Basic Level](#basic-level)
  * [Examples](#examples)  
  * [Mandatory files](#mandatory-files)  
  * [Report file example](#report-file-example)
* [Medium Level](#medium-level)  
  * [Examples](#examples-1)
  * [Mandatory files](#mandatory-files-1)
* [Advanced Level](#advanced-level)
  * [Mandatory files](#mandatory-files-2)
* [Author](#author)
* [Credits](#credits)
* [License](#license) 

## Introduction

Let's practice all the concepts we have learnt so far by doing a **final project**. You should develop a **python application** for getting information about the human and other vertebrates **genome**

The application **user interface** is a **web page** with **forms** for querying the genome database. We will use the database from the [ensembl project](http://www.ensembl.org/index.html). The API REST can be found in this link: [Ensembl REST API Endpoints](http://rest.ensembl.org/)

It is **important** that you **spend time** understanding this **API** and all the information available before you begin to code. There are many details and definitions involved that are necessary for a complete understanding of all the services provided by your application

As an Engineer, is your job to **understand** and **process** all the available information. Initially you may be a little lost... but **DON'T PANIC!** The more you read and test, the more you will understand it. All the projects initially look complex and are difficult to start. But little by little, everything makes sense. Read, work and test
 
## Project structure

* The project will be developed in your **github** account
* It should be stored in your working **2020-2021-PNE-Practices** repository in github
* It should be located inside the **Final-Project** folder
* Your application **filename** must be **Final-Project/server.py**. It must be listening on **port 8080**
* You can include any other additional files you need

## Project levels

The project is divided into three levels: **Basic**, **medium** and **advanced**. You decide were to stop. But, you can only access to the next level if the previous one is **working perfectly**

**Important!** For every level you should include a **Test report**: a text file in which you show the endpoints tested, the argument passed and the response from the server. This is a document that demonstrate that your endpoints are working. Only the **endpoints** shown in this report will be evaluated

## Basic LEVEL

* **Maximum score**: 6 points
* **Requirements**: You should have finished all the practices (P0 - P7) and have more than **6 weeks** of activity on github

Your application will be a **web server** that should provided some the following **4 services** using the **HTTP protocol**. The response should be an **HTML page** with the required information


|  Endpoint  |  Parameters | Endpoint | Description |
|---------------|-------------|-------------|-------------|
|  /listSpecies | limit (optional) | http://rest.ensembl.org/documentation/info/species |List the names of all the species available in the database. The limit parameter (optional) indicates the maximum number of species to show. If it is not specified, all the species will be listed | 
|  /karyotype   | specie  | https://rest.ensembl.org/documentation/info/assembly_info | Return information about the [karyotype](https://en.wikipedia.org/wiki/Karyotype) of a specie: The name (usually a number) of all the chromosomes |
| /chromosomeLength | specie, chromo |https://rest.ensembl.org/documentation/info/assembly_info | Return the Length of the chromosome named "chromo" of the given specie |
| /         | none | **Main endpoint**. The server should return an HTML page with the forms for accessing to all the previous services |

If other endpoint different than the previous is introduced, the server should response with an **HTML error page**

### Examples

These are examples of use of the previous endpoints

* http://localhost:8080/listSpecies?limit=10
* http://localhost:8080/listSpecies
* http://localhost:8080/karyotype?specie=mouse
* http://localhost:8080/chromosomeLength?specie=mouse&chromo=18

The **main page** should contain forms for accessing to the services. It should looks like this:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s20-final-project/basic-01.png)

(You can change the colors and the look and feel if you like, of course!)

In this **animation** you can seen an example of getting the names of **10 species** in the database and the **human Kariotype**. Notice that it may take some time (as it has to connect to the remote ensemble database)

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s20-final-project/basic-02.gif)

In this animation we are getting the Length of the chromosome 18th in the mouse

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s20-final-project/basic-03.gif)

Again, notice that it takes some time for the application to get the answer from the data base

Finally, if any requested data is not found, the application should show us an **error page**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s20-final-project/basic-04.gif)


### Mandatory Files

Your basic application should contains **at least** the following files:

* **File**:  Final-Project/server.py
  * **Description**: Main file for executing your application. It implements the 4 basic endpoints mentioned in the specification 
* **File**: Final-Project/report-basic.txt
  * **Description**: Report file. It is a text file that contains the endpoints that you have tested and the information returned by your application to the browser. The purpose of this file is to document the functioning of your server, so that other engineer can review it 

### Report file example

The report file is a **text file** (.txt) with **information **about the tests you have performed on your server. This is an example of how it looks like:

```
Test report example
====================

---> listSpecies endpoint

* TEST 1:

* Input:

http://127.0.0.1:8080/listSpecies?limit=2

* output:

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>LIST OF SPECIES IN THE BROWSER</title>
</head>
<body style="background-color: lightblue;">
<body>
   The total number of species in the ensembl is : 267 <br>
   The limit you have selected is : 2 <br>
   The names of the species are : <ul><li>Burton's mouthbrooder</li><li>Agassiz's desert tortoise</li>
</body>
</html>

...
...
Many more test here!
...
...
```

The number of tests you should include here is up to you. You are the engineer, so you are responsible for ensuring that your server works. How many test you should perform at least to guaranteed that your server is working? At least one test per service, but, the more tests, the better...


## Medium level

* **Maximum score**: 8 points
* **Requirements**: You should have finished the Basic level (with an score equal or greater than 5)

Extend the **Basic server** with the following **services**. Make sure that the Basic services continue working well once you have added the new ones

|  Endpoint     |  Parameters | Description |
|---------------|-------------|-------------|
| /geneSeq | gene | Return the sequence of a given **human gene** |
| /geneInfo | gene | Return information about a **human gene**: start, end, Length, id and Chromosome name |
| /geneCalc  | gene | Performs some calculations on the given human gene and returns the total length and the percentage of all its bases |

You can use the **/sequence/id/:id** endpoint. In some operations is neccessary to **perform some calculations** on the data. Use the **Seq class** developed in the practices

### Examples

* http://localhost:8080/geneSeq?gene=FRAT1
* http://localhost:8080/geneInfo?gene=FRAT1
* http://localhost:8080/geneCalc?gene=FRAT1

As this is a medium level, no more information is given to you. You should read the Ensembl API and think of how to implement those services

### Mandatory Files

Your Medium level application should contains **at least** the following files:

* **File**:  Final-Project/server.py
  * **Description**: Main file for executing your application. It implements the 4 basic endpoints + the 4 medium endpoints mentioned in the specification 
* **File**: Final-Project/report-medium.txt
  * **Description**: Report file. It is a text file that contains **ALL* the endpoints that you have tested and the information returned by your application to the browser. The purpose of this file is to document the functioning of your server, so that other engineer can review it. You should test AGAIN the **basic services** for ensuring that they are still working and write the result in this report along with the information of the new services

## Advanced level

* **Maximum score**: 10 points
* **Requirements**: You should have finished the Medium level (with an score equal or greater than 7)

Convert the previous user API into a **REST API**. If the parameter **json=1** is included, the server will create a json object with the requested data and send it to the client. When the json parameter is not present, the server response with the previous HTML pages (It should behaves the same as in the basic and medium levels).

In order to test the server, you should create a **client** that makes request to the server, process the received json file and print the information on the console

### Mandatory files

* **File**:  Final-Project/server.py
  * **Description**: Main file for executing your application. It implements the 4 basic endpoints + the 4 medium endpoints mentioned in the specification 
* **File**:  Final-Project/client.py
  * **Description**: Main file for executing your application. It implements the 4 basic endpoints + the 4 medium endpoints mentioned in the specification 
* **File**: Final-Project/report-advanced.txt
  * **Description**: Report file. It is a text file that contains **ALL* the endpoints that you have tested and the information returned by your application. The purpose of this file is to document the functioning of your server, so that other engineer can review it. You should test AGAIN the **basic services** and the **medium services** and then with the json parameter activated 

# Credits
* [Juan González-Gómez](https://github.com/Obijuan) (Obijuan)

![](https://github.com/Obijuan/digital-electronics-with-open-FPGAs-tutorial/raw/master/wiki/portada/logos-urjc-gsyc-peloto-jderobot.png)

* [Alvaro del Castillo](https://github.com/acs). He designed and created the original content of this subject. Thanks a lot :-)

# License

![](https://github.com/Obijuan/digital-electronics-with-open-FPGAs-tutorial/raw/master/wiki/portada/attribution-share-alike-creative-commons-license.png)

# Links

* [Universidad Rey Juan Carlos de Madrid](https://www.urjc.es/)
* [Escuela Técnica Superior de Ingeniería de Telecomunicaciones (URJC)](https://www.urjc.es/universidad/facultades/escuela-tecnica-superior-de-ingenieria-de-las-telecomunicaciones/content/etsit-escuela-tecnica-superior-de-ingenieria-de-telecomunicacion)