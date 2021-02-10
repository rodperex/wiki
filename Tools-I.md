![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/Cover/Cover.png)

# Session 1: Tools-I

* **Time**: 2h
* **Date**: Wednesday, Feb-10th-2020
* **Goals**:
  * Brief introduction to Github
  * Create your first repository
  * Learn how to access to github from the Pycharm IDE
  * Testing the "Hello world" program in Pycharm

# Contents

* [Introduction](#introduction)  
* [Introduction to Github](#introduction-to-github)  
  * [Our Github's account](#our-githubs-account)  
  * [Playing with repositories](#playing-with-repositories)  
  * [Wikis](#wikis)  
  * [Downloading all the files in a repo](#downloading-all-the-files-in-a-repo) 
  * [Creating a working repo](#creating-our-working-repo)  
* [Working with PyCharm and Github](#working-with-pycharm-and-github)  
  * [Opening Pycharm](#opening-pycharm)  
  * [Cloning our working repo](#cloning-our-working-repo)  
  * [Our first commit to the repo](#our-first-commit-to-the-repo)  
* [Hello world with Pycharm!](#hello-world-with-pycharm)
  * [Configuring the python environment](#configuring-the-python-environment)  
  * [Writting the Hello world program](#writing-the-hello-world-program)  
    * [Creating the hello folder](#creating-the-hello-folder)
    * [Creating a python file](#creating-a-python-file)  
    * [Writing the code](#writing-the-code)  
  * [Running the program](#running-the-program)  
  * [Adding the program to the Github Repo](#adding-the-program-to-the-github-repo)  
* [Exercises](#exercises)
  * [Ex-1: hello.py](#ex-1-hellopy)
  * [Ex-2: count.py](#ex-2-countpy)  
  * [Ex-3: sum20.py](#ex-3-sum20py)  
* [End of the session](#end-of-the-session)
* [Credits](#credits)
* [License](#license)

## Introduction

In the **Programming in Network Environment** subject we will learn how to create programs capable of **communicating** one to other through Internet

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/intro-01.png)

But first, we need to learn about the tools we are going to use: [Github](https://github.com/), [Python](https://www.python.org/), [Firefox](https://www.mozilla.org/es-ES/firefox/new/) and [Pycharm](https://www.jetbrains.com/es-es/pycharm/download) (Community Edition)


## Introduction to Github

Modern **programming projects** have thousand of lines of code and hundred of **developers** working on them. It is necessary to use **powerful tools** to manage it: [The revision control systems](https://en.wikipedia.org/wiki/Repository_(version_control)). The projects are located into a what we call a **repository**


Currently, the two most used controls systems are [Github](https://github.com/) and [GitLab](https://gitlab.com/). Both are based on the **opensource** engine called [git](https://es.wikipedia.org/wiki/Git), developed in 2005 by [Linux Torvalds](https://es.wikipedia.org/wiki/Linus_Torvalds), the creator of the [Linux Kernel](https://en.wikipedia.org/wiki/Linux_kernel)

![](https://github.com/myTeachingURJC/2018-19-PNE/raw/master/wiki/s01_tools/github-logo.png)  
![](https://github.com/myTeachingURJC/2018-19-PNE/raw/master/wiki/s01_tools/GitLab_logo.png)

In this **subject** we will focus on the use of **Github**

### Our Github's account

* Create your account on [Github](https://github.com/). Do not forget to send your **real name** and your **username** in the post in Aula Virtual

* Once you have your account, Github will enable a link to your profile. This is my link (username: Obijuan):

* **Link**: [https://github.com/obijuan](https://github.com/obijuan)

![](https://github.com/myTeachingURJC/2019-2020-CSAAI/raw/master/L01/github-01.png)

You can find a repository tap in the top. It will show you all your current repos. In your profile page Github places the most popular repos 

### Playing with repositories

Just to get familiar with Github, Let's see some of my repositories. Click on the [3D-parts](https://github.com/Obijuan/3D-parts) repo. This is the one I use for sharing all my **3D printable designs**. Anyone can download them, and print them on a **3D printer**

![](https://github.com/myTeachingURJC/2019-2020-CSAAI/raw/master/L01/github-02.gif)

The designs are stored in their own **folders**. We can organize every repository **as we want**, using all the folder we need. In the bottom part you will see images and texts. They are the contents of the **README.md** file, that we can add optionally in every folder or repo

Let's continue our journey through the repos!. Let's enter into this folder:  [2017-10-09-urjc-logo](https://github.com/Obijuan/3D-parts/tree/master/2017-10-09-urjc-logo)

![](https://github.com/myTeachingURJC/2019-2020-CSAAI/raw/master/L01/github-03.png)

There are **3 files** and **3 folders**. Most of the files can be seen directly just by clicking on them. For example, let's click on the [Logo_URJC.png](https://github.com/Obijuan/3D-parts/blob/master/2017-10-09-urjc-logo/Logo_URJC.png) file

![](https://github.com/myTeachingURJC/2019-2020-CSAAI/raw/master/L01/github-04.png)

As it is a **png fil**e, Github shows it as an image. If we want to download it, just press the **Download** button in to top right

Any file from the repository can be downloaded. There is **no need for checking in**. No account is needed for browsing the report or for downloading any files from them

Let's see now this other file: [logo-urjc.svg](https://github.com/Obijuan/3D-parts/blob/master/2017-10-09-urjc-logo/logo-urjc.svg). It is a drawing, in the [SVG](https://es.wikipedia.org/wiki/Gr%C3%A1ficos_vectoriales_escalables) vectorial format

![](https://github.com/myTeachingURJC/2019-2020-CSAAI/raw/master/L01/github-05.png)

As this is a **text file** (the SVG files are written in plain text), instead of the Download button there is a **RAW Button**. If we want to download it, just click with the **right mouse button** and select the *save link as* option

If we enter the **STL** folder and click on the file [urjc-coin.stl](https://github.com/Obijuan/3D-parts/blob/master/2017-10-09-urjc-logo/stl/urjc-coin.stl), as it is a 3D design, Github will render it and allow us to **rotate** it and **change the point of view**

![](https://github.com/myTeachingURJC/2019-2020-CSAAI/raw/master/L01/github-06.png)

In this **animation** you can see our journey though this repository

![](https://github.com/myTeachingURJC/2019-2020-CSAAI/raw/master/L01/github-07.gif)

#### Wikis

Optionally, a **wiki page** can be added to any repo for storing the documentation, and making the information more accesible to the users. For example, in the previous 3D-part repo, I have added a **index** with the most import 3D parts

If you want to **access the wiki**, just click on the **wiki tab**

![](https://github.com/myTeachingURJC/2019-2020-CSAAI/raw/master/L01/github-08.png)

The wiki's link is also available: [https://github.com/Obijuan/3D-parts/wiki](https://github.com/Obijuan/3D-parts/wiki). It allows us to access it as if a standar. It looks like this:

![](https://github.com/myTeachingURJC/2019-2020-CSAAI/raw/master/L01/github-09.png)
 
Now we can browse normally. The documentation that you are reading now, from the Programming  in Network Environment subject, is located **its own wiki page** at Github 🙂

From the [3D parts wiki](https://github.com/Obijuan/3D-parts/wiki), enter to the this design: [URJC Keyring/coin](https://github.com/Obijuan/3D-parts/wiki/Llavero-moneda-URJC). It is located on the same folder we saw before, but now you are looking at the wiki, that is easier for the users

![](https://github.com/myTeachingURJC/2019-2020-CSAAI/raw/master/L01/github-10.png)

In this **animation** you can see our **journey** though the wiki

![](https://github.com/myTeachingURJC/2019-2020-CSAAI/raw/master/L01/github-11.gif)

### Downloading all the files in a repo

You can download either individual files from the repo or all of them. Let's try the second option with this repo [RISC-V-FPGA](https://github.com/Obijuan/RISC-V-FPGA) (We do not use the previous repo because is too big and it will take us more time)

In the **main page** of the repo, click on the **Clone or Download** green button

![](https://github.com/myTeachingURJC/2019-2020-CSAAI/raw/master/L01/github-15.png)

Select the **DOWNLOAD ZIP** option in the bottom of the new windows

![](https://github.com/myTeachingURJC/2019-2020-CSAAI/raw/master/L01/github-16.png)

The browser will show us another window with the **file to download**. Click on the **OK** button

![](https://github.com/myTeachingURJC/2019-2020-CSAAI/raw/master/L01/github-17.png)

The complete process is shown in this animation

![](https://github.com/myTeachingURJC/2019-2020-CSAAI/raw/master/L01/github-18.gif)

In our Download folder there wil be the file **RISC-V-FPGA.zip**, which contains all of the files and folders of that repo. But, **Be carefull!**. It only contains the latest version of the files, not the repo itself. All the information regarding changes, revisions and versions is not there

We can **decompress** this file as usual to have access to all the files and folders

![](https://github.com/myTeachingURJC/2019-2020-CSAAI/raw/master/L01/github-19.gif)

### Creating our working repo

In this subject, all your work will be stored in a **public Github repo**. In this section we will create it from a **template repository**, which has beeen already configured

This is the repository. Click on the link to enter: [2019-2020-PNE-Practices](https://github.com/myTeachingURJC/2019-2020-PNE-Practices)

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/github-01.png)

You can see al the folders were you should store all your practices and work, as well as the **README.md** file. The firs step is to create a copy of this template repo in your Github's account. Press the green button: **Use this template**

Now we should chose a new for the repo.  In the upper left part you will see your **username** (in the pictures you will see mine (obijuan) but you should see yours) Use the same name of the template repo: **2019-2020-PNE-Practices**

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/github-02.png)

Write an optional description for the repo and click on the **Create repository from Template** button.

You will see a this screen: 

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/github-03.png)

After some seconds **your repository will be ready**. You can have a look at your main github page. It should looks like this, but with your username instead of mine:

![](https://github.com/davidrol6/2019-2020-PNE/blob/master/s1-tool-1/github-04.png)

Our repo is ready for working!

In this **animation** you can see all the process:

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/github-05.gif)

## Working with Pycharm and Github

For developing in python we are going to use the [PyCharm IDE](https://www.jetbrains.com/pycharm/download/?gclid=Cj0KCQiA-JXiBRCpARIsAGqF8wU4k1AvuaMc2tQ7gsbn23gdFIMNlczsnPDi-WyXa-cKkdUgxcbW7hYaAn2uEALw_wcB&gclsrc=aw.ds#section=linux) (Community edition 2019.3.2) It is already installed in the Linux machines of the Lab

### Opening PyCharm

Go to the **activities menu** in the top left corner and write pycharm. Click on the PyCharm icon. **CAUTION!** In the lab there are two version of PC. We will use the **Community Edition** (which is OpenSource). Make sure the icon looks like this one:

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-01.png)

If this is **the first time** it is opened, some configuration windows will appear

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-02.png)

Select **Do not import setting** and click on **OK**. Another window will apper asking you to select the Pycharm color theme

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-03.png)

I will use the default theme: **Darcula**. Click on **Next:Featured plugins**

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-04.png)

In this windows just click on **Start using PyCharm**. The initial window will show up:

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-06.png)

### Cloning our working repo

We are going to work on our **working repository** that is in Github. The first step is called c**loning the repo**. It will **copy the repository** from github and creates a **local copy** in **our computer**.This operation is executed only **one time per computer**. If you are working in two computers, one in this Lab and the other at home, you will have to **clone twice**: one per computer

From the main Pycharm windows we select the option **Get from version Control**

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-05.png)

This window shows up. It is asking us for the location of our project in the repository:

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-07.png)

We change to the Browser and go to our **working repo** main page at Github and click on the **Clone or download** button

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-08.png)

Click on the **copy button** on the right side

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-09.png)

Then move to the Pycharm Windows and paste the URL by pressing Ctrl-V on the keyboard:

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-10.png)

Then select below the **local folder** were you want to store your project. By default it is located in the **PycharmProjects** folder in your home. I will use the default folder. Click on the **Clone** button

Now you will be asked if you want to **open** the new project

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-11.png)

Click on **YES**. The main window appears along with a welcome message

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-12.png)

Click on the **Close** button. **We are ready to work on our projects!**

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-13.png)

In this **animation** the whole process is shown

![](https://raw.githubusercontent.com/davidrol6/2019-2020-PNE/master/s1-tool-1/pycharm-14.gif) 

### Our first commit to the repo

If you click on the top left **2019-2020-PNE folder**, you will see all the **contents** of your working project, with all the folder for the practices

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-15.png)

Before doing our first python program, let's make some **changes** to the **README file** and upload into our remote repository in Github. Click on the **small button** in the README file for viewing it as text

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-16.png)

Add some text. Notice how the color of the README file has changed. It is indicating that a change has been made: The **current README** file is **different** than the file stored in the **repository**

Let's **commit** that change. Click on the **green tick** in the upper right corner

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-17.png)

Everytime you commit a change, you should write a comment. In this case we can write *my first change*. Then click on the **commit** button

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-18.png)

Congrats! You've done your first commit! 

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-19.png)

But you have committed your change to the **local repository** in your computer. It is not yet in github. You have to execute a **push command**. Click on the option at **VCS/Git/Push**

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-20.png)

In the next screen click on the **Push** button

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-21.png)

Enter your Github **username** and **password**. Then click on **Log In**

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-22.png)

After some seconds your changes will be pushed

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-23.png)

**Congrats!** You've made your first contribution to your remote github repository!

If you go to your github repo page you will see your changes

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/pycharm-24.png)

## Hello world with Pycharm!

Let's write our first python program in Pycharm. The first step is to configure the python environment.

### Configuring the python environment

We have to chose which python interpreter to use. Go to **File/Setting** and click on the **Project:2019-2020-PNE-Practices/Project Interpreter** option

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/Hello-01.png)

Click on the **configure** button on the right:

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/Hello-02.png)

And then on the **ADD** option

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/Hello-03.png)

Select the first option: **Virtual Environmnet**. Check **New Environment** and click on **OK**

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/Hello-04.png)

And click again on **OK** for closing the Settings Windows

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/Hello-05.png)

The **python interpreter** is ready! You will see the new folder called **venv**. It contains the python interpreter and all the related files needed

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/Hello-06.png)

### Writing the Hello world program

Let's write our first Hello world program in Pycharm. First we create a **new folder** called Hello for working there

#### Creating the Hello Folder

 In the the Pycharm project windows select the **2019-2020-PNE-Practices** project 

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/Hello-07.png)

and click on the **File/New** Menu

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/Hello-08.png)

Then select the **Directory** option

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/Hello2-01.png)

and type in the new directory file: **Hello**. Press the **Enter** Key

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/Hello2-03.png)

In our **project view**, on the right we can see now the new empty folder: **Hello**

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/Hello2-02.png)

In **animation** the process of creating a **new folder** is shown:

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/Hello2-04.gif)

#### Creating a python file

Let's create our first python file. Make sure the **Hello folder is selected**, as we want to create our new file in that directory. Then click on **File/new/python file**

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/Hello2-05.png)

**Type in** the **filename**. For example **hello**. It is not necessary to introduce the extesion (.py) 

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/Hello2-06.png)

As we are working with the **Github repo**, Pycharm ask us if we want this new file to be **added** to our **local repository**. Click on **ADD**. Sometimes you just want to make a quick test on a temporary file. In that case you do not want it to be included in the repo. But in this case, we want to include our **hello.py** file into the repo for learning

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/Hello2-07.png)

We can see now the **new hello.py file** in the **project view** on the right side

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/Hello2-08.png)

Also, the file is opened on a new tap. **We are now ready for typing python code!**. Look at the **green tick** in the upper right corner. It tells us that the hello.py is **ok**, with **no errors**

Notice the color of the new file: green. It means that is a new file, added to the project, but it is not already in the repository, because we still have **not committed** the file

In this **animation** the process of creating a **new python file** is shown

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/Hello2-09.gif)

#### Writing the code

It is time to write the **hello world program**. It consist of two print stataments:

```python
print("This is my first python program in the Pycharm IDE")
print("Hello world!!")
```

In the **hello.py tab** type start typing in the **code**

When the editor detects you have written the first letters, *pr*, it shows below some of the functions that matches. You can continue typing or pressing the **TAB key** for accepting the first choice

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/typing-01.png)

Once the **print()** function is typed, the editor will show us all the possible **parameters** that the print function has. The first one (values) are variables or strings we want to print

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/typing-02.png)

We continue writing the string we want to print. Finish pressing the **enter** key. You should see something like this, with the **green tick** on the right

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/typing-03.png)

Imagine that you make a mistake typing the print. You delete accidentaly the final bracket. In that case you will see a **red exclamation** and a **red mark** on the location where the error is detected

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/typing-04.png)

If you place the **mouse pointer** on the **red line** below the red exclamation, you will get **more information** about the error

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/typing-05.png)

Let's finish our program. Write the second line

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/typing-06.png)

A typical error is to add a **blank new line** after the last line. The **python style guide** recommends not to do that. Therefore, you will see a **warning** in that case:

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/typing-07.png)

If you place the pointer in the **upper mark**, you will read that there is **1 week error**

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/typing-08.png)

If you place the pointer in the **second mark** on the right, you will see the **error message**

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/typing-09.png)

In this **animation** the process of **writing the hello world** is shown

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/typing-10.gif)

In this **animation** some **errors** are forced and corrected

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/typing-11.gif)

### Running the program

The first time a file is created, cannot be executed directly. The buttons for running and debugging cannot be pressed. Also there is an option that says: **add configuration** 

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/run-01.png)

Instead of creating a custom configuration, we will let Pycharm to create one for us. Click on **Run/Run**

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/run-02.png)

Click on the **hello** option

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/run-03.png)

The program will **run**. A **new run** tab is open in the bottom. There you will see the **messages** we have printed. Also notice that now there is a **new configuration**, called **hello** and the run and debug **green buttons** are activated

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/run-04.png)

Once the configuration has been created, **running the program is straightforward**. Just click on the green run button in the toolbar 

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/run-05.gif)

### Adding the program to the github repo

Now that the program is working, it is time to **add** it to our **repo**. First we have lo add it to our **local repo** (commit) and then **pushing** it to the **remote repo** at Github 

* Click on the **commit button**

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/push-01.png)

* Add a **comment** to the commit and press the commit button

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/push-02.png)

Notice that now the hello.py file is **NOT green anymore**. It has the same color than the other files in the local repo

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/push-03.png)

* Now go to **VCS/Git/Push** and click on **Push**

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/push-04.png)

After some seconds, you will see the **confirmation message**. Our local repo has been pushed to Github!

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/push-05.png)

* Go to the browser and **check** that the changes are in **Github**

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/push-06.png)

If you enter into the Hello folder, the **hello.py** file will be there

![](https://github.com/davidrol6/2019-2020-PNE/raw/master/s1-tool-1/push-07.png)

Congrats! You have created, running and committed to the Github repo your first python program

## Exercises

The only way of **mastering** something is practicing, practicing and practicing!

### Ex-1: hello.py

* Add another **print()** statement to the *hello.py* program
* Add some **comments**
* Make sure you get a **green tick**
* **Run** the program
* **Upload** the changes to your github repo

### Ex-2: count.py 

* In the **2019-2020-PNE-Practice** project create a **new folder** called: **Session-01**
* Inside the **Session-01 folder**, write a python the **count.py** program that prints the number from 1 to 20 in the console
* **Upload** that new file in your github repo

### Ex-3: sum20.py

* Inside the **Session-01** folder, write the python **sum20.py** program for calculating the sum of the first 20 integer numbers (1+2+3+...+20). The result should be printed on the console
* Upload that file in your github repo

# END of the session

The session is finished. Make sure, during this week, that everything in this list is checked!

* [ ] You have a Github account
* [ ] You have sent me your real name and Github user name
* [ ] You have the **2019-2020-PNE-Practices** working repo created in your account
* [ ] You know how to write and run programs in Pycharm
* [ ] You have uploaded the **Hello folder** with the **hello.py** program to the repo
* [ ] Exercise 1 done!
* [ ] Exercise 2 done!
* [ ] Exercise 3 done!


# Credits
* [Juan González-Gómez](https://github.com/Obijuan) (Obijuan)
* [Alvaro del Castillo](https://github.com/acs). He designed and created the original content of this subject. Thanks a lot :-)

# License

![](https://github.com/Obijuan/digital-electronics-with-open-FPGAs-tutorial/raw/master/wiki/portada/attribution-share-alike-creative-commons-license.png)

# Links

* [Universidad Rey Juan Carlos de Madrid](https://www.urjc.es/)
* [Escuela Técnica Superior de Ingeniería de Telecomunicaciones (URJC)](https://www.urjc.es/universidad/facultades/escuela-tecnica-superior-de-ingenieria-de-las-telecomunicaciones/content/etsit-escuela-tecnica-superior-de-ingenieria-de-telecomunicacion)