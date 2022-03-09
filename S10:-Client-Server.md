![](https://github.com/davidrol6/2021-2022-PNE/raw/master/s10-client-server-3/Cover/Cover2.png)

# Session 10: Client-Server

* **Time**: 2h
* **Date**: Tuesday, March-07th-2022
* **Goals**:
  * Learn how servers work
  * Program our first server

## Contents

* [Introduction](#introduction)  
* [Introduction to the programming of servers](#introduction-to-the-programming-of-servers)  
  * [Connection of many clients to the server](#connection-of-many-clients-to-the-server)
* [Introduction to the programming of servers](#introduction-to-the-programming-of-servers)  
  * [Setting up a server](#setting-up-a-server)  
  * [Happy server :-)](#happy-server--)  
  * [Initial configuration](#initial-configuration)  
  * [Waiting for connections](#waiting-for-connections)  
  * [Error: Address already in use](#error-address-already-in-use)  
  * [Reading data from the client](#reading-data-from-the-client)  
  * [Sending the response message](#sending-the-response-message)  
  * [Server's main loop](#servers-main-loop)  
  * [Manually stopping the server](#manually-stopping-the-server)  
* [Exercises](#exercises)
  * [Exercise 1](#exercise-1)  
  * [Exercise 2](#exercise-2)
  * [Exercise 3](#exercise-3)  
  * [Exercise 4](#exercise-4)  
* [End of the session](#end-of-the-session)
* [Credits](#credits)
* [License](#license) 

## Introduction

We already known the **basic communication mechanism** between two applications located in different computers. Each of them is **identified** with the **IP** and **PORT**. We use the **abstraction of sockets**. These are **objects** that has some **methods** for allowing the communication. The bytes **written** to one socket are received on the other side, and vice-versa

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s10-client-server-3/intro-01.png)

The way the twos apps behaves in the communication depends on the **model used**. In the **client-model**, the **initiative** of the communications relies on the **client**, while the **server** is just **waiting** for clients to connect

We saw in the previous sessions that the **client** uses only **one socket** to connect to a server

In the case of Servers they need **two sockets**: One for **listenning** to the connections from the clients, and the other for **transferring** the data from/to the client, once the **connection** has been **established**

The **communication process** between the **client** and server is as follows:

* **Step 1**: Initial state
  * The client has created a socket
  * The sever has created a socket and configured it in **listening mode**

* **Step 2**: The client start the connection (calling the *connect()* method in the socket)

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s10-client-server-3/intro-02.png)

* **Step 3**: The server creates **another socket** for communicating with the **client**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s10-client-server-3/intro-03.png)

* **Step 4**: The client and the server communicates normally, using the "blue" sockets. The "red" socket continues listening for new connection from other clients

### Connection of many clients to the server

What happens if **another client** tries to **connect** to the server when it is already connected to the previous client?

The **clients** connect to the first socket, the one that is in **listening mode**. Typically, whenever there is a new connection, the server creates a **copy of itself** (we call it a fork, or a thread) that attends the client using another socket

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s10-client-server-3/intro-04.png)

Depending on the **capacity of the server**, it could attend more or less clients. If the server is **busy** and it cannot attend more clients, the **listening socket** will put the requests in a **queue**. They will be attended when the server finished with the previous clients 

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s10-client-server-3/intro-05.png)

In the **servers** we are developing in **this subject**, we will only **attend one client at a time**, for simplicity

## Introduction to the programming of servers

We will learn the **basic ideas** used for programming a simple server

### Setting up a server

The **steps** that should be followed to setup a **working server** are:

* **Step 1**: Create the socket (Method socket())
* **Step 2**: Configure the socket: bind it to the remote IP and PORT (Method bind() 
* **Step 3**: Configure the socket in listening mode (Method listen())
* **Main loop**:
  * **Step 5**: Wait for a client to connect (method accept())
  * **Step 6**: When a client connects, the socket library creates a new socket for communicating with the client
  * **Step 7**: Read the client messages. What does the client want? (metho rcv)
  * **Step 8**: Process the request and send a response message (method send)

### Happy server :-)

Let's write our **first server**. We will call it **happy server**, as it is always sending us a message no matter what is the request from the client

Create the **Session-10** folder in your working repo. Our server will be programed in the **happy-server.py** file

We will write our server from **scratch**. Make sure you understand all the parts

### Initial configuration

This is the **version 1**. We create the **socket**, **bind** it to its **IP and PORT** parameters and configure it for being a **listening** socket. Finally we **close** the socket

```python3
import socket

# Configure the Server's IP and PORT
PORT = 8080
IP = "192.168.1.45"

# -- Step 1: create the socket
ls = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# -- Step 2: Bind the socket to server's IP and PORT
ls.bind((IP, PORT))

# -- Step 3: Configure the socket for listening
ls.listen()

print("The server is configured!")

# -- Close the socket
ls.close()
```

This server will be **running in your computer**. Makes sure that your **IP address is correct**. 

**Run it**. You will see the message we have printed and nothing more. It just finished ok

```
The server is configured!

Process finished with exit code 0
```
If you have not configure the right IP you will see a message in red like this:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s10-client-server-3/error-01.png)

### Waiting for connections

Once the server is correctly configured, we **wait for connections** from the client. It is done by calling the **accept() method** on the **listening socket** (ls)

```python3
import socket

# Configure the Server's IP and PORT
PORT = 8080
IP = "192.168.124.179"

# -- Step 1: create the socket
ls = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# -- Step 2: Bind the socket to server's IP and PORT
ls.bind((IP, PORT))

# -- Step 3: Configure the socket for listening
ls.listen()

print("The server is configured!")

# -- Waits for a client to connect
print("Waiting for Clients to connect")
ls.accept()

print("A client has connected to the server!")

# -- Close the socket
ls.close()
```

**Run it**. You will see this message on the console:

```
The server is configured!
Waiting for Clients to connect
```

The program no longer finish (like before). Now it **waits** for the clients to connect. You can **test** it with some of the clients you did in **Practice 2**, or you can directly use the **nc command** from the **linux console**:

```
$ printf "Test" | nc 192.168.124.179 8080
```

In the **server's console** you will see **new messages** and then the **server is done**:

```
The server is configured!
Waiting for Clients to connect
A client has connected to the server!

Process finished with exit code 0
```

Let's **debug** it. We place a **breakpoint** after calling the **accept()** method and then we click on the little green bug

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s10-client-server-3/happy-server-02.png)

The server starts **running** 

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s10-client-server-3/happy-server-03.png)

Only when a **client is connected**, the program reaches the breakpoint and **stops**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s10-client-server-3/happy-server-04.png)

From there, we can execute the program **step by step** until it is finished. In this **animation** you can see this process

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s10-client-server-3/happy-server-01.gif)

### Error: Address already in use

Sometimes, after executing the server and running it again you will see a **red error message** on the console that says:

```
OSError: [Errno 98] Address already in use
```
![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s10-client-server-3/happy-server-05.png)

This is because the port **has not still been freed** by the operating system. Soemetimes it takes one minute or two to free it. One solution is just to **change the server port to another**. For example 8081. Then running it again

**Another solution** is to configure the socket so that the **addresses can be reused**. You have to add this line below the socket creations:

```python3
# -- Step 1: create the socket
ls = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# -- Optional: This is for avoiding the problem of Port already in use
ls.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
``` 

### Reading data from the client

The **accept() method** returns a pair of values: the **new socket** used for **communicating with the client** and the **client's ip** and **port** values

We **store** the socket in the **cs object** (client-socket). We use the **rcv() method** of the cs socket for 
**receiving** the **client's message** and printing it on the **console**

```python3
# ....
# ....
# -- Waits for a client to connect
print("Waiting for Clients to connect")
(cs, client_ip_port) = ls.accept()

print("A client has connected to the server!")

# -- Read the message from the client
# -- The received message is in raw bytes
msg_raw = cs.recv(2048)

# -- We decode it for converting it
# -- into a human-redeable string
msg = msg_raw.decode()

# -- Print the received message
print(f"Received Message: {msg}")

# -- Close the socket
ls.close()
```

We **run** the server and **send a message** from a client, for example with the nc command:

```
$ printf "Test" | nc 192.168.124.179 8080
```

We will see the message on the **Server's console**:

```
The server is configured!
Waiting for Clients to connect
A client has connected to the server!
Message received: Test

Process finished with exit code 0
```

### Sending the response message

For **sending information** from the server to the client we use the **send() method**. As this is a happy server, we will send always the same **constant message**:

```python3
# ....
# ....
# -- Send a response message to the client
response = "HELLO. I am the Happy Server :-)\n"

# -- The message has to be encoded into bytes
cs.send(response.encode())

# -- Close the client socket
cs.close()
```
if we **run the server** and send a message with the **nc command**, we will see the **server's response**:

```
$ printf "Test" | nc 192.168.124.179 8080
HELLO. I am the Happy Server :-)
$
```

### Server's main loop

Usually the servers run in a **never-ending loop**. After sending the response message, we **close the cs socket** and **repeat again**, from the accept() method, for attending the next client

The whole server program is:

```python3
import socket

# -- Step 1: create the socket
ls = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# -- Optional: This is for avoiding the problem of Port already in use
ls.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)

# Configure the Server's IP and PORT
PORT = 8080
IP = "192.168.124.179"

# -- Step 1: create the socket
ls = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# -- Optional: This is for avoiding the problem of Port already in use
ls.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)

# -- Step 2: Bind the socket to server's IP and PORT
ls.bind((IP, PORT))

# -- Step 3: Configure the socket for listening
ls.listen()

print("The server is configured!")

while True:
    # -- Waits for a client to connect
    print("Waiting for Clients to connect")
    (cs, client_ip_port) = ls.accept()

    print("A client has connected to the server!")

    # -- Read the message from the client
    # -- The received message is in raw bytes
    msg_raw = cs.recv(2048)

    # -- We decode it for converting it
    # -- into a human-redeable string
    msg = msg_raw.decode()

    # -- Print the received message
    print(f"Message received: {msg}")

    # -- Send a response message to the client
    response = "HELLO. I am the Happy Server :-)\n"

    # -- The message has to be encoded into bytes
    cs.send(response.encode())

    # -- Close the data socket
    cs.close()
```

### Manually stopping the server

When we **stop the server** by pressing on the **red stop button**, there appear the following **error message**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s10-client-server-3/happy-server-06.png)

For making it finished better, we will add a **try-except-else** block in the main **server's loop**:

```python3
while True:
    # -- Waits for a client to connect
    print("Waiting for Clients to connect")

    try:
        (cs, client_ip_port) = ls.accept()

    # -- Server stopped manually
    except KeyboardInterrupt:
        print("Server stopped by the user")

        # -- Close the listenning socket
        ls.close()

        # -- Exit!
        exit()

    # -- Execute this part if there are no errors
    else:

        print("A client has connected to the server!")

        # -- Read the message from the client
        # -- The received message is in raw bytes
        msg_raw = cs.recv(2048)

        # -- We decode it for converting it
        # -- into a human-redeable string
        msg = msg_raw.decode()

        # -- Print the received message
        print(f"Message received: {msg}")

        # -- Send a response message to the client
        response = "HELLO. I am the Happy Server :-)\n"

        # -- The message has to be encoded into bytes
        cs.send(response.encode())

        # -- Close the data socket
        cs.close()
```

Now, when the **server is stopped** we will see this message in white:

```
Waiting for Clients to connect
Server stopped by the user

Process finished with exit code 0
```
OK! Now we understand how the servers work! **It is time for some practicing!!!**

## Exercises

All the exercises and experiments performed during this session should be stored in the **Session-10 folder**

### Exercise 1

Convert the happy server into an **echo server**: It is a server that just response with the **same message** sent by the client. It should start the response message with the **string "ECHO: "** and then add the **client's message**

* **Filename**: Session-10/echo-server1.py
* **Description**: Once the server is running, it will print the client's messages in the **server's console** in green color. If we send 3 messages using the nc command, this is what we will on the **linux's console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s10-client-server-3/Ex-01.png)

And this is what we should see on the **Server's console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s10-client-server-3/Ex-01-2.png)

### Exercise 2

Modify the server from exercise 1 so that **it counts the number of connections** from the clients. It should also print the client's Ip and ports

* **Filename**: Session-10/echo-server2.py
* **Description**: This is an example of the output that you should see on the Server's console. In this example 4 clients have been connected to the server

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s10-client-server-3/Ex-02-1.png)

### Exercise 3

Modify the server of exercise 2 so that it **stores the client's tuples (IP, PORT)** in a **list**. After **5 clients** has connected, it will print the information of all the clients in the console and finish

* **Filename**: Session-10/echo-server3.py
* **Description**: This is an example of the output

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s10-client-server-3/Ex-03-1.png)

### Exercise 4

**Write a client** for **testing** the server of the exercise 3.It should connect **5 times** to the server, sending the message: **message i**, where i change from 0 to 4. You must use the **Client0 module** developed in the **Practice 2**. Use the method talk() for sending the messages to the server

* **Filename**: Session-10/client-test.py
* **Description**: This is an example of the output in the **client's console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s10-client-server-3/Ex-04-1.png)

And this is what is shown in the **server's console**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s10-client-server-3/Ex-04-2.png)

## END of the session

The session is finished. Make sure, during this week, that everything in this list is checked!

* [ ] You have all the items of the session 9 checked!
* [ ] Your working repo contains the **Session-10 Folder** with the following files:
  * [ ] happy-server.py
  * [ ] echo-server1.py
  * [ ] echo-server2.py
  * [ ] echo-server3.py
  * [ ] client-test.py
* [ ] All the previous files have been pushed to your remote Github repo

# Credits

* [Juan González-Gómez](https://github.com/Obijuan) (Obijuan)
* [Alvaro del Castillo](https://github.com/acs). He designed and created the original content of this subject. Thanks a lot :-)

# License

![](https://github.com/Obijuan/digital-electronics-with-open-FPGAs-tutorial/raw/master/wiki/portada/attribution-share-alike-creative-commons-license.png)

# Links

* [Universidad Rey Juan Carlos de Madrid](https://www.urjc.es/)
* [Escuela Técnica Superior de Ingeniería de Telecomunicaciones (URJC)](https://www.urjc.es/universidad/facultades/escuela-tecnica-superior-de-ingenieria-de-las-telecomunicaciones/content/etsit-escuela-tecnica-superior-de-ingenieria-de-telecomunicacion)