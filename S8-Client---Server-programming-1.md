![](https://github.com/davidrol6/2021-2022-PNE/raw/master/s8-client-server-1/Cover/Cover.png)

# Session 8: Client-Server 1

* **Time**: 2h
* **Date**: Tuesday, Feb-22th-2020
* **Goals**:
  * Learn basic network concepts
  * Understand the IP addresses
  * Check the connectivity of Internet machines
  * Understand how a simple client works

## Contents

* [Introduction](#introduction)  
* [Introduction to the client-server model](#introduction-to-client-server-model)  
  * [IP address](#ip-address)  
  * [Ping: Testing the connectivity of a computer](#ping-testing-the-connectivity-of-a-computer)  
  * [URLS](#urls)  
  * [Ports](#ports)
* [Introduction to the programming of clients](#introduction-to-the-programming-of-clients)  
  * [Sockets](#sockets)  
  * [Teacher's server](#teachers-server)  
  * [Sending mesages to the server from the command line](#sending-messages-to-the-server-from-the-command-line)
  * [Client 1: Creating the socket and sending a message to the sever](#client-1-creating-the-socket-and-sending-a-message-to-the-server)  
  * [Client 2: Receiving and sending](#client-2-receiving-and-sending)  
* [Exercises](#exercises)
  * [Exercise 1](#exercise-1)  
  * [Exercise 2](#exercise-2)
  * [Exercise 3](#exercise-3)  
  * [Exercise 4](#exercise-4)  
* [End of the session](#end-of-the-session)
* [Author](#author)
* [Credits](#credits)
* [License](#license) 

## Introduction

Now that we **master** the tools (pycharm, github) and we have recalled how to **program in python**, it is time to learn how to create our own applications capable of **communicating** between them. There are many concepts that we should learn in order to **fully understand** how the communications work

In this session we will **introduce** all these concepts. **DON'T PANIC!** We will use them during all the course. Therefore, you will have time to learn them. What is important is that you **practice**. And do the exercises many times. The more you repeat the exercises, the more you will learn

## Introduction to client-server model

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s8-client-server-1/client-server-01.png)

The **model** we are using for communicating our apps is called **client-server**. In this model, there is one application, called the **server**, which purpose is to attend the **requests** of the **clients**. Usually there are many clients

The **client** is the app that **initiates the conversation**. It sends a messages **requesting** something to the server and the server response with another message, known as the **response message**

Let's identify a**ll the parts** that are needed for this communication to happen:

* The client need to identify the computer where the server is running. It needs its **"address"** (IP Address)
* This address is **not unique**. It depends on the network interface. You may have one, or two, and they may change. 
* Inside the computer there are **many apps running** at the same time. You have to specify to which app you want to access. It is called the **port**
* How can we send information to another app from our apps? We need and object to send the information. It is called a **socket**
* The **client** and the **server** can be in the **same computer** (we sill do it for developing our clients and server from our computer, without having to use two different computers. This is good, because you will be able to test your projects from your home)

### IP Address

* **IP address**: Numbers for identifying the network interfaces of a computer. IP examples: 216.58.201.174, 8.8.8.8

All the **computers** connected to internet has a special number that **identify** that interface. It is know as the **IP address**. Your mobile phone have an IP address. Your computer at the LAB has an **IP address**

For getting the **IP address** of your **Linux machine** in the **LAB** follow the next steps:

1. Open a terminal
2. Write the following command:
```ifconfig```
3. Locate your IP address
4. Write it down (You will need it for Exercise 1)

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s8-client-server-1/client-server-02.png)

### Ping: testing the connectivity of a computer

Once you know the **IP address** of one device, you can test if it is **connected to internet or not** using the **ping command**. This command sends a **small message** to that computer and tells you if an answer has been detected

Open a terminal and try to detect if the machine with the IP Address 8.8.8.8 is connected:

```
ping 8.8.8.8
```

You **stop** it by pressing **ctr-C**. The ping command also informs you about the time it takes for the Ping message to reach the machine and return to your computer. Notice that the values are not the same. Write down some of them in your notes (Exercise 2)

### URLS

IP address are difficult to remember for humans. We prefer to use characters and names. That's why we use the URLs. There are special servers in the internet, called **DNS** servers (Domain Name system). They give you the IP address of the machines associated to its name.

For example, when we connect to the www.urjc.es, that service is running in a machine which have an IP address. The DNS server give it to use. We can obtain the IPs with the ping command:

```
ping www.urjc.es
PING www.urjc.es (212.128.240.50) 56(84) bytes of data.
64 bytes from www.urjc.es (212.128.240.50): icmp_seq=1 ttl=253 time=2.14 ms
64 bytes from www.urjc.es (212.128.240.50): icmp_seq=2 ttl=253 time=2.15 ms
64 bytes from www.urjc.es (212.128.240.50): icmp_seq=3 ttl=253 time=2.12 ms
...
```

The ping command returns its IP address: 212.128.240.50. We can ping it directly:

```
$ ping 212.128.240.50
PING 212.128.240.50 (212.128.240.50) 56(84) bytes of data.
64 bytes from 212.128.240.50: icmp_seq=1 ttl=253 time=2.71 ms
64 bytes from 212.128.240.50: icmp_seq=2 ttl=253 time=2.16 ms
64 bytes from 212.128.240.50: icmp_seq=3 ttl=253 time=2.17 ms
64 bytes from 212.128.240.50: icmp_seq=4 ttl=253 time=2.62 ms
```

### Ports

As said before, there are **many apps** running inside a **computer**. We use the **IP** for identifying the **machine**, and the **Port** for the **application**

In order to communicate with a remote app, we need the pair of values (IP, port). And the remote app also need that information from our local app: (IP, port)
* There are some **standard ports** for some services. For example the **80 port** is reserved for **web servers**

## Introduction to the programming of clients

We will learn the **basic ideas** used for communicating a **client an a server** thought internet

### Sockets

For communicating with a program that is running in another computer we used the **socket concept**. The mechanism is quite similar to the one used for managing **files**. When we open a **file** we get a **file descriptor**. This is an **object** that allows us to read and write information from/to the file. Once we are finished, we **close** the file descriptor

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s8-client-server-1/client-server-03.png)

The idea behind the **sockets** is similar, but instead of opening a local file, it opens a "channel" for communicating with the remote program. The **socket is an object**, and as such, it has **properties** and **methods** for managing that channel

Each application that wants to communicate should do the following:

* **Create** the socket 
* **Connect** to an (IP, Port) remote pair
* **Write** data to the socket for sending to the remote app
* **Read** data from the socket for receiving the incoming messages
* **Close** the socket when finished

### The nc tool

For testing the communication between computers in Linux we have the **nc command** (netcat). It allow us to test our clients and servers. Let's do some experiments:

* In the Teacher's computer the following command is ran:

```
nc -l p 8000
```
It means that nc is working as a server, "listening" to the connection from other computers. It is located on port 8000

From any other machine in the lab you can **connect to server** with the command:

```
nc "Teacher's IP" 8000
```
You should substitute the "Teacher's IP" by the real teacher's IP

The nc command only allows the connection of 1 client to the server. So that once a connection has been established with a client, other clients cannot connect (they should wait until the former connection is finished)

* **Experiment**: Work in pairs. Establish connection between server and clients

### Teacher's server

For programming our **first client** we need a server for connecting to. This is the purpose of the **Teacher's server**. It will be running on the *Teacher's computers** for letting you test your clients. Once you learn, you can launch the Teacher's server in your own computer

* This is the **code** of the **Teacher's server**. Do not worry about this code. You do not have to understand it yet

```python
import socket

# Configure the Server's IP and PORT
PORT = 8081
IP = "192.168.1.36"
MAX_OPEN_REQUESTS = 5

# Counting the number of connections
number_con = 0

# create an INET, STREAMing socket
serversocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
try:
    serversocket.bind((IP, PORT))
    # become a server socket
    # MAX_OPEN_REQUESTS connect requests before refusing outside connections
    serversocket.listen(MAX_OPEN_REQUESTS)

    while True:
        # accept connections from outside
        print("Waiting for connections at {}, {} ".format(IP, PORT))
        (clientsocket, address) = serversocket.accept()

        # Another connection!e
        number_con += 1

        # Print the conection number
        print("CONNECTION: {}. From the IP: {}".format(number_con, address))

        # Read the message from the client, if any
        msg = clientsocket.recv(2048).decode("utf-8")
        print("Message from client: {}".format(msg))

        # Send the messag
        message = "Hello from the teacher's server"
        send_bytes = str.encode(message)
        # We must write bytes, not a string
        clientsocket.send(send_bytes)
        clientsocket.close()

except socket.error:
    print("Problems using port {}. Do you have permission?".format(PORT))

except KeyboardInterrupt:
    print("Server stopped by the user")
    serversocket.close()
```

It will wait for the **clients to connect**. Once a client is connected, It will print the message given by the client (if any) and response with a greeting message

### Sending messages to the server from the command line

Once the **Teacher's server is running**, we will use the **commands printf** and **nc** for sending messages to it. Execute the following command from your LAB computer. Change the IP and Port according to the Teacher's specification:

```
printf "Testing!!! :-)" | nc 192.168.124.179 8080
```

You will see the **server's response** printed on your console:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s8-client-server-1/client-server-04.png)

In the **Server's console**, you will see **your message**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s8-client-server-1/client-server-05.png)

### Client-1: Creating the socket and sending a message to the server

Let's learn how to **send messages** from our **python programs**. We will **assume** that there is already a **server running** and we will connect to it and send them messages

For doing that, we need **sockets**. For creating a socket we will use the **system module socket**

Create the **client.py** file with this code (inside the Session-08 folder)

```python3
import socket

# SERVER IP, PORT
# Write here the correct parameter for connecting to the
# Teacher's server
PORT = 8080
IP = "192.168.124.179"


# First, create the socket
# We will always use this parameters: AF_INET y SOCK_STREAM
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# establish the connection to the Server (IP, PORT)
s.connect((IP, PORT))

# Send data. No strings can be send, only bytes
# It necesary to encode the string into bytes
s.send(str.encode("HELLO FROM THE CLIENT!!!"))

# Closing the socket
s.close()
```

When the **socket() constructor** is executed, a **new object** is stored in the **s variable**. It is our socket (it is an object). As this is an object, it has certain method that we will use. The **connect()** method is used for configuring the **IP** and **PORT** of the **remote application**. The method **send()** is used for **sending messages** to the remote app. And finally, the close() method is for closing the connection

**Notice** that the what is send to the app are **raw bytes**. That is the reason why we should **encode** our **text messages:** we need to convert the strings into raw bytes

### Client-2: Receiving and sending

This is a similar example, but waiting for the **server's response**, and printing it on the **console**

```python3
import socket

# SERVER IP, PORT
PORT = 8080
IP = "192.168.124.179"

# First, create the socket
# We will always use this parameters: AF_INET y SOCK_STREAM
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# establish the connection to the Server (IP, PORT)
s.connect((IP, PORT))

# Send data. No strings can be send, only bytes
# It necesary to encode the string into bytes
s.send(str.encode("HELLO FROM THE CLIENT!!!"))

# Receive data from the server
msg = s.recv(2048)
print("MESSAGE FROM THE SERVER:\n")
print(msg.decode("utf-8"))

# Closing the socket
s.close()
```

## Exercises

All the exercises and experiments performed during this session should be stored in the **Session-08 folder**

### Exercise 1

* **Filename**: Session-08/IPs.py

Let's play a little bit with the **IP address**. Try to find the IP address of your **mobile phone**. If you are connected to the URJC wifi you should have an IP

How to find this information depends on your mobile phone. Usually on **Android phones** you will find it in **Settings/system/About the phone/state/IP address**

Get the **IP address** of your **computer** at the LAB

Open a new file (IPs.txt) and complete the following information:

|Machine      | Interface   | Date        |  Place             |   IP            |
|-------------|-------------|-------------|--------------------|-----------------|
|mobile       | Wifi        |             |                    |                 |
|Lab computer | Wire        |             |                    |                 |
|.....        | .....       | .....       | ..........         | ..............  |

The first column is for your computer in the lab and/or your mobile. The second is the type of interface. Wifi or wire. The third is the date. The fourth is the place: home/Alcorcon Lab and the last one is the IP address.

You should get the IP of your phone when you reach **home**. And also, take note of your mobile IP when you reach the LAB tomorrow. Write down all the IPs in the table

### Exercise 2

* **Filename**: Session-08/Ex2.txt

Create a new text file: **EX2.txt**. Fill in the time given by the **ping** command when executed from your LAB computer to different machines:

| Destination IP |  Name (if known) | Time  |
|----------------|------------------|-------|
| 192.168.124.179  | Self            | 0.020 ms, 0.017 ms... |
|  212.128.255.129 | f-l3208-pc01    |  |
| 8.8.8.8          | Google          |   |
| 10.1.128.39      | Mobile          | |
|                  | www.urjc.es     |  |
|                  | github.com      |  |
|                  | wikipedia.org   |  |
|                  | newdomain.com.au |  |


The first should be your own computer (ping to your IP address). The second is an IP address of a machine located in Fuenlabrada. The third is the google dns machine and the forth you mobile IP address. Complete the table for the other UTLS

### Exercise 3

* **Filename**: Session-08/Ex3.py

Write a python program for implementing a **chat application**. Your client will ask the user to **enter a message**. Then, it will create a socket, connect to the **Teacher's server**, send the message, close the socket and repeat the operation:

```python3
import socket

# SERVER IP, PORT
PORT = 8080
IP = "192.168.124.179"

while True:
  # -- Ask the user for the message

  # -- Create the socket 

  # -- Establish the connection to the Server

  # -- Send the user message

  # -- Close the socket
```

### Exercise 4

* **Filename**: Session-08/server.py

In this exercise you should learn to launch the teacher's server from your computer. Write the server in the file server.py. **Configure** the **IP address**: it should be the IP address of your computer. **Run** the server

Ask any of your mates to **connect** to the server, using the client developed in exercise 3. Once it is working, close the server, and connect your client to your mate's server, so that both of you have tested the server

### Exercise 5

Now run the server again. Configure your client of exercise 3 to connect to the your server, so that you are running both the client and the server. Check that it is working. Get familiar with it, because we will use it a lot :-)

Congrats! Your are now ready to develop your own clients and server in your own computer!

## END of the session

The session is finished. Make sure, during this week, that everything in this list is checked!

* [ ] You have all the items of the session 7 checked!
* [ ] Your working repo contains the **Session-08 Folder** with the following files:
  * [ ] IPs.txt
  * [ ] Ex2.txt
  * [ ] Ex3.py
  * [ ] server.py
* [ ] All the previous files have been pushed to your remote Github repo

# Credits

* [Juan González-Gómez](https://github.com/Obijuan) (Obijuan)
* [Alvaro del Castillo](https://github.com/acs). He designed and created the original content of this subject. Thanks a lot :-)

# License

![](https://github.com/Obijuan/digital-electronics-with-open-FPGAs-tutorial/raw/master/wiki/portada/attribution-share-alike-creative-commons-license.png)

# Links

* [Universidad Rey Juan Carlos de Madrid](https://www.urjc.es/)
* [Escuela Técnica Superior de Ingeniería de Telecomunicaciones (URJC)](https://www.urjc.es/universidad/facultades/escuela-tecnica-superior-de-ingenieria-de-las-telecomunicaciones/content/etsit-escuela-tecnica-superior-de-ingenieria-de-telecomunicacion)