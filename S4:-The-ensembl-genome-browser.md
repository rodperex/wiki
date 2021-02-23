![](https://github.com/davidrol6/2020-2021-PNE/blob/master/s4-ensemble/Cover/Cover.png)

# Session 4: The ensembl genome browser

* **Time**: 2h
* **Date**: Tuesday, Feb-23th-2021
* **Goals**:
  * Learn about the Ensembl database
  * Know how to download dna sequences from Emsembl
  * Practicing with real dna sequence files

## Contents

* [Introduction](#introduction)  
* [Architecture](#architecture)
* [Formats](#formats) 
* [Playing with Ensembl](#playing-with-ensembl)
  * [Accesing the Human gnome](#accesing-the-human-gnome)  
  * [Accesing a single gene](#accesing-a-single-gene)  
* [Exercises](#exercises)
  * [Exercise 1](#exercise-1)  
  * [Exercise 2](#exercise-2)  
  * [Exercise 3](#exercise-3)  
  * [Exercise 4](#exercise-4)  
  * [Exercise 5](#exercise-5)  
* [End of the session](#end-of-the-session)
* [Author](#author)
* [Credits](#credits)
* [License](#license) 

## Introduction

[ensembl.org](http://www.ensembl.org/index.html) is one of several well known **genome browsers** for the retrieval of **genomic information**. It can be directly used from the **web page**. But, It can also be used by accessing directly to its **databases** by means of a [Rest API](https://github.com/Ensembl/ensembl-rest/wiki)

![](https://github.com/myTeachingURJC/2018-19-PNE/raw/master/wiki/s03-s04_tools/p0-03.png)

You can find **more information** in the [Ensambl wikipedia page](https://en.wikipedia.org/wiki/Ensembl_genome_database_project)

As **BIO-specialists**, you should be able to use the databases and understand the underlying concepts: genome, DNA, bases and so on. Concepts that computer scientists and Electronic Engineers are not familiar with

As **Engineers**, you should understand the **technology behind these databases**: the networks, the **internet architecture**, the **protocols**, the **formats**... and how to create **applications** that can access these databases. This is what this subject, the **Programming in Network Environments**, is about

## Architecture

This is a drawing of the main ideas of the architecture we are using in this subject

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/architecture-01.png)

We have the **Ensembl database**, that is located anywhere on the internet. It has a lot of information about the **vertebrates gnome**. There is also a **server** that is capable of accessing to this **huge database** and give the information to us. On one hand, any user can access this database using the **browser**. In this case the server is showing **web pages**. On then other hand, the server can also give that information to **other apps** on the internet (not users)

We will learn how to create **python clients** capable of accessing to this information. We will also learn how to create **python apps** that are both a **client** and a **server**. On one side they offer a service to both users/apps. On the other side they are client that ask for information to the **Ensembl** database, process it and return it to the user/app

We have to learn the **terminology** and all the **protocols**, **data formats** and **APIs** for implementing it in our **python apps** 

## Formats

The information located in the databases is available in **different formats**. The most important are:

* [FASTA](https://en.wikipedia.org/wiki/FASTA_format): for representing either **nucleotide** sequences or **peptide** sequences. This is a format used in **Bioinformatics** applications
* [JSON](https://en.wikipedia.org/wiki/JSON): Generic format for representing any **data object**
* [XML](https://en.wikipedia.org/wiki/XML): is a **markup language** that defines a set of rules for encoding documents in a format that is both human-readable and machine-readable

As Engineers we should **understand that formats**, and to be able to **create programs** for **reading** data in those formats, and to **write** information with them

## Playing with Ensembl

Just to **get familiar** with the **Ensembl web page**, Let's play a little bit using the **browser**

* Enter into the [ensembl.org](http://www.ensembl.org/index.html) web page
* Let's have a look of all the species available in the database. Click on **View full list of all Ensembl species**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/ensembl-01.png)

### Accesing the Human gnome

* There appear a list of all the species. Write **human** on the right for shortening the list, and then click on the **human link**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/ensembl-02.png)

* The page of the **human gnome** is shown in the browser. Let's have a look at the **Human karyotype**. Click on the **view karyotype** option

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/ensembl-03.png)

* We can see now all the **chromosomes** of the Human gnome. Let's click on the **Chromose number 16**, for example

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/ensembl-04.png)

* We see a summary of the chromose. Let's select now a zone, with the mouse, near the the q21 region. Then click on **Jump to region overview** 

![](https://github.com/myTeachingURJC/2019-2020-PNE/blob/master/s4-ensemble/ensembl-05.png)

* In the new panel, below, you will find the names of the **genes** located on that **region**. Choose one, for example the **RNU6-269P**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/ensembl-06.png)

* Then click on **Gene ID**. We want to have **more information** about this gene

https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/ensembl-07.png

* The **summary page** of that gene is shown. Now click on the left, on the **Sequence option**

![](https://github.com/myTeachingURJC/2019-2020-PNE/blob/master/s4-ensemble/ensembl-08.png)

* On the **bottom left** we can see a new button for **downloading** that sequence

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/ensembl-09.png)

* We select the **FASTA format** (the default) and click on **Download**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/ensembl-10.png)

* A file called **Homo_sapiens_RNU6_269P_sequence.fa** will be download. We chose the **Save File** option and click on **OK**
![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/ensembl-11.png)

* After some seconds we will see the file available on the folder were it was saved (in this example it is located in the Download directory) 

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/ensembl-12.png)

* Just doble click on it from the file manager to open it. You are seeing all the bases of the RNU6-269P gene! Congrats! You've downloaded your fist gene sequence! :-)

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/ensembl-13.png)

Now that we have that file with the bases, we can perform **calculations** such as the total number and the percentages of each base. We will write **python programs** to do it automatically

### Accesing a single gene

It is also possible to download the **sequence of a Gene** just knowing its **name**. Let's have a look at the [human Gnome in wikipedia](https://en.wikipedia.org/wiki/Human_genome)

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/wikipedia-01.png)

**Scroll down** until the section called **Molecular organization and gene content**. There we can see all the chromosomes

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/wikipedia-02.png)

Click on the **Chromosome number 10**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/wikipedia-03.png)

There you will see all the information related to this chromosome. On the right you can also find a **link to the ensembl database**. Let's scroll down to the **Gene List section** first

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/wikipedia-04.png)

You can see there the **names** of all the genes located in the Chromose 10. Let's find the **FRAT1 gene**, for example, and click on it to see **more information**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/wikipedia-05.png)

**Scroll down** the page. On the **right side** there is a summary of the Gene. You will find there a **link** to the gene in the **Ensembl database**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/wikipedia-06.png)

You will see the page in Ensembl, similar to the one that we already saw. Just click on the **Sequence option** on the left and repeat the previous process for **downloading the FRAT1** gene sequence to a file

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/wikipedia-07.png)

You can also go to the **Emsambl main page** and enter **search** for the **FRAT1 gene**: 

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/wikipedia-08.png)

Then press the **GO** button. The first entry is what we are looking for:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s4-ensemble/wikipedia-09.png)

That link will take us directly to the previous **FRAT1 Ensembl page**, were we can **download** the FRAT1 gene

## Exercises

Let's practice with the ensembl database. Create the **Session-04 folder** in your working repository. Store all the files create during this session (exercises and sequences)

### Exercise 1

Get from the **Ensembl database** the following sequences of the given **Genes**:

* **RNU6_269P** gene, from Chromose 16 of the Human gnome
  * **Filename**: Session-04/RNU6_269P.txt 
* **FRAT1**. Chromosome 10. Human Gnome
  * **Filename**: Session-04/FRAT1.txt
* **U5**. Clown anemonefish
  * **Filename**: Session-04/U5.txt
* **ADA**. Human Gnome. In which Chromosome is found?
  * **Filename**: Session-04/ADA.txt
* **FXN**. Cat Gnome. In which Chromosome is found?
  * **Filename**: Session-04/FXN.txt

### Exercise 2

From now on, we will use the **module Path** from the [Pathlib library](https://docs.python.org/3/library/pathlib.html) for accessing the files. This is a very **simple** and **modern** way of working with files and paths

* **Filename**: Session-04/print_file.py
* **Description**: This program just opens a text file (for example a dna file) and prints the contents on the console. The goal is to **get familiar** with the **Path module**. This exercise is already solve for your. Just try it and make sure you understand it. No error control is implemented yet

```python3
from pathlib import Path

# -- Constant with the new of the file to open
FILENAME = "RNU6_269P.txt"

# -- Open and read the file
file_contents = Path(FILENAME).read_text()

# -- Print the contents on the console
print(file_contents)
```
 
### Exercise 3

Have a look at the **dna files** that you have downloaded in the previous exercise. Notice that they consist of **two parts**: a **head** an a **body**. The **first line** is the head, which starts with the '\>' symbol. The following lines are the body and contains the **sequence of nucleotides**

* **Filename**: Session-04/head.py
* **Desription**: Write a python program that opens the file **RNU6_269P.txt** and prints only its head
```
First line of the RNU6_269P.txt file:
>16 dna:chromosome chromosome:GRCh38:16:58377452:58378748:-1
```
* **Considerations**: 
  * Do not check for error when opening the file
  * Open the file using the module **Path**, imported from **pathlib**
  * The split method is very very useful. Try it and learn about it
  * The character used for separating the lines is '\n'

### Exercise 4

* **Filename**: Session-04/body.py
* **Description**: Write a program that opens the **U5.txt** file and prints on the console all the lines except the first one

```
Body of the U5.txt file:
ATAGACCAAACATGAGAGGCTGTGAATGGTATAATCTTCGCCGTTCGACAGGTAAGGTTA
TTTTTATTTTTTTTTTTTACTATTAAAGCGCTTTATAGATGTTTGTTCTTAATATTGCAG
ATTTAACTTTAACAACTCATTGTGCACGGAAACTCTCCGTTTGAGGACAGCAGTAGCAGG
...(the whole file is not shown in this output, but you should
    see it in your console) ...
TTCTTGATGCTGATGATTTAAGTCCAGTTTATGTTAACAGTGGCTAATGTTAACATAAAT
GGAACTTACATCATTAGCATTATCTCAGACCGTAATAAAATTTGAACAGTAATA
```

* **Considerations**
  * Do not check for error when opening the file

### Exercise 5

* **Filename:** Session-04/sequence.py
* **Description**: Write a program that opens the **ADA.txt** file and writes the **total number of bases** (Have in mind that you should remove the new line ('\n') characters
* **Considerations**: 
  * Remove the first line (the header) and all the '\n' characters. Then the total number of bases can be calculated using the len() function
  * The correct result is: 33912

## END of the session

The session is finished. Make sure, during this week, that everything in this list is checked!

* [ ] You have all the items of the session 3 checked!
* [ ] Your working repo contains the **Session-04 Folder** with the following files:
  * [ ] RNU6_269P.txt
  * [ ] FRAT1.txt
  * [ ] U5.txt
  * [ ] ADA.txt
  * [ ] FXN.txt
  * [ ] print_file.py
  * [ ] head.py 
  * [ ] body.py
  * [ ] sequence.py
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