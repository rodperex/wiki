![](https://github.com/davidrol6/2021-2022-PNE/raw/master/s15-http-module-2/Cover/Cover.png)

# Session 15: Practice 5

* **Time**: 2h
* **Date**: Wednesday, March-30th-2022
* **Goals**:
  * Practicing with the HTTP python module
  * Develop the BASES2 server

## Contents

* [Introduction](#introduction)  
* [Exercises](#exercises)  
  * [Exercise 1: A.html](#exercise-1-ahtml)
  * [Exercise 2: info/A](#exercise-2-infoa)  
  * [Exercise 3: info/C](#exercise-3-infoc)  
  * [Exercise 4: info/G and info/T](#exercise-4-infog-and-infot)  
  * [Exercise 5: Error](#exercise-5-error)  
  * [Exercise 6: Index.html](#exercise-6-indexhtml)
* [End of the session](#end-of-the-session)
* [Author](#author)
* [Credits](#credits)
* [License](#license) 

## Introduction

The goal of this practice is to develop the same **web server** as the one of the practice 4, but using the **HTTP python module** instead of raw sockets. It should also treat **all the resources** requested as **HTML files**, so that the server can be fed with more data just by including more HTML files, and without having to modify the code 

This table describe the **names** of the resources (path) for getting the web pages. The entry **/filename** means "any filename". You can specify any filename. If the Server has it, it will send it to the client. Otherwise the Error.html page is returned

| Resource          | html File | Description |
|-------------------|-----------|-------------|
| **/info/A.html**  | info/A.html    |  Information about the Adenine base. Color: lightgreen |
| **/info/C.html**  | info/C.html    |  Information about the Cytosine base. Color: yellow |
| **/info/G.html**  | info/G.html    |  Information about the Guanine base. Color: ligthblue |
| **/info/T.html**  | info/T.html    |  Information about the Guanine base. Color: pink |
| **/**             | index.html|  Main page: index. Color: white |
| **/index.html**   | index.html|  Main page: index. Color: white |
| **/filename**     | filename  |  "filename" page if it exist |
| **/filename**     | Error.html|  Error page, if "filename" does not exist |

## Exercises

**NOTE**: This webserver is extremely easy if you already have finished the server from the Practice 4 and the exercises of the Session 14

For making it works, you only have to change **small things** and **pay attention** to the details 

### Exercise 1: A.html

Implement the server. Use the same HTML files from the practice 4, with small modifications for working ok on this server. The A,C, T and G HTML pages are store into the P5/info/ folder

* **Server Filename**: P5/Bases2-webserver.py
* **HTML files**: 
  * P5/index.html
  * P5/Error.html
  * P5/info/A.html
  * P5/info/C.html
  * P5/info/T.html
  * P5/info/G.html

In this **animation** you can see it working:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s15-http-module-2/exercise-01.gif)

## END of the session

The session is finished. Make sure, during this week, that everything in this list is checked!

* [ ] You have all the items of the session 14 checked!
* [ ] Your working repo contains the **P5 Folder** with the following files:
  * [ ] info/A.html
  * [ ] info/C.html
  * [ ] info/G.html
  * [ ] info/T.html
  * [ ] Error.html
  * [ ] index.html
  * [ ] Bases2-webserver.py
* [ ] All the previous files have been pushed to your remote Github repo


# Credits
* [Juan González-Gómez](https://github.com/Obijuan) (Obijuan)
* [Alvaro del Castillo](https://github.com/acs). He designed and created the original content of this subject. Thanks a lot :-)

# License

![](https://github.com/Obijuan/digital-electronics-with-open-FPGAs-tutorial/raw/master/wiki/portada/attribution-share-alike-creative-commons-license.png)

# Links

* [Universidad Rey Juan Carlos de Madrid](https://www.urjc.es/)
* [Escuela Técnica Superior de Ingeniería de Telecomunicaciones (URJC)](https://www.urjc.es/universidad/facultades/escuela-tecnica-superior-de-ingenieria-de-las-telecomunicaciones/content/etsit-escuela-tecnica-superior-de-ingenieria-de-telecomunicacion)