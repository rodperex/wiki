![](https://github.com/davidrol6/2021-2022-PNE/raw/master/s9-Practice-2/Cover/Cover.png)

# Session 9: Practice 2

* **Time**: 2h
* **Date**: Wednesday, Mar-2th-2022
* **Goals**:
  * Practicing with the creation of clients
  * More Practicing on creating classes and objects
  * Learn how to run servers and clients on the same machine
  * Get familiar with the typical socket and network errors that will occur 

## Contents

* [Introduction](#introduction)  
* [Exercises](#exercises)  
  * [Exercise 1: ping()](#exercise-1-ping)
  * [Exercise 2: \_\_str\_\_()](#exercise-2-__str__)  
  * [Exercise 3: talk()](#exercise-3-talk)   
  * [Exercise 4: Sending a gene to the server](#exercise-5-sending-a-gene-to-the-server)  
  * [Exercise 5: Sending fragments of a gene to the server](#exercise-6-sending-fragments-of-a-gene-to-the-server)  
  * [Exercise 6: Sending fragments to two different servers](#exercise-7-sending-fragments-to-two-different-servers)  
* [End of the session](#end-of-the-session)
* [Author](#author)
* [Credits](#credits)
* [License](#license) 

## Introduction

The goal of this practice is to **gain experience** running **servers** and **clients** in the same computer. We will develop python programs (clients) that **send messages** and **sequences** to other servers

For making it easier to send the messages, we will develop the **class Client** located in the **Client0 module** (File Client0.py)

| Method           | Parameters                | Return | Description        |
|------------------|---------------------------|--------|--------------------|
| **\_\_init\_\_(ip, port)** | IP: String, Port: Integer | None   | Object Constructor. Stores the IP and Port values inside the object |
| **\_\_str\_\_()**    | none    | String | It returns the string: "Connection to SERVER at {ip}, PORT: {port}", where the {ip} and {port} are the server's ip and port respectivelly |
| **ping()**  | None | None | It prints the "OK" message on the console. It is just for testing the module |
| **talk(msg)**   | msg: String to send to the server | The response message from the server | It creates a new socket, connects to the server, sends the message, receive the response message from the server and closes the socket |
| **debug_talk(msg)** | msg: String to send to the server | The response message from the server | It works the same than the talk method, but it prints on the console both the message sent to the server and the response received, in different colors |

As always, this class will be created step by step in the exercises. The process is guided

## Exercises

We will implement the **Client Class** and develop some example programs to test it against the server

### Exercise 1: ping()

Let's start writing the **Client Class**. Create the file **P2/Client0.py**. Implement the \_\_init\_\_() and the **ping()** methods. Do not forget to **mark** the **P2 folder** as **Sources Root**

* **Filename:** P2/Client0.py
* **Description**: Class for sending messages easily to the server

Create the **Ex1.py** File for testing the Client Class. It just creates a client object, calls the ping() method and prints the configured IP and PORT.

* **Filename:** P2/Ex1.py
* **Description**: Preliminary test of the Client Class

The code should looks like this:

```python
from Client0 import Client

PRACTICE = 2
EXERCISE = 1

print(f"-----| Practice {PRACTICE}, Exercise {EXERCISE} |------")

# -- Parameters of the server to talk to
IP = "192.168.1.45"
PORT = 8080

# -- Create a client object
c = Client(IP, PORT)

# -- Test the ping method
c.ping()

# -- Print the IP and PORTs
print(f"IP: {c.ip}, {c.port}")
```

When **executed**, this is what you should see (but with different values of the IP and PORT):

```
-----| Practice 2, Exercise 1 |------
OK!
IP: 192.168.1.45, 8080

Process finished with exit code 0
```

### Exercise 2: \_\_str\_\_()

Implement the **\_\_str\_\_()** method. It should return the string:

```
"Connection to SERVER at {ip}, PORT: {port}"
```
Where the {ip} and {port} are the server's ip and port respectivelly

* **Filename:** P2/Ex2.py
* **Description**: Testing the Printing of a Client object

After the **client object** is created, you should print it:

```python3
#...
c = Client(IP, PORT)
print(c)
#...
```

This is what you should see on the **console**:

```
-----| Practice 2, Exercise 2 |------
Connection to SERVER at 192.168.1.45, PORT: 8080

Process finished with exit code 0
```
No real connection has been established yet. It just prints the IP and port of the Client object

### Exercise 3: talk()

Implement the **talk()** method in the **Client Class**. It should **send** a message to the server and return the **response**

This is the implementation. Make sure you understand the details

```python3
# -- Create the socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# establish the connection to the Server (IP, PORT)
s.connect((self.ip, self.port))

# Send data.
s.send(str.encode(msg))

# Receive data
response = s.recv(2048).decode("utf-8")

# Close the socket
s.close()

# Return the response
return response
```

* **Filename:** P2/Ex3.py
* **Description**: Testing the talk() method. The client should send a message to the server and print the response from the server

After the client object is created, this example will send a message a print the response message:

```python
...
# -- Send a message to the server
print("Sending a message to the server...")
response = c.talk("Testing!!!")
print(f"Response: {response}")
...
```

First you should **launch the Teacher's server** of **Session-08** (server.py). Then execute the EX3.py program. This is what you see on the **client console**:

```
-----| Practice 2, Exercise 3 |------
Connection to SERVER at 192.168.1.45, PORT: 8080
Sending a message to the server...
Response: 

Hello from the teacher's server



Process finished with exit code 0
```

And if you have a look a the Server's console, this is what you should see:

```
Waiting for connections at 192.168.1.45, 8080 
CONNECTION: 1. From the IP: ('192.168.1.45', 40652)
Message from client: Testing!!!
Waiting for connections at 192.168.1.45, 8080 
```

Make sure you **configure** the **server** with YOUR **IP** and that the client uses **the same IP and PORT** than the server


### Exercise 4: Sending a gene to the server

The **Client Class** is now ready. Let's use it for sending gene sequences to the server

* **Filename:** P2/Ex5.py
* **Description**: Write a python program that sends the U5, FRAT1 and ADA genes from the files to the Teacher's server (one at a time). It should initially send the message: "Sending the U5 Gene to the server..." and then the Gene itself
* **Considerations**: Use the class Seq that we have developed in order to load the genes into the program. Given an object of type Seq, s, you can obtain its sequence as a string just by calling str(s)

This is an example of what you should see on the **Client's console** when sending the information about the U5 Gene:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s9-Practice-2/exercise-04.png)

These are the **messages** received on the **server**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s9-Practice-2/exercise-05.png)

Congrats! You've been able to transfer your first gene from one computer to another over the internet!

### Exercise 6: Sending fragments of a gene to the server

* **Filename:** P2/Ex6.py
* **Description**: Write a python program that takes **5 fragments** of **10 bases** each from the **FRAT1 gene** and sends them to the server. Use the talk method. Print the fragments on the Client console for checking 

This is what you should see on the **client's console**:

```
-----| Practice 2, Exercise 6 |------
Connection to SERVER at 192.168.1.45, PORT: 8080
NULL Seq created
Gene FRAT1: ACCTCCTCTCCAGCAATGCCAACCCCAGTCCAGGCCCCCATCCGCCCAGGATCTCGATCAAAAAACA...
Fragment 1: ACCTCCTCTC
Fragment 2: CAGCAATGCC
Fragment 3: AACCCCAGTC
Fragment 4: CAGGCCCCCA
Fragment 5: TCCGCCCAGG

Process finished with exit code 0
```

Check on the **Server's console** that all the fragments has been received:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s9-Practice-2/exercise-06.png)

### Exercise 7: Sending fragments to two different servers

Copy the **server.py** program from folder Session-08 to the the** P2 folder** as files **server1.py** and **server2.py**. Change the Server's port so that **server1** is on port **8080** and **server2** on port **8081**

Execute the two servers

* **Filename:** P2/Ex7.py
* **Description**: Write a python program that takes **10 fragments** of **10 bases** each from the **FRAT1 gene** and sends them to two servers. The odd segments (1,3,5,7 and 9) should be sent to server 1, and the even segments (2,4,6,8 and 10) to server 2. The client should print on the console all the fragments

This is what you should see on the **Client's console**:

```
-----| Practice 2, Exercise 7 |------
Connection to SERVER at 192.168.1.45, PORT: 8080
Connection to SERVER at 192.168.1.45, PORT: 8081
NULL Seq created
Gene FRAT1: ACCTCCTCTCCAGCAATGCCAACCCCAGTCCAGGCCCCCATCCGCCCAGGATCTCGATCAAAAAACATTAATCTGT...
Fragment 1: ACCTCCTCTC
Fragment 2: CAGCAATGCC
Fragment 3: AACCCCAGTC
Fragment 4: CAGGCCCCCA
Fragment 5: TCCGCCCAGG
Fragment 6: ATCTCGATCA
Fragment 7: AAAAACATTA
Fragment 8: ATCTGTGGCC
Fragment 9: TTTCTTTGCC
Fragment 10: ATTTCCAACT

Process finished with exit code 0
```

**Server1's console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s9-Practice-2/exercise-07.png)

**Server2's console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s9-Practice-2/exercise-8.png)


## END of the session

The session is finished. Make sure, during this week, that everything in this list is checked!

* [ ] You have all the items of the session 8 checked!
* [ ] Your working repo contains the **P2 Folder** with the following files:
  * [ ] Ex1.py
  * [ ] Ex2.py
  * [ ] Ex3.py
  * [ ] Ex4.py
  * [ ] Ex5.py
  * [ ] Ex6.py
  * [ ] Ex7.py
  * [ ] server1.py
  * [ ] server2.py
  * [ ] Client0.py
* [ ] All the previous files have been pushed to your remote Github repo


# Credits

* [Alvaro del Castillo](https://github.com/acs). He designed and created the original content of this subject. Thanks a lot :-)
* [Juan González-Gómez](https://github.com/Obijuan) (Obijuan)

![](https://github.com/Obijuan/digital-electronics-with-open-FPGAs-tutorial/raw/master/wiki/portada/logos-urjc-gsyc-peloto-jderobot.png)

# License

![](https://github.com/Obijuan/digital-electronics-with-open-FPGAs-tutorial/raw/master/wiki/portada/attribution-share-alike-creative-commons-license.png)

# Links

* [Universidad Rey Juan Carlos de Madrid](https://www.urjc.es/)
* [Escuela Técnica Superior de Ingeniería de Telecomunicaciones (URJC)](https://www.urjc.es/universidad/facultades/escuela-tecnica-superior-de-ingenieria-de-las-telecomunicaciones/content/etsit-escuela-tecnica-superior-de-ingenieria-de-telecomunicacion)