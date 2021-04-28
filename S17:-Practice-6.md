![](https://github.com/davidrol6/2020-2021-PNE/raw/master/s17-http-fomrs-ii/Cover/Cover.png)

# Session 17: Practice 6

* **Time**: 2h
* **Date**: Wednesday, April-28th-2020
* **Goals**:
  * Practicing with forms
  * Practicing with servers

## Contents

* [Introduction](#introduction)  
* [Exercises](#exercises)  
  * [Exercise 1: Ping](#exercise-1-ping)
  * [Exercise 2: Get](#exercise-2-get)  
  * [Exercise 3: Gene](#exercise-3-gene)  
  * [Exercise 4: Operation](#exercise-4-operation)  
* [End of the session](#end-of-the-session)
* [Author](#author)
* [Credits](#credits)
* [License](#license) 

## Introduction

The goal of this practice is to develop the second version of the **Seq server** developed in practice 3, but using the **HTTP python module** instead of raw sockets and accessing to its services by means of **HTML forms**

This table describe the **names** of the actions and their parameters

| Service name | Action | Argument |Response message | Description |
|--------------|--------|---------|-----------------|-------------|
| **PING**     | ping   |  none   | OK. See exercise 1  | Ping service for testing if the server is alive of not |
| **GET**      | get    | n: 0-4  | A sequence. See exercise 2 | Get the sequence n. It could be any valid sequence of any length. There are only 5 sequences, numbered from 0 to 4 |
| **GENE**     | gene   | name: U5, ADA, FRAT1, RNU6_269P, FXN | The sequence of the gene. See exercise 3 |  Get the complete sequence of the given GENE |
| **OPERATION**| operation | seq: A sequence, op: Operation to perform: info, comp, rev |  See exercise 4 | Perform the operation on the given sequence. INFO: Get more info, COMP: Calculate the complement, REV: Calculate the rev sequence|

The response message returned by the **INFO** service should be like this example:

```
Sequence: ATAGACCAAACATGAGAGGCT
Total length: 21
A: 9 (42.9%)
C: 4 (19.0%)
G: 5 (23.8%)
T: 3 (14.3%)
```

The names of the genes that are **valid** when calling the **GENE service** are: **U5**, **ADA**, **FRAT1**, **FXN**, **RNU6_269P**

## Exercises

As always, we will develop this server **step by step**, in the **Seq2-server.py** file. It will be extended in every exercise (but working on the same file)

### Exercise 1: PING

**Implement the ping service** in the server. It should return a **response message** with a page saying that the **server is alive**. It should include a **link** to the **main page**. If a different resource is requested an **Error** web page is returned

* **Server Filename**: P6/Seq2-server.py
* **HTML file**: P6/form-1.html
* **HTML file**: P6/Error.html
 
In this **animation** you can see it working:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s17-http-fomrs-ii/exercise-01.gif)

### Exercise 2: GET

Extend the previous server for **implementing the get service**. It should return the requested sequence (0 - 4). A **response message** with a page with the sequence is generated. It should include a **link** to the **main page**

* **Server Filename**: P6/Seq2-server.py
* **HTML file**: P6/form-2.html
 
This is how it should work:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s17-http-fomrs-ii/exercise-02.gif)

### Exercise 3: GENE

Extend the previous server for **implementing the gene service**. It should return the requested gene by its name. A **response message** with a page with the gene is generated. It should include a **link** to the **main page**

* **Server Filename**: P6/Seq2-server.py
* **HTML file**: P6/form-3.html
 
This is how it should work:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s17-http-fomrs-ii/exercise-03.gif)

### Exercise 4: Operation

Extend the previous server for **implementing the operation service**. It should return the requested operation on the sequence introduced. There are three operation: Info about the sequence, its complement and its reverse . A **response message** with a page with the results of the operation is generated. It should include a **link** to the **main page**

* **Server Filename**: P6/Seq2-server.py
* **HTML file**: P6/form-4.html
 
This is how it should work:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s17-http-fomrs-ii/exercise-04.gif)

## END of the session

The session is finished. Make sure, during this week, that everything in this list is checked!

* [ ] You have all the items of the session 16 checked!
* [ ] Your working repo contains the **P6 Folder** with the following files:
  * [ ] Seq2-server.py
  * [ ] Error.html
  * [ ] form-1.html
  * [ ] form-2 html
  * [ ] form-3 html
  * [ ] form-4 html
* [ ] All the previous files have been pushed to your remote Github repo


# Credits
* [Juan González-Gómez](https://github.com/Obijuan) (Obijuan)
![](https://github.com/Obijuan/digital-electronics-with-open-FPGAs-tutorial/raw/master/wiki/portada/logos-urjc-gsyc-peloto-jderobot.png)

* [Alvaro del Castillo](https://github.com/acs). He designed and created the original content of this subject. Thanks a lot :-)

# License

![](https://github.com/Obijuan/digital-electronics-with-open-FPGAs-tutorial/raw/master/wiki/portada/attribution-share-alike-creative-commons-license.png)

# Links

* [Universidad Rey Juan Carlos de Madrid](https://www.urjc.es/)
* [Escuela Técnica Superior de Ingeniería de Telecomunicaciones (URJC)](https://www.urjc.es/universidad/facultades/escuela-tecnica-superior-de-ingenieria-de-las-telecomunicaciones/content/etsit-escuela-tecnica-superior-de-ingenieria-de-telecomunicacion)