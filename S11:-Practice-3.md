![](https://github.com/davidrol6/2020-2021-PNE/raw/master/s11-client-server-4/Cover/Cover.png)

# Session 11: Practice 3

* **Time**: 2h
* **Date**: Wednesday, March-09th-2022
* **Goals**:
  * Practicing on the programming of servers
  * Develop our own server for working with DNA sequences

## Contents

* [Introduction](#introduction)  
* [Localhost IP address](#localhost-ip-address)  
* [Exercises](#exercises)  
  * [Exercise 1: PING](#exercise-1-ping)
  * [Exercise 2: GET](#exercise-2-get)  
  * [Exercise 3: INFO](#exercise-3-info)  
  * [Exercise 4: COMP](#exercise-4-comp)  
  * [Exercise 5: REV](#exercise-5-rev)  
  * [Exercise 6: GENE](#exercise-6-gene)  
  * [Exercise 7: Test-client](#exercise-7-test-client)  
* [End of the session](#end-of-the-session)
* [Author](#author)
* [Credits](#credits)
* [License](#license) 

## Introduction

The goal of this practice is to develop our own **Seq** server for working with **DNA sequences**. We have been working with DNA sequences for many sessions, but always in our local computer. Now we will make these calculations available to other applications on Internet

The first step is to **define** the set of **rules** and **commands** that the **clients** need to follow in order to access the **services** given by our **server**: we should define the **protocol**

| Service name | Request message | Argument |Response message | Description |
|--------------|-----------------|---------|-----------------|-------------|
| **PING**         | "PING"          |  none   | "OK"            | Ping service for testing if the server is alive of not |
| **GET**          | "GET n"         | n: 0-4  | A sequence      | Get the sequence n. It could be any valid sequence of any length. There are only 5 sequences, numbered from 0 to 4 |
| **INFO**         | "INFO seq"      | seq: A sequence |  See format below | Get information about the given sequence: total length, number of bases and their percentages |
| **COMP**         | "COMP seq"     | seq: A sequene | The complement sequence | Calculate the complement of the given sequence |
| **REV**          | "REV seq"      | seq: A sequence | The reverse sequence | Calculate the reverse of the given sequence |
| **GENE**         | "GENE name"    | Gene name. See format below | The sequence of the gene |  Get the complete sequence of the given GENE |

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

The server will be programmed **step by step**, following the guides given in the **exercises**

## Localhost IP address

There is a special **IP** address: **127.0.0.1**, which is used to identify **your local machines**. When programming a server, instead of having to used the real IP, it is** easier to use this IP. Doing so, you do not have to change the code when running the server in a different computer

**We will always use the 127.0.0.1 address** in our servers

## Exercises

We will implement the **Seq Server** and develop some example clients for testing it. While developing the server, we will use the **printf** and **nc** linux commands for **sending messages** to the **server**. But you can also do it from your own client, if you like

The server will be stored in the **Seq-Server.py file** inside **folder P3**

you should use the **Seq1 module** developed in **practice 1**

### Exercise 1: PING

* **Filename:** P3/Seq-Server.py

Let's start by programming a server that implements the **PING command**. The client will send a message with the word **PING**. Then, the server should **parse** the request message. If the PING command is **detected**, it should generate the response message **"OK!\n"**. Also, it should **print on the console** the message "PING command!" in GREEN, and then the response message in white

For **testing the server** we use this command, executed from the **command line**:

```
printf "PING" | nc 127.0.0.1 8080
```

This is what we will see on the **linux console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s11-client-server-4/exercises-01.png)

And this is what we should get in the **Server's console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s11-client-server-4/exercises-02.png)


### Exercise 2: GET

* **Filename:** P3/Seq-Server.py

Modify the Seq server for implementing the **GET command**. The client sends a message with the word **GET** followed by a **number** between **0** and **4**. The server will return a **response message** with a **sequence** associated to that number. These sequences are for testing purposes, therefore you can use whatever sequences you want. They should be stored into a **list**. The server uses the number received in the GET command for accessing this list and **returning the sequence**

For **testing the server** we use this command, executed from the **command line**:

```
printf "GET 2" | nc 127.0.0.1 8080
```

In this example the client is asking for the sequence number 2

This is what is shown in the **Linux's console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s11-client-server-4/exercises-03.png)

And this is what we should get in the **Server's console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s11-client-server-4/exercises-04.png)

### Exercise 3: INFO

* **Filename:** P3/Seq-Server.py

Modify the Seq server for implementing the **INFO command**. The client sends a message with the word **INFO** followed by a sequence. The server will return a **response message** with information about that sequence. This information should be obtained using the **Seq Class**

For **testing the server** we use commands like this, executed from the **Linux's command line**:

```
printf "INFO AACCGTA" | nc 127.0.0.1 8080
```

This is what is shown in the **Linux's console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s11-client-server-4/exercises-05.png)

And this is what we should get in the **Server's console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s11-client-server-4/exercises-06.png)

### Exercise 4: COMP

* **Filename:** P3/Seq-Server.py

Modify the Seq server for implementing the **COMP command**. The client sends a message with the word **COMP** followed by a sequence. The server will return a **response message** with the complement of that sequence. It should be obtained using the **Seq Class**

For **testing the server** we use commands like this, executed from the **Linux's command line**:

```
printf "COMP AACCGTA" | nc 127.0.0.1 8080
```

This is what is shown in the **Linux's console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s11-client-server-4/exercises-07.png)

And this is what we should get in the **Server's console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s11-client-server-4/exercises-08.png)

### Exercise 5: REV

* **Filename:** P3/Seq-Server.py

Modify the Seq server for implementing the **REV command**. The client sends a message with the word **REV** followed by a sequence. The server will return a **response message** with the reverse of the given sequence. It should be obtained using the **Seq Class**

For **testing the server** we use commands like this, executed from the **Linux's command line**:

```
printf "REV AACCGTA" | nc 127.0.0.1 8080
```

This is what is shown in the **Linux's console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s11-client-server-4/exercises-09.png)

And this is what we should get in the **Server's console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s11-client-server-4/exercises-10.png)


### Exercise 6: GENE

* **Filename:** P3/Seq-Server.py

Modify the Seq server for implementing the **GENE command**. The client sends a message with the word **REV** followed by a **gene name**: U5, ADA, FRAT1, FXN or RNU6_269P. The server will return a **response message** with the complete sequence of that gene. It should be obtained using the **Seq Class** (and reading the gene from the corresponding file)

For **testing the server** we use commands like this, executed from the **Linux's command line**:

```
printf "GENE U5" | nc 127.0.0.1 8080
```

This is what is shown in the **Linux's console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s11-client-server-4/exercises-11.png)

And this is what we should get in the **Server's console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s11-client-server-4/exercises-12.png)

### Exercise 7: Test client

* **Filename:** P3/test-client.py

Finally let's create a client for **testing our server**. You should use the **Client class** from **practice 2**. Use the **talk** method

For the services **INFO**, **COMP** and **REV**, use the sequence obtained when calling the **GET 0 command**

The client should **write messages on the console** indicating the test it is performing and the response obtained from the server:

```
-----| Practice 3, Exercise 7 |------
Connection to SERVER at 127.0.0.1, PORT: 8080
* Testing PING...
OK!

* Testing GET...
GET 0: ACCTCCTCTCCAGCAATGCCAACCCCAGTCCAGGCCCCCATCCGCCCAGGATCTCGATCA
GET 1: AAAAACATTAATCTGTGGCCTTTCTTTGCCATTTCCAACTCTGCCACCTCCATCGAACGA
GET 2: CAAGGTCCCCTTCTTCCTTTCCATTCCCGTCAGCTTCATTTCCCTAATCTCCGTACAAAT
GET 3: CCCTAGCCTGACTCCCTTTCCTTTCCATCCTCACCAGACGCCCGCATGCCGGACCTCAAA
GET 4: AGCGCAAACGCTAAAAACCGGTTGAGTTGACGCACGGAGAGAAGGGGTGTGTGGGTGGGT

* Testing INFO...
Sequence: ACCTCCTCTCCAGCAATGCCAACCCCAGTCCAGGCCCCCATCCGCCCAGGATCTCGATCA
Total length: 60
A: 13 (21.7%)
C: 29 (48.3%)
G: 9 (15.0%)
T: 9 (15.0%)

* Testing COMP...
COMP ACCTCCTCTCCAGCAATGCCAACCCCAGTCCAGGCCCCCATCCGCCCAGGATCTCGATCA
TGGAGGAGAGGTCGTTACGGTTGGGGTCAGGTCCGGGGGTAGGCGGGTCCTAGAGCTAGT

* Testing REV...
REV ACCTCCTCTCCAGCAATGCCAACCCCAGTCCAGGCCCCCATCCGCCCAGGATCTCGATCA
ACTAGCTCTAGGACCCGCCTACCCCCGGACCTGACCCCAACCGTAACGACCTCTCCTCCA

* Testing GENE...
GENE U5
ATAGACCAAACATGAGAGGCTGTGAATGGTATAATCTTCGCCGTTCGACAGGTAAGGTTATTTTTATTTTTTTTTTTTACTATTAAAGCGCTTTATAGATGTTTGTTCTTAAT
[...]
CTAATGTTAACATAAATGGAACTTACATCATTAGCATTATCTCAGACCGTAATAAAATTTGAACAGTAATA

GENE ADA
AGATCGCGCCACTTCACTGCAGCCTCCGCGAAAGAGCGAAACTCCGTCTCAGTAAATAAATAAATAAATAAATAAATAAATAAATAAATAAATAAATAACCTGTACCCGCGTGTTATTTCCCTCCGTCCTTACCTCCTCCCGGCTCCTTCCCTTTCACCTGAGATAACCACTCTTCTCGTATCTATGCTCATCTTTCCCTTGCTTTACATTTTTTCCACCGATGCA
[...]
GAGTGGTTGGGGAA

GENE FRAT1
ACCTCCTCTCCAGCAATGCCAACCCCAGTCCAGGCCCCCATCCGCCCAGGATCTCGATCAAAAAACATTAATCTGTGGCCTTTCTTTGCCATTTCCAACTCTGCCACCTCCATCGAACGACAAGGTCCCCTTCTTCCTTTCCATTCCCGTCAGCTTCATTTCCCTAATCTCCGTACAAATCCCTAGCCTGACTCCCTTTCCTTTCCATCCTCACCAGACGCCCGCA
[...]
CTTTTCAGGGCTGG
GENE FXN
TCTCAAGCATATATAAGCTATGAAAGAAACGTTCACAATCTGTATTCCTTTGCAACATACTAAAGTAAAAATGTCTTTTAAGGTGTATTAACAACTTAATATTTACCATACACTTAGCAGGGTCTAGGGCTTGTCCCCCCACAAAAATACACTTTACATAGATGAACTCATTTTACCCTTAAAGTAACCCTAAGAAGTAGAAACTTTAATAAACTCCATTTTACAG
[...]
GGGTTGAGGAAGGC

GENE RNU6_269P
GAGCAGGAGCAGGTGCTGGCACAAGAGATAGAAGAGCTGTATTTGAAGCTGTCCTCACAGGGTTAACAAGAGTTCTGGACAGAAATATAGTTATAATTAAGCATTAGTCAGGCTGCAATTTGACTCATTTCCTTGTAGCCAGAATTCATGGAGCACTAGATGTTGACCATTTGTATCCCCATTGTTTCTACAGATGAAATTTCTGATGTTAGAATCATAAGGGTTT
[...]
CAATAAAGAAGGGCTGATCTCAAACAGCCTGAGCCTGGTGTCCTAATGGAATGA


Process finished with exit code 0
```


## END of the session

The session is finished. Make sure, during this week, that everything in this list is checked!

* [ ] You have all the items of the session 10 checked!
* [ ] Your working repo contains the **P3 Folder** with the following files:
  * [ ] Seq-server.py
  * [ ] test-client.py
* [ ] All the previous files have been pushed to your remote Github repo


# Credits

* [Juan González-Gómez](https://github.com/Obijuan) (Obijuan)
* [Alvaro del Castillo](https://github.com/acs). He designed and created the original content of this subject. Thanks a lot :-)

# License

![](https://github.com/Obijuan/digital-electronics-with-open-FPGAs-tutorial/raw/master/wiki/portada/attribution-share-alike-creative-commons-license.png)

# Links

* [Universidad Rey Juan Carlos de Madrid](https://www.urjc.es/)
* [Escuela Técnica Superior de Ingeniería de Telecomunicaciones (URJC)](https://www.urjc.es/universidad/facultades/escuela-tecnica-superior-de-ingenieria-de-las-telecomunicaciones/content/etsit-escuela-tecnica-superior-de-ingenieria-de-telecomunicacion)