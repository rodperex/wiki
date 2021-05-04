![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s18-json-rest/Cover/Cover.png)

# Session 18: JSON and API rest

* **Time**: 2h
* **Date**: Tuesday, May-4th-2021
* **Goals**:
  * Learning about JSON
  * Learning about API REST
  * Testing our first python program capable of getting remote objects

## Contents

* [Introduction](#introduction)  
* [JSON Format](#json-format)  
  * [Example 1: Reading people's json file from python](#example-1-reading-the-peoples-json-file-from-python)  
  * [Example 2: Arrays](#example-2-arrays)  
  * [Example 3: Array of objects](#example-3-array-of-objects)  
* [API REST](#api-rest)  
  * [Our first JSON server](#our-first-json-server)  
  * [HTTP client python-library](#httpclient-python-library)  
  * [Reading the JSON object from the client](#reading-the-json-object-from-the-client)
* [Exercises](#exercises)
  * [Exercise 1: JSON file](#exercise-1-json-file)
  * [Exercise 2: JSON client](#exercise-2-json-client)
* [End of the session](#end-of-the-session)
* [Author](#author)
* [Credits](#credits)
* [License](#license) 

# Introduction

We are about to finish our main goal: being capable of building **python programs** for connecting to **remote computers** and getting information from them. We still need to know an important tool: the **JSON format**. We also need to know how to **create clients** capable of **reading remote JSON objects** 

# JSON Format

The [JSON](https://en.wikipedia.org/wiki/JSON) format is a **standard** for managing **data** very easily. It allow us to define the **structure of our data**

Imagine that we need to **store information** about **people** in our application: Firstname, lastname and age. Initially we only have one person. We create an **object** in JSON, with the information of this person:

```json
{
    "Firstname": "Troll",
    "Lastname": "Face",
    "age": 20
}
```

We use the **curly brackets {}** to indicate that it is an **object**. Let's save this information in the **people-1.json** file, inside the **Session-18 folder**

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s18-json-rest/json-01.png)

Some **browsers** allow you to **display** the **json files** in **color**. This is what you see if you open the **people-1.json** file in **Firefox**:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s18-json-rest/json-02.png)

You can change to the **raw view** just by clicking on the **raw tab**. Other browsers different than Firefox may have only the raw visualization mode:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s18-json-rest/json-03.png)

For **viewing** the file just **drag** the .json file from the File manager and **drop it** to the browser's URL input

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s18-json-rest/json-04.gif)

## Example 1: Reading the people's json file from python

Let's learn how to **read** that information from our **python** programs. We will use the **json python library**

Our program will open the **people-1.json** file and create the **person** variable with all the data. Then the information is **printed** on the **console**

```python
import json
import termcolor
from pathlib import Path

# -- Read the json file
jsonstring = Path("people-1.json").read_text()

# Create the object person from the json string
person = json.loads(jsonstring)

# Person is now a dictionary. We can read the values
# associated to the fields 'Firstname', 'Lastname' and 'age'

# -- Read the Firtname
firstname = person['Firstname']
lastname = person['Lastname']
age = person['age']

# Print the information on the console, in colors
print()
termcolor.cprint("Name: ", 'green', end="")
print(firstname, lastname)
termcolor.cprint("Age: ", 'green', end="")
print(age)
```

**Execute** the program. You should see this information on the console:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s18-json-rest/json-05.png)

Congrats! You've read your first **JSON file** from python!

## Example 2: Arrays

The JSON format let us define **arrays** of elements, stored in order. The first element is 0, the second 1, and so on. The arrays are created using the **brackets []**

Let's **extend** the people-1.json file for adding a new attribute called **phoneNumber**, which  is an **array** of the phone numbers of that person. This information should be stored in the **people-2.json** file

```json
{
    "Firstname": "Troll",
    "Lastname": "Face",
    "age": 20,
    "phoneNumber": ["1111", "2222"]
}
```
The phone number 0 is "1111" and the phone number 1 is "2222". Let's change our program for printing the new information. The variable **phoneNumbers** contains the **list of phone numbers**. Using a **for loop** we read all the phone numbers and print them on the console

* **Session-18/test-json-2.py** file

```python
import json
import termcolor
from pathlib import Path

# -- Read the json file
jsonstring = Path("people-2.json").read_text()

# Create the object person from the json string
person = json.loads(jsonstring)

# Person is now a dictionary. We can read the values
# associated to the fields 'Firstname', 'Lastname' and 'age'

# Print the information on the console, in colors
print()
termcolor.cprint("Name: ", 'green', end="")
print(person['Firstname'], person['Lastname'])
termcolor.cprint("Age: ", 'green', end="")
print(person['age'])

# Get the phoneNumber list
phoneNumbers = person['phoneNumber']

# Print the number of elements int the list
termcolor.cprint("Phone numbers: ", 'green', end='')
print(len(phoneNumbers))

# Print all the phone numbers
for i, num in enumerate(phoneNumbers):
    termcolor.cprint("  Phone {}:".format(i), 'blue', end='')
    print(num)

```
**Run** the program. This is what is shown in the console

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s18-json-rest/json-06.png)

### Example 3: Array of objects

The **objects** defined with **curly brackets** can also be elements in an **array**. Let's modify our previous example for including additional information on the **type** of phone number. Now, the phone number will have two attributes: the **number** and the **type**

* File: **Session-18/people-3.json**

```json
{
    "Firstname": "Troll",
    "Lastname": "Face",
    "age": 20,
    "phoneNumber": [
      {"number": "1111", "type": "home"},
      {"number": "333", "type" : "office"}
    ]
}
```

We **change** the program for **printing** the new information on the console

* File: **Session-18/test-json-3.py**

```python
import json
import termcolor
from pathlib import Path

# -- Read the json file
jsonstring = Path("people-3.json").read_text()

# Create the object person from the json string
person = json.loads(jsonstring)

# Person is now a dictionary. We can read the values
# associated to the fields 'Firstname', 'Lastname' and 'age'

# Print the information on the console, in colors
print()
termcolor.cprint("Name: ", 'green', end="")
print(person['Firstname'], person['Lastname'])
termcolor.cprint("Age: ", 'green', end="")
print(person['age'])

# Get the phoneNumber list
phoneNumbers = person['phoneNumber']

# Print the number of elements in the list
termcolor.cprint("Phone numbers: ", 'green', end='')
print(len(phoneNumbers))

# Print all the numbers
for i, num in enumerate(phoneNumbers):
    termcolor.cprint("  Phone {}:".format(i), 'blue')

    # The element num contains 2 fields: number and type
    termcolor.cprint("    Type: ", 'red', end='')
    print(num['type'])
    termcolor.cprint("    Number: ", 'red', end='')
    print(num['number'])
```

**Run it**. This is the result:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s18-json-rest/json-07.png)


# API Rest

The **web server** were initially created for delivering information for the **humans**. We use the **browser** for **requesting** web pages to the server, and the browser **renders** them on the **screen** for the human to read

But it is also possible to use the **Web servers** for delivering **objects** different than html pages or images to **any application**. This way, the servers can offer an special **API** (Application Programming Interface) to the applications, that is call **API REST**.  The applications **request** information to the servers using this Interface. The **protocol** used for the communication is **HTTP**

The **response messages** from the server will contain the information in the **JSON format**

### Our first JSON server

Let's create a **server** with a special **entry point** called **/listusers**. When the client request that resource, the server will return a **JSON file** with all the users. For this example, our list will only have one user: the same that we used for the examples 1 to 3 (*trollface*)

The **server** is exactly the same than the servers we have been programming so far, but when the **/listuser** is requested, instead of an html file, what will be returned is the **people-3.json** file. It will be very important to set the **Content-Type** header to **application/json**

When the **main page** is requested, the server will return the **index.html** file, with information about its API REST

This is the server's **code**

* File: **Session-18/json-server.py**

```python
import http.server
import socketserver
import termcolor
from pathlib import Path

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

        # -- Parse the path
        # -- NOTE: self.path already contains the requested resource
        list_resource = self.path.split('?')
        resource = list_resource[0]

        if resource == "/":
            # Read the file
            contents = Path('index.html').read_text()
            content_type = 'text/html'
            error_code = 200
        elif resource == "/listusers":
            # Read the file
            contents = Path('people-3.json').read_text()
            content_type = 'application/json'
            error_code = 200
        else:
            # Read the file
            contents = Path('Error.html').read_text()
            content_type = 'text/html'
            error_code = 404

        # Generating the response message
        self.send_response(error_code)  # -- Status line: OK!

        # Define the content-type header:
        self.send_header('Content-Type', content_type)
        self.send_header('Content-Length', len(str.encode(contents)))

        # The header is finished
        self.end_headers()

        # Send the response message
        self.wfile.write(str.encode(contents))

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

and this is the **index.html** file:

* File: **Session-18/index.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>API REST</title>
</head>
<body>
    <p>JSON Server. My API REST is: </p>
    <ul>
        <li>GET listusers</li>
    </ul>
    <p>Get the list of all my users</p>
    <a href="listusers">Test</a>
</body>
</html>
```

When the **/listusers** resource is requested, the **JSON file** is sent to the **browser** and we will see this:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s18-json-rest/json-08.png)

In this **animation** you can see how it works

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s18-json-rest/json-09.gif)

## HTTP.client python library

The python **HTTP.client** library allow us to implement python clients **easily**. This is an example of use. The client is **requesting** the main page (/) from the server, and printing the data on the console

* File: **Session-18/json-client-1.py**

```python
# -- Example of a client that uses the HTTP.client library
# -- for requesting the main page from the server
import http.client

PORT = 8080
SERVER = 'localhost'

print(f"\nConnecting to server: {SERVER}:{PORT}\n")

# Connect with the server
conn = http.client.HTTPConnection(SERVER, PORT)

# -- Send the request message, using the GET method. We are
# -- requesting the main page (/)
try:
    conn.request("GET", "/")
except ConnectionRefusedError:
    print("ERROR! Cannot connect to the Server")
    exit()

# -- Read the response message from the server
r1 = conn.getresponse()

# -- Print the status line
print(f"Response received!: {r1.status} {r1.reason}\n")

# -- Read the response's body
data1 = r1.read().decode("utf-8")

# -- Print the received data
print(f"CONTENT: {data1}")
```

**Run** the previous server (json-server) and **execute** the client. In the client's console you should see something like this:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s18-json-rest/json-10.png)

**Change** the requested resource to **/listusers** and **execute** the client again. What you get now is:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s18-json-rest/json-11.png)

You've received the **json file**!

## Reading the JSON object from the client

Now we are ready for implementing a **client** that connects to the server through its **REST API**. It should read the **JSON data** and print it on the console. We will use as an example the previous server and print the list of users:

```python

import http.client
import json
import termcolor

PORT = 8080
SERVER = 'localhost'

print(f"\nConnecting to server: {SERVER}:{PORT}\n")

# Connect with the server
conn = http.client.HTTPConnection(SERVER, PORT)

# -- Send the request message, using the GET method. We are
# -- requesting the main page (/)
try:
    conn.request("GET", "/listusers")
except ConnectionRefusedError:
    print("ERROR! Cannot connect to the Server")
    exit()

# -- Read the response message from the server
r1 = conn.getresponse()

# -- Print the status line
print(f"Response received!: {r1.status} {r1.reason}\n")

# -- Read the response's body
data1 = r1.read().decode("utf-8")

# -- Create a variable with the data,
# -- form the JSON received
person = json.loads(data1)

print("CONTENT: ")

# Print the information in the object
print()
termcolor.cprint("Name: ", 'green', end="")
print(person['Firstname'], person['Lastname'])

termcolor.cprint("Age: ", 'green', end="")
print(person['age'])

# Get the phoneNumber list
phoneNumbers = person['phoneNumber']

# Print the number of elements int the list
termcolor.cprint("Phone numbers: ", 'green', end='')
print(len(phoneNumbers))

# Print all the numbers
for i, num in enumerate(phoneNumbers):
    termcolor.cprint("  Phone {}:".format(i), 'blue')

    # The element num contains 2 fields: number and type
    termcolor.cprint("    Type: ", 'red', end='')
    print(num['type'])
    termcolor.cprint("    Number: ", 'red', end='')
    print(num['number'])
```

**Run** the json server and **execute** the client. This is what should be obtained:

![](https://github.com/myTeachingURJC/2019-2020-PNE/raw/master/s18-json-rest/json-12.png)

Congrats! You've read your first **remote json object**!!

# Exercises

The only way of learning is practicing...

## Exercise 1: JSON File

* File: Session-18/people-EX01.json
* File: Session-18/test-json-EX01.py

Extend the **people-3.json** file for adding **two more people** (fake people) using the same attributes (Tip: You should create and array of people). Create a python program (based on test-json-3.py) for printing the information of all the people contained in the JSON file. Initially it should print the **total number of people** in the database

The **output** should be something like this:

![](https://github.com/myTeachingURJC/2018-19-PNE/raw/master/wiki/s17-json/json-05.png)

## Exercise 2: JSON client

* **File**: Session-18/json-server-EX02.py
* **Description**: Modify the json-server.py for returning the **people-EX01.json** file when the resource **/listusers** is requested. This file contains the data of the three users

* **File**: Session-18/json-client-EX02.py
* **Description**: Modify the json-client-2.py for requesting que list of users to the server and printing them o the console, like in the Exercise 1

## END of the session

The session is finished. Make sure, during this week, that everything in this list is checked!

* [ ] You have all the items of the session 17 checked!
* [ ] Your working repo contains the **Session-18 Folder** with the following files:
  * [ ] Error.html
  * [ ] index.html
  * [ ] json-client-1.py
  * [ ] json-client-2.py
  * [ ] json-client-EX02.py
  * [ ] json-server.py
  * [ ] json-server-EX02.py
  * [ ] people-1.json
  * [ ] people-2.json
  * [ ] people-3.json
  * [ ] people-EX01.json
  * [ ] test-json-1.py
  * [ ] test-json-2.py
  * [ ] test-json-3.py
  * [ ] test-json-EX01.py
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