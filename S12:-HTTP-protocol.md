![](https://github.com/davidrol6/2020-2021-PNE/blob/master/s12-http-1/Cover/Cover.png)

# Session 12: HTTP protocol

* **Time**: 2h
* **Date**: Tuesday, April-13th-2021
* **Goals**:
  * Learn about the HTTP protocol
  * Write our first web server using sockets

## Contents

* [Introduction to the HTTP protocol](#introduction-to-the-http-protocol)
  * [Requesting a web page](#requesting-a-web-page)
    * [Step 1: Connection establishment](#step-1-connection-establishment)
    * [Step 2: The client sends a request message for a web page](#step-2-the-client-sends-a-request-message-for-a-web-page)
    * [Step 3: The server reads the page from the disk](#step-3-the-server-reads-the-page-from-the-disk)
    * [Step 4: the server sends a response message](#step-4-the-server-sends-a-response-message)
    * [Step 5: The browser renders the page on the screen](#step-5-the-browser-renders-the-page-on-the-screen)
  * [HTTP messages](#http-messages)
    * [Request messages](#request-messages)
    * [Response messages](#response-messages)
* [Creating our first http server](#creating-our-first-http-server)
  * [Starting point: The echo server](#starting-point-the-echo-server)
  * [Reading the browser's request message](#reading-the-browsers-request-message)
  * [Sending a simple response message](#sending-a-simple-response-message)
  * [curl: Watching the http messages](#curl-watching-the-http-messages)
  * [Response with HTML contents](#response-with-html-contents)
* [HTML](#html)
* [Exercises](#exercises)
  * [Exercise 1](#exercise-1)  
  * [Exercise 2](#exercise-2)
  * [Exercise 3](#exercise-3)  
  * [Exercise 4](#exercise-4)  
* [End of the session](#end-of-the-session)
* [Author](#author)
* [Credits](#credits)
* [License](#license) 

# Introduction to the HTTP protocol

* [HTTP protocol](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) is the language spoken between a **browser** (client) and a **web server**
* This is our **general scenario**, in which there is a communication between one client and one server. As we already know, there are two kinds of sockets: one just for listening to new connection on the server (Red dot), and others for interchanging data between the client and the server (blue dots)

![](https://github.com/myTeachingURJC/2018-19-PNE/raw/master/wiki/s11-http/src/client-server-sockets.svg?sanitize=true)

## Test
* [Test1](https://fpgawars.github.io/LOVE-FPGA/Web-components/Led/led.html)  
* [Test2](https://fpgawars.github.io/LOVE-FPGA/Web-components/Eye/eye.html)  

## Requesting a web page

Let's understand what is happening when a **browser** connects to a **web server** for viewing a **web page**. This is the **initial scenario**:

![](https://github.com/myTeachingURJC/2018-19-PNE/raw/master/wiki/s11-http/src/client-server-sockets-web-0.svg?sanitize=true)

The client is the **browser** running in our device (computer, mobile, tablet...). the server is running in another computer on the internet. It is waiting for the clients to connect

### Step 1: Connection establishment

When we write an **URL** in the browser, we are requesting a web page from the server. The client creates a **socket** and **establish a connection** with the server. The server creates a new **socket** (clientsocket) for **interchanging data** with the **client** (in both directions). The original sockets continues listening for new connections

![](https://github.com/myTeachingURJC/2018-19-PNE/raw/master/wiki/s11-http/src/client-server-sockets-web-1.svg?sanitize=true)

Now the client and server can **communicate** by means of the "blue" sockets. When they **write** to the sockets, the data is **sent**. When they **read** from them, the data is **received**. There is a **bidirectional communication** channel established

### Step 2: The client sends a request message for a web page

The client takes the initiative (always) and sends a **request message** for obtaining the **web page** that the user wants to see

![](https://github.com/myTeachingURJC/2018-19-PNE/raw/master/wiki/s11-http/src/client-server-sockets-web-2.svg?sanitize=true)

### Step 3: The server reads the page from the disk

The server receives the **request message** and reads the **html file** from the **hard disk**

![](https://github.com/myTeachingURJC/2018-19-PNE/raw/master/wiki/s11-http/src/client-server-sockets-web-3.svg?sanitize=true)

### Step 4: The server sends a response message

The server builds a **response message**, composed of different fields. The HTML contents are located in the end of the message

![](https://github.com/myTeachingURJC/2018-19-PNE/raw/master/wiki/s11-http/src/client-server-sockets-web-4.svg?sanitize=true)

### Step 5: The browser renders the page on the screen

The client receive the **html content** and shows it on the screen

![](https://github.com/myTeachingURJC/2018-19-PNE/raw/master/wiki/s11-http/src/client-server-sockets-web-5.svg?sanitize=true)

## HTTP messages

There are two types of messages in HTTP: **Request** and **response**. They both have the **same format**: They consist of **Lines in plain text** (strings) separated by the **special character** '\n'

The lines are divided into two parts: the **heather** and the **body**. There is a **blank line** for separating both elements

### Request messages

This is the **format** of the Request messages

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s12-http-1/src/http-request-message.svg?sanitize=true)

The **request line** is the most important part. Here is where the client tells the server the service it needs. Consist of **three parts** separated by one space:

* **Method**: Command name. There are three: GET, POST, HEAD
  * **GET**: Request an **object** to the server. The client wants the server to send it an object. The object id is given in the Path argument
  * **POST**: The client wants to send data to the server. They are placed in the message body
  * **HEAD**: Similar to GET, but only the object's headers are requested. It is used by the client to know if the object has been modified without having to transfer the whole object
* **Path**: It is the name of the object that the client wants to get from the server, or the object which will receive the data the client is sending
* **Version**: the HTTP version used. The syntax is like this: **HTTP/x.y**, where x and y are integer numbers

This is an **Example** of a request line:

```
GET /directory/other/file.html HTTP/1.0
```

And this is an **example** of a real message:

![](https://github.com/myTeachingURJC/2018-19-PNE/raw/master/wiki/s11-http/src/http-request-message-example.svg?sanitize=true)

In this example, there is no body (it is empty)

### Response messages

This is the **format** of the response message. It is the same than for the request message

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s12-http-1/src/http-response-message.svg?sanitize=true)

The **status line** consist of **three parts** separated by spaces

* **Version**: HTTP version. The syntax is: HTTP/x.y
* **Status code**: A number that indicates what happened with the request
  * 200 --> OK
  * 404 --> Not Found
  * 304 --> Not modified
* **Status**: Status information, in text format (readable)

**Example** of a status line:

```
HTTP/1.0 200 OK
```

This is an **example** of a response message:

![](https://github.com/myTeachingURJC/2018-19-PNE/raw/master/wiki/s11-http/src/http-request-response-example.svg?sanitize=true)

# Creating our first HTTP server

Let's create our **first HTTP server**, step by step, learning while doing

## Starting point: The echo server

 We start from a **simple server**, from the previous week, that just **receives the request message** and print it on the console: The **echo server**. It does no generates a response yet

**Create** the **Session 12 folder** and the **new** python file **echo-server.py**. Copy & paste the following code

```python3
import socket
import termcolor


# -- Server network parameters
IP = "127.0.0.1"
PORT = 8080


def process_client(s):
    # -- Receive the request message
    req_raw = s.recv(2000)
    req = req_raw.decode()

    print("Message FROM CLIENT: ")
    termcolor.cprint(req, "green")


# -------------- MAIN PROGRAM
# ------ Configure the server
# -- Listening socket
ls = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# -- Optional: This is for avoiding the problem of Port already in use
ls.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)

# -- Setup up the socket's IP and PORT
ls.bind((IP, PORT))

# -- Become a listening socket
ls.listen()

print("SEQ Server configured!")

# --- MAIN LOOP
while True:
    print("Waiting for clients....")
    try:
        (cs, client_ip_port) = ls.accept()
    except KeyboardInterrupt:
        print("Server Stopped!")
        ls.close()
        exit()
    else:

        # Service the client
        process_client(cs)

        # -- Close the socket
        cs.close()

```

First, let's check that our **server** is **working fine**. From the **linux console** we send a message to the server using the **printf** and **nc commands**:

```
printf "Hello!" | nc 127.0.0.1 8080
```

We should see this message on the **server's console**, in **green** color

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s12-http-1/Cover/echo-server-01.png)

## Reading the browser's request message

**Internet browsers** (like Firefox or Chrome) speak the **HTTP protocol**. It means that they send a request message with the format we have already seen. Let's check it

Open a **new tab** in your **browser** and type it:

```
http://127.0.0.1:8080/
```

This is the **URL** of the **main page** of our server:

* **"http://"**: It means that we want to use the HTTP protocol
* **127.0.0.1**: Server's IP (in this case is the server in our local machine)
* **:8080**: The Server's Port. It is separated by the caracter **:** from the IP
* **/**: This slash indicate that we want to access the server's **main page**

In the **browser** we will see something like this:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s12-http-1/echo-server-02.png)

As our server does NOT speak HTTP yet, the **browser** could **not** establish the connection with the web server. An error message is shown

But... our server **has received** the **request messages** from the **browser**. If we have a look at the **server's console**, we will see something like this:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s12-http-1/echo-server-03.png)

**Notice** that there appear **many** request messages (all the same). This is because we have not generate a response to the client's request messages. The browser **re-sends** the request messages many times, until there is a **timeout** and the browser writes an **error message** 

This is the **request message** received from the browser:

```
GET / HTTP/1.1
Host: 127.0.0.1:8080
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:73.0) Gecko/20100101 Firefox/73.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-GB,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: keep-alive
Upgrade-Insecure-Requests: 1
```

Have a look at the first line:

```
GET / HTTP/1.1
```

The browser is asking our server for the **/** object. It means the **main page. The HTTP version used is 1.1

## Sending a simple response message

Let's modify our server for generating a **valid response message** in **HTTP format**. Use the file **Session-12/webserver1.py**

Our **response message** should have the following format:

* **Status line**. We will inform the browser that everything went well. The typical status line is like this:

```
HTTP/1.1 200 OK\n
``` 
* The **header** should contain at least two elements:
  * **Content-Type:** This is for indicating the type of content return by the server. It will be typically **text/html** (but can also be image/png in the case of sending back an image in png format)
  * **Content-Length:** It indicates the **total length** of the information sent in the **body** of the response
* The **body** with the **contents** we are sending to the browser

In our server we will generate a **simple response** in which body we will store the string: "Hello from my first web server!"

```python
import socket
import termcolor


# -- Server network parameters
IP = "127.0.0.1"
PORT = 8080


def process_client(s):
    # -- Receive the request message
    req_raw = s.recv(2000)
    req = req_raw.decode()

    print("Message FROM CLIENT: ")

    # -- Split the request messages into lines
    lines = req.split('\n')

    # -- The request line is the first
    req_line = lines[0]

    print("Request line: ", end="")
    termcolor.cprint(req_line, "green")

    # -- Generate the response message
    # It has the following lines
    # Status line
    # header
    # blank line
    # Body (content to send)

    # -- Let's start with the body
    body = "Hello from my first web server!\n"

    # -- Status line: We respond that everything is ok (200 code)
    status_line = "HTTP/1.1 200 OK\n"

    # -- Add the Content-Type header
    header = "Content-Type: text/plain\n"

    # -- Add the Content-Length
    header += f"Content-Length: {len(body)}\n"

    # -- Build the message by joining together all the parts
    response_msg = status_line + header + "\n" + body
    cs.send(response_msg.encode())


# -------------- MAIN PROGRAM
# ------ Configure the server
# -- Listening socket
ls = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# -- Optional: This is for avoiding the problem of Port already in use
ls.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)

# -- Setup up the socket's IP and PORT
ls.bind((IP, PORT))

# -- Become a listening socket
ls.listen()

print("SEQ Server configured!")

# --- MAIN LOOP
while True:
    print("Waiting for clients....")
    try:
        (cs, client_ip_port) = ls.accept()
    except KeyboardInterrupt:
        print("Server Stopped!")
        ls.close()
        exit()
    else:

        # Service the client
        process_client(cs)

        # -- Close the socket
        cs.close()
```

Run the server and connect with the browser again. Now we can see the **answer**. Our first **mini-web server** is working!!! :-)

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s12-http-1/echo-server-04.png)

In the **server's console** in pycharm we see that there are **two request messages**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s12-http-1/echo-server-05.png)

This is the first one:

```
GET / HTTP/1.1
```

We see the three parts:

* **Method**: GET. The client wants some object from the server
* **Resource (Path)**: The client wants the main object (/)
* **HTTP Version**: 1.1

The **second request message** is this one:

```
GET /favicon.ico HTTP/1.1
```

The server is asking for the resource **/favicon.ico**. The [favicon](https://en.wikipedia.org/wiki/Favicon) is a short image file that stores the **icon** of the webpage you are accessing. We are ignoring this request

## curl: Watching the http messages

The Linux command **curl** allow us to watch both the  http **request** and **response messages**. Run the **web-server-1.py** and **execute** the following command on the **Linux Console**:

```
curl 127.0.0.1:8080 -v
```

The messages that start with the **\>** symbol are the **requests:** from the client to the server. The messages with the **\<** symbol are the responses: from the server to the client

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s12-http-1/curl-01.png)

## Response with HTML contents

Let's response with our first web page written in [HTML](https://en.wikipedia.org/wiki/HTML). We know nothing about HTML yet. It is the **language** used for creating **web pages**,that describes the structure of the document

In our server we are changing the contents. Instead of responding with a **string**, we will send a **message in HTML**. It is important to change the **Content-type** header from **text/plain** to **text/html** for indicating that we are sending HTML code instead of plain text

Write the following server in the **Sesion-12/web-server-2.py** file

```python
import socket
import termcolor


# -- Server network parameters
IP = "127.0.0.1"
PORT = 8080


def process_client(s):
    # -- Receive the request message
    req_raw = s.recv(2000)
    req = req_raw.decode()

    print("Message FROM CLIENT: ")

    # -- Split the request messages into lines
    lines = req.split('\n')

    # -- The request line is the first
    req_line = lines[0]

    print("Request line: ", end="")
    termcolor.cprint(req_line, "green")

    # -- Generate the response message
    # It has the following lines
    # Status line
    # header
    # blank line
    # Body (content to send)

    # This new contents are written in HTML language
    body = """
    <!DOCTYPE html>
    <html lang="en" dir="ltr">
      <head>
        <meta charset="utf-8">
        <title>Green server</title>
      </head>
      <body style="background-color: lightgreen;">
        <h1>GREEN SERVER</h1>
        <p>I am the Green Server! :-)</p>
      </body>
    </html>
    """
    # -- Status line: We respond that everything is ok (200 code)
    status_line = "HTTP/1.1 200 OK\n"

    # -- Add the Content-Type header
    header = "Content-Type: text/html\n"

    # -- Add the Content-Length
    header += f"Content-Length: {len(body)}\n"

    # -- Build the message by joining together all the parts
    response_msg = status_line + header + "\n" + body
    cs.send(response_msg.encode())


# -------------- MAIN PROGRAM
# ------ Configure the server
# -- Listening socket
ls = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# -- Optional: This is for avoiding the problem of Port already in use
ls.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)

# -- Setup up the socket's IP and PORT
ls.bind((IP, PORT))

# -- Become a listening socket
ls.listen()

print("SEQ Server configured!")

# --- MAIN LOOP
while True:
    print("Waiting for clients....")
    try:
        (cs, client_ip_port) = ls.accept()
    except KeyboardInterrupt:
        print("Server Stopped!")
        ls.close()
        exit()
    else:

        # Service the client
        process_client(cs)

        # -- Close the socket
        cs.close()

```

Now we will see a **different page** in the browser:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s12-http-1/web-server-01.png)

If we test it with the curl command:

```
curl 127.0.0.1:8080 -v
```

We will see that now the ****Content-Type header of the response message is different. Its new value is **"text/html"** because the server is returning an html document

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s12-http-1/web-server-02.png)

# HTML

[HTML](https://en.wikipedia.org/wiki/HTML) is a special language used for defining the **structure** and the contents of the **web pages**. It consist of **text** inside **tags**. There is always an **opening tag** and a **closing tag**. This is the HTML code for the green server we used in the previous example

```html
<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title>Green server</title>
  </head>
  <body style="background-color: lightgreen;">
    <h1>GREEN SERVER</h1>
    <p>I am the Green Server! :-)</p>
  </body>
</html>
```

* **HTML documents** should always start with the special tag: \<!DOCTYPE html\>
* The rest of the html code is inside the **\<html\>** and **\</html\>** tags
* Every html document consist of two parts: the **head** and the **body**
* The **head** contains information for the browser, about the document
* The actual content is located in the **body**
* In this example there are two elements inside the **body**:
  * The **heading**: GREEN SERVER. It is a bigger text
  * A **paragraph**: "I am the green server"
* The **background** color of the elements in the body is set inside the **style attribute**
* You can learn more about html following this [tutorials from the w3school](https://www.w3schools.com/html/)
* You also can learn more HTML in this [notes that I prepared for the CSAAI subject](https://github.com/myTeachingURJC/2019-2020-CSAAI/wiki/S2:-HTML) (in spanish)

## Exercises

All the exercises and experiments performed during this session should be stored in the **Session-12 folder**

### Exercise 1

* **Filename**: Session-12/exercise-1.txt
* **Description**: A Text file in which you should write down you answers to the exercise 1

Run the **web-server-2**. Open the browser and connect to the URL:  **http://127.0.0.1:8080/hello**. Answer the following questions:

* Which is the request line?
* Which is the resource name that the client is asking for? (Path)

Repeat the exercise for this URL:  **http://127.0.0.1:8080/file.html**

Repeat the exercise for this URL:  **http://127.0.0.1:8080/hi/there?name=virus&type=corona**

What should be the URL that we have to write in the Browser for accessing the /dna/u5 resource?

### Exercise 2

* **Filename**: Session-12/we-server-Ex2.py
* **Description**: It is the web-server-2.py server, modify so that the **Content-Type** header has the value: **text/plain**

**Run** the server and use the **curl tool** to confirm that the response message has the new header:

```
< Content-Type: text/plain
```

Try to connect from the Browser. What happens? Could you see the web page? (is the page green?)

### Exercise 3

* **Filename**: Session-12/we-server-Ex3.py
* **Description**: It is the web-server-2.py server, modified so that the **Content-Length** header has the value: **5**

When you connect from the browser without any change in the Content-Length you will see the Green server... but What happens when you modify the Content-Length?

Test it with the curl command. Could you see the HTML message?

### Exercise 4

* **Filename**: Session-12/we-server-Ex4.py
* **Description**: It is the web-server-2.py server, modified so that it reads the **index.html** file and sends it as a response to the client
* **Filename**: Session12/index.html
* **Description**: The HTML page of the Green server, in a file

```html
<!DOCTYPE html>
    <html lang="en" dir="ltr">
      <head>
        <meta charset="utf-8">
        <title>Green server</title>
      </head>
      <body style="background-color: lightgreen;">
        <h1>GREEN SERVER</h1>
        <p>I am the Green Server! :-)</p>
      </body>
    </html>
```

When you connect from the browser, you will se the Green server web page

Once it is working, modify the file **index.html** so that the message that appears is: "I am the Green Server! :-) (MODIFIED BY ME!!!!)"


## END of the session

The session is finished. Make sure, during this week, that everything in this list is checked!

* [ ] You have all the items of the session 11 checked!
* [ ] Your working repo contains the **Session-12 Folder** with the following files:
  * [ ] echo-server.py
  * [ ] web-server-1.py
  * [ ] web-server-2.py
  * [ ] exercise-1.txt
  * [ ] web-server-Ex2.py
  * [ ] web-server-Ex3.py
  * [ ] web-server-Ex4.py
  * [ ] index.html

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