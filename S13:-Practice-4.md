![](https://github.com/davidrol6/2021-2022-PNE/raw/master/s13-http-2/Cover/Cover2.png)

# Session 13: Practice 4

* **Time**: 2h
* **Date**: Wednesday, March-16th-2022
* **Goals**:
  * Practicing with web servers
  * Practicing with HTML

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
* [Credits](#credits)
* [License](#license) 

## Introduction

The goal of this practice is to develop a **web server** with information about the **four bases**: A, C, T and G. Each base should have **its page**, with the following information: **Name**, **letter**, **chemical formula** and a **link** to the wikipedia URL with **more information**. In addition, each page will be in a **different color**. This table describe the **names** of the resources (path) for getting the web pages

| Resource     | html File | Description |
|--------------|-----------|-------------|
| **/info/A**  | A.html    |  Information about the Adenine base. Color: lightgreen |
| **/info/C**  | C.html    |  Information about the Cytosine base. Color: yellow |
| **/info/G**  | G.html    |  Information about the Guanine base. Color: ligthblue |
| **/info/T**  | T.html    |  Information about the Guanine base. Color: pink |
| **/**        | index.html|  Main page: index. Color: white |
| any other    | error.html|  Error page. Color: red |

## Exercises

We will implement the **Web Server** step by step. The exercise will guide you

### Exercise 1: A.html

* **Filename:** P4/A.html

Let's start by writing the **HTML page** for the **Adenine** base. We will use it as a **template**. The pages for the other bases will be similar but with a different color and information

The page should look like this:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s13-http-2/exercises-01.png)

You can **preview** your page with pycham. Just open the html file in pycharm and press on the top right brower icons. For example in firefox's icon:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s13-http-2/exercises-02.png)

The page is quite similar to the Page of the **Green server**. Use the **H1 tags** for the base name, and the **P tags** for the **letter** and its **chemical formula**. Finally, you can place **links** to other **URLS** using the **a tag**. In this example you can see how to place a link to the wikipedia's main page:

```html
<a href="https://en.wikipedia.org/">Wikipedia</a>
```

### Exercise 2: info/A

* **Filename**: P4/EX2.py
* **Description**: Write a webserver that returns the **A.html** file when the **info/A** resource is **requested** by the client. When the URL **http://127.0.0.1:8080/info/A** is written in the browser, we should see the **web page** of the **A base**. If another resource is requested, the server will send a response message with a **blank body** (therefore a blank page will be shown) 

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s13-http-2/exercises-03.png)

### Exercise 3: info/C

* **Filenames**: P4/C.html and P4/EX3.py
* **Description**: Extend the previous web server for accessing to the web pages of the **C base**, in addition to the A base. It should be available in the **path /info/C**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s13-http-2/exercises-04.png)

### Exercise 4: info/G and info/T

* **Filenames**: P4/T.html and P4/EX4.py
* **Description**: Extend the previous web server for accessing to the web pages of the **G** and **T** bases, in addition to A and C. They should be available in the **path /info/G** and **/info/T** respectively

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s13-http-2/exercises-05.png)

### Exercise 5: Error

* **Filename:** P4/Error.html and P4/EX5.py
* **Description**: Extend the previous web server.  If the user tries to access to any other resource not implemented, and error page should be shown

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s13-http-2/exercises-06.png)


### Exercise 6: index.html

* **Filename:** P4/index.html and P4/EX6.py
* **Description**: Final version of the web server. When you connect to URL: **http://127.0.0.1:8080/** you get the main page: **index.html** with **links** to the other bases:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s13-http-2/exercises-07.png)

In addition, **modify** all the other **html** files (A.html, C.html, G.html, T.html and Error.html) for including a **link** to the **main page**. In this **animation** you can see how it works:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s13-http-2/exercises-08.gif)
 

## END of the session

The session is finished. Make sure, during this week, that everything in this list is checked!

* [ ] You have all the items of the session 12 checked!
* [ ] Your working repo contains the **P4 Folder** with the following files:
  * [ ] A.html
  * [ ] C.html
  * [ ] G.html
  * [ ] T.html
  * [ ] Error.html
  * [ ] index.html
  * [ ] EX2.html
  * [ ] EX3.html
  * [ ] EX4.html
  * [ ] EX5.html
  * [ ] EX6.html
* [ ] All the previous files have been pushed to your remote Github repo


# Credits
* [Juan González-Gómez](https://github.com/Obijuan) (Obijuan)
* [Alvaro del Castillo](https://github.com/acs). He designed and created the original content of this subject. Thanks a lot :-)

# License

![](https://github.com/Obijuan/digital-electronics-with-open-FPGAs-tutorial/raw/master/wiki/portada/attribution-share-alike-creative-commons-license.png)

# Links

* [Universidad Rey Juan Carlos de Madrid](https://www.urjc.es/)
* [Escuela Técnica Superior de Ingeniería de Telecomunicaciones (URJC)](https://www.urjc.es/universidad/facultades/escuela-tecnica-superior-de-ingenieria-de-las-telecomunicaciones/content/etsit-escuela-tecnica-superior-de-ingenieria-de-telecomunicacion)