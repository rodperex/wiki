![](https://github.com/davidrol6/2021-2022-PNE/blob/master/s14-http-module-1/Cover/Cover.png)

# Session 14: HTTP python library

* **Time**: 2h
* **Date**: Tuesday, March-22th-2022
* **Goals**:
  * Learn how to implement **web servers** using the **HTTP python module**
  * Debugging the HTTP protocol with the Browser developer's tools

## Contents

* [Introduction](#introduction)  
* [HTTP module web server](#http-module-web-server)  
* [Web Server 1: Using the httpserver handler](#web-server-1-using-the-httpserver-handler)  
* [Web Server 2: Implementing our own handler](#web-server-2-implementing-our-own-handler)  
  * [WebServer 2-1: Detecting get requests](#webserver-2-1-detecting-get-requests)  
  * [WebServer 2-2: Getting information from the request message](#webserver-2-2-getting-information-from-the-request-message) 
  * [Webserver 2-3: Generating the response message](#webserver-2-3-generating-the-response-message) 
* [Debugging the HTTP protocol](#debugging-the-http-protocol)  
* [Exercises](#exercises)
  * [Exercise 1](#exercise-1)  
  * [Exercise 2](#exercise-2)
  * [Exercise 3](#exercise-3)  
* [End of the session](#end-of-the-session)
* [Author](#author)
* [Credits](#credits)
* [License](#license) 

# Introduction

Python includes an [HTTP module](https://docs.python.org/3/library/http.html) for implementing both HTTP **clients** and **servers** very **easily**. In the previous week we learnt how to implement them from sockets. We did it this way for you to learn how the **socket mechanism** worked. Now that you know how they work, we will focus on programming the server using the **HTTP module**. This is the module that we will use from now on.

We will follow a **top-down** approach: starting with the **fully-working server** provided by the **http module**. Then we will focused on the **internal details** for implementing our own servers

# HTTP module web server

The **HTTP module** includes a fully working web server. Let's test it

* **Create a new folder** in your **2021-2022-PNE-practices** project. Call it: **Session-14**
* **Download** these **html example files** and store them into the **Session-14** folder:
  * [index.html](https://github.com/myTeachingURJC/2018-19-PNE/raw/master/wiki/s13-http-module/examples/index.html)
  * [green.html](https://github.com/myTeachingURJC/2018-19-PNE/raw/master/wiki/s13-http-module/examples/green.html)
  * [blue.html](https://github.com/myTeachingURJC/2018-19-PNE/raw/master/wiki/s13-http-module/examples/blue.html)
  * [pink.html](https://github.com/myTeachingURJC/2018-19-PNE/raw/master/wiki/s13-http-module/examples/pink.html)
* Select the **Session-14** folder

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s14-http-module-1/intro-01.png)

* Right-click on it and chose the **Open in terminal** entry

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s14-http-module-1/intro-02.png)

* From that terminal **execute** the following command:
```
python -m http.server 8080
```

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s14-http-module-1/intro-03.png)


* It will launch the **web server**. Go to the browser and open this page: **http://localhost:8080**. This other URLs are equivalent: **http://0.0.0.0:8080/**, **http://your-IP:8080** and **http://127.0.0.1:8080**. You should see something like this:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s14-http-module-1/intro-04.png)

The server is showing the **index.html** (that is our main web page). You should be able to **navigate** to the other pages, just **clicking on the links**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s14-http-module-1/intro-05.gif)

# Web Server 1: Using the http.server handler

This is our first version of the web server using the **http.server** module. [Here you can find all the documentation of the http.server module](https://docs.python.org/3/library/http.server.html#module-http.server)

The **Handler** is the name given to an object that is called when a client is connected and need to be attended. In this example we are using the **Handler** provided by the **http.server module**

* Create a new python file called **webserver1.py** and type this code

```python
import http.server
import socketserver

# Define the Server's port
PORT = 8080

# -- This is for preventing the error: "Port already in use"
socketserver.TCPServer.allow_reuse_address = True

# -- Use the http.server Handler
Handler = http.server.SimpleHTTPRequestHandler

# -- Open the socket server
with socketserver.TCPServer(("", PORT), Handler) as httpd:

    print("Serving at PORT", PORT)

    # -- Main loop: Attend the client. Whenever there is a new
    # -- clint, the handler is called
    try:
        httpd.serve_forever()
    except KeyboardInterrupt:
        print("Server Stopped!")
        httpd.server_close()
```

Initially a **server socket** is created, bound to our **IP** and **port** and changed to the **listen mode**. Then, **serve_forever()** method is called. It makes the server wait until a client is connected. When it happens, the **handler function** is called. 

* **Execute** it from pycharm. It should work exactly the same as the previous example

# Web Server 2: Implementing our own handler

Let's define our **own Handler** for attending the clients. As always, we will start with something very simple and we will be adding **more functionality** on every example

## Webserver 2-1: Detecting GET requests

This example just prints a **message** on the console telling us that we have received a **GET** request message 

```python
import http.server
import socketserver

# Define the Server's port
PORT = 8080


# -- This is for preventing the error: "Port already in use"
socketserver.TCPServer.allow_reuse_address = True


# Class with our Handler. It is a called derived from BaseHTTPRequestHandler
# It means that our class inheritates all his methods and properties
class TestHandler(http.server.BaseHTTPRequestHandler):

    def do_GET(self):
        """This method is called whenever the client invokes the GET method
        in the HTTP protocol request"""

        # We just print a message
        print("GET received!")

        # IN this simple server version:
        # We are NOT processing the client's request
        # We are NOT generating any response message
        return


# ------------------------
# - Server MAIN program
# ------------------------
# -- Set the new handler
Handler = TestHandler

# -- Open the socket server
with socketserver.TCPServer(("", PORT), Handler) as httpd:

    print("Serving at PORT", PORT)

    # -- Main loop: Attend the client. Whenever there is a new
    # -- clint, the handler is called
    try:
        httpd.serve_forever()
    except KeyboardInterrupt:
        print("")
        print("Stopped by the user")
        httpd.server_close()

```
We should create a **Class** derived from the **http.server.BaseHTTPRequestHandler** base Class. For attending the GET request message, we should implement the **do_GET** method. This method will be called whenever there is a **GET request** from the client. In this example we are just **printing a message** on the console

Notice that we are **not processing** the client **requests**. And we are not generating any **response message**. For the later reason the browser will show us an **error message**

We have also **improved** how the server is **stopped**: whenever the **control-c** is detected (or the server is stopped within pycharm) the **server_close()** method is called and a message is printed on the script

* Type the code in the **webserver2-1.py** file and execute it
* In the server you should see an error like this:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s14-http-module-1/intro-06.png)

**NOTE**: If you still see the previous yellow page is due to the browser has stored it into its cache memory. Just click on the reload button (or press F5). It will send a new request message to the server

In our console there should appear the message: **GET received!** (many times, because as the browser is not getting any response from the server, it is sending the request message many times)

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s14-http-module-1/intro-07.png)

## Webserver 2-2: Getting information from the request message

As our **TestHandler** is derived from the Base class **BaseHTTPRequestHandler**, it inheritates all its properties and methods. You can find all the properties and method in the [http.server documentation](https://docs.python.org/3/library/http.server.html#module-http.server) (Check it!!)

In this example we will print the following properties:

* **self.requestline**: It contatins the full request line (remember that the request line is the first line of the HTTP request messages)
* **self.command**: The command that the clients is invoking. It should be always **GET** as we are inside the do_GET() method
* **self.path**: It contains the resource that the client is asking for

This is the **new web server**:

```python
import http.server
import socketserver
import termcolor

# Define the Server's port
PORT = 8080

# -- This is for preventing the error: "Port already in use"
socketserver.TCPServer.allow_reuse_address = True


# Class with our Handler. It is a called derived from BaseHTTPRequestHandler
# It means that our class inheritates all his methods and properties
class TestHandler(http.server.BaseHTTPRequestHandler):

    def do_GET(self):
        """This method is called whenever the client invokes the GET method
        in the HTTP protocol request"""

        # We just print a message
        print("GET received! Request line:")

        # Print the request line
        termcolor.cprint("  " + self.requestline, 'green')

        # Print the command received (should be GET)
        print("  Command: " + self.command)

        # Print the resource requested (the path)
        print("  Path: " + self.path)

        # IN this simple server version:
        # We are NOT processing the client's request
        # We are NOT generating any response message
        return


# ------------------------
# - Server MAIN program
# ------------------------
# -- Set the new handler
Handler = TestHandler

# -- Open the socket server
with socketserver.TCPServer(("", PORT), Handler) as httpd:

    print("Serving at PORT", PORT)

    # -- Main loop: Attend the client. Whenever there is a new
    # -- clint, the handler is called
    try:
        httpd.serve_forever()
    except KeyboardInterrupt:
        print("")
        print("Stoped by the user")
        httpd.server_close()
```

* **Execute** the new web server and connects from the browser. Check your **console messages**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s14-http-module-1/intro-08.png)

## Webserver 2-3: Generating the response message

Now we will add a **response message** to our handler so that the browser will show some contents instead of an error message. Our server will always send **the same message**, no matter what resources is the client requesting: is a **happy server** :-)

In our **TestHandler** Class we can use the following methods for **generating the response** very easily:

* **self.send_response(code)** : Creates a **response header** with a **status line** with the error CODE passed as an argumento. The response is not really sent yet, but stored into a buffer. The **status codes** can be found in [this link](https://docs.python.org/3/library/http.html#http-status-codes )
* **self.send_header()**: Add a header to the response message (Ex. Content-Type, Content-Length...)
* **self.end_headers()**: Add a blank line to the response message (indicating that the header is finished)

The message body is sent using the **self.wfile.write()** method

```python
import http.server
import socketserver
import termcolor

# Define the Server's port
PORT = 8080

# -- This is for preventing the error: "Port already in use"
socketserver.TCPServer.allow_reuse_address = True


# Class with our Handler. It is a called derived from BaseHTTPRequestHandler
# It means that our class inheritates all his methods and properties
class TestHandler(http.server.BaseHTTPRequestHandler):

    def do_GET(self):
        """This method is called whenever the client invokes the GET method
        in the HTTP protocol request"""

        # Print the request line
        termcolor.cprint(self.requestline, 'green')

        # IN this simple server version:
        # We are NOT processing the client's request
        # It is a happy server: It always returns a message saying
        # that everything is ok

        # Message to send back to the clinet
        contents = "I am the happy server! :-)"

        # Generating the response message
        self.send_response(200)  # -- Status line: OK!

        # Define the content-type header:
        self.send_header('Content-Type', 'text/plain')
        self.send_header('Content-Length', len(contents.encode()))

        # The header is finished
        self.end_headers()

        # Send the response message
        self.wfile.write(contents.encode())

        return


# ------------------------
# - Server MAIN program
# ------------------------
# -- Set the new handler
Handler = TestHandler

# -- Open the socket server
with socketserver.TCPServer(("", PORT), Handler) as httpd:

    print("Serving at PORT", PORT)

    # -- Main loop: Attend the client. Whenever there is a new
    # -- clint, the handler is called
    try:
        httpd.serve_forever()
    except KeyboardInterrupt:
        print("")
        print("Stoped by the user")
        httpd.server_close()
```

* **Run the server**. Now the browser should display the **following message**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s14-http-module-1/intro-10.png)

And this is what you get in the **pycharm** console:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s14-http-module-1/intro-09.png)

# Debugging the HTTP protocol

The servers are sometimes **hard to debug**. Maybe one of our server is not working fine, but we do not know why. The browsers have tools for helping the **developers** to understand what is going wrong. We will learn how to use the Firefox's **developer toools**. Although I will use Firefox in the examples, the Chrome browser has also very similar tools

* **Run** the previous web server
* Go to the Browser
* click on the **top-right menu** and select the entry **webdeveloper/network**
* Connect to the server: localhost:8080
* You will see all the **requests** done by the browser, and their **status codes**

In this **animation** you can see the process:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s14-http-module-1/intro-11.gif)

In the lower panel you will see all the **requests** sent by the **browser**. This appear on the bottom by default, but it can be placed anywhere. Maybe you will see it on your right

In this example we see that the browser has sent **two request messages**. The first one is the **main page** (resoruce /) with an **Status code** of **200**: everything went ok. The second one is the [favicon.icon](https://en.wikipedia.org/wiki/Favicon). It is an optional small icon displayed on the browser's tab. As our server is not sending it to the browser, a **404 Status code** is obtained (not found)

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s14-http-module-1/intro-12.png)

* **Clicking** on the first request will give you **more information** about the **response** and **request messages** interchanged:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s14-http-module-1/intro-13.png)

## Exercises

All the exercises and experiments performed during this session should be stored in the **Session-14 folder**

### Exercise 1

* **Filename**: Session-14/webserver-EX01.py
* **Description**: Program a server, based on **webserver4.py** that **only** has a **main page** (/ resource). If the client request this resource, the server sends the content: **"Welcome to my server"**. But if any other resource is requested, the server should display and error message: **"Resource not available"**

This is what you should see when the **main page** is requested:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s14-http-module-1/Exercise-01.png)

and this is what is shown when **any other page** different than the main page is requested:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s14-http-module-1/Exercise-02.png)

### Exercise 2

* **Filename**: Session-14/webserver-EX02.py
* **Description**: Modify the previous server so that the main page returned is the index.hmtl from a file. Notice that now there are two ways for reaching the main page: **localhost:8080** and **localhost:8080/index.html**. Both URLs should return the index.html HTML file. If a different resource than the main page is request, the **Error.html** page should be return (this file was proposed as an exercise in Practice 4)

In this **animation** you can see how it should behave:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s14-http-module-1/Exercise-03.gif)

### Exercise 3

* **Filename**: Session-14/webserver-EX03.py
* **Description**: Modify the previous server so that **any resource** requested from the server is treated as a **file**. For example, the URL: **localhost:8080/myfile.html** means that the server will open the the file **myfile.html** and send it to the client. If the requested file is not available on the server, the Error.html page is sent. Use the **Path** object from the **pathlib** python module for opening the files. You will have to catch the **FileNotFoundError** exemption for knowing if the requested file exist or not

This is an **example** of how the server should behave:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s14-http-module-1/Exercise-04.gif)

## END of the session

The session is finished. Make sure, during this week, that everything in this list is checked!

* [ ] You have all the items of the session 13 checked!
* [ ] Your working repo contains the **Session-14 Folder** with the following files:
  * [ ] webserver1.py
  * [ ] webserver2.py
  * [ ] webserver3.py
  * [ ] webserver4.py
  * [ ] webserver-EX01.py
  * [ ] webserver-EX02.py
  * [ ] webserver-EX03.py
  * [ ] blue.html
  * [ ] Error.html
  * [ ] green.html
  * [ ] index.html
  * [ ] pink.html
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