---
title: "#Day13: Python Basics for DevOps
#90DaysofDevOps"
datePublished: Sat Apr 01 2023 20:12:49 GMT+0000 (Coordinated Universal Time)
cuid: clfyeuius000309la8h7l1fwz
slug: day13-python-basics-for-devops-90daysofdevops
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/ZIPFteu-R8k/upload/767c98c1f8f6add922580734c97dd5f2.jpeg
tags: linux, python, windows, devops

---

Starting the basics of Python as it is also important for Devops Engineer to build the logic and Programs.

## **What is Python?**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680379674548/cef0d51e-f31f-461e-a404-e6bff59df051.png align="center")

* Python is a Open source, general purpose, high level, and object-oriented programming language.
    
* It was created by **Guido van Rossum**
    
* Python consists of vast libraries and various frameworks like Django,Tensorflow, Flask, Pandas, Keras etc.
    

## Why Python?

Python is a lot easier to code and learn. Python programs can be written on any plain text editor like ***notepad***, ***notepad++***, or anything of that sort. One can also use an [**online IDE for writing Python codes**](https://ide.geeksforgeeks.org/index.php) or can even install one on their system to make it more feasible to write these codes because IDEs provide a lot of features like intuitive code editor, debugger, compiler, etc.

## **How to Install Python?**

You can install Python in your System whether it is window, MacOS, ubuntu, centos etc. Below are the links for the installation:

### **Installation on Windows:**

* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680380303594/a0a2bc24-0ff2-4c2b-9b7e-efcfacdb5a8e.png align="center")
    

This can be done by following the step by step instructions provided below:

#### What if Python already exists? Let’s check

To check if your device is pre-installed with Python or not, just go to the Command line(search for cmd in the Run dialog( + R).  
Now run the following command:

`python --version`

If it is already installed it will generate a message with the python version available

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680377444960/bd68c80f-ec00-4955-aab0-ea27568e2d41.png align="center")

Incase it is not installed, here's how to get started:

Before starting with the installation process, you need to download it. For that all versions of Python for Windows are available on [**python.org**.](https://www.python.org/)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680377583248/8c393988-f7ea-492d-8019-41095cd24f3a.png align="center")

Select the required version and follow the instructions given below for installation:

**Getting started:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680377683824/6bf47ce1-88da-4035-a927-0904f83615a9.png align="center")

**Installing libraries:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680377710733/f05d3abc-0de8-47be-aed9-843c50e89f12.png align="center")

**Installing pip and other features:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680377741098/e6ab1184-1fe9-4ad5-a94b-1b76e77c6f3e.png align="center")

**Finishing installation:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680377764716/88ef8afa-8878-4628-af0b-6af751291342.png align="center")

To verify the installation enter the following commands in your Terminal.

`python`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680377820613/807f5ec5-c513-42a2-99af-6ae69dc5e420.png align="center")

### **Installation in linux(ubuntu):**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680380490557/0852d20c-21d6-42a3-b881-ac9adc97403e.png align="center")

Ubuntu 20.04 and other versions of Debian Linux ship with Python 3 pre-installed. To make sure that our versions are up-to-date, update your local package index:

`sudo apt update`

Then upgrade the packages installed on your system to ensure you have the latest versions:

`sudo apt -y upgrade`

The `-y` flag will confirm that we are agreeing for all items to be installed, but depending on your version of Linux, you may need to confirm additional prompts as your system updates and upgrades.

Once the process is complete, we can check the version of Python 3 that is installed in the system by typing:

`python3 -V`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680378175988/a881f79e-6b88-47a9-b479-3c188de9bc2b.png align="left")

You’ll receive output in the terminal window that will let you know the version number. While this number may vary, the output will be similar to this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680378216147/81ee475f-6093-4aa9-a4cb-84d6adbe38ea.png align="left")

To manage software packages for Python, let’s install **pip**, a tool that will install and manage programming packages we may want to use in our development projects.

`sudo apt install -y python3-pip`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680378291991/e6f33810-68a4-4a59-b95c-e291b02b2c12.png align="center")

**Once you have installed pip, you can use it to install packages for Python.**

**Now, you have Python installed in your system!**

## Different Data Types in Python.

There are several built-in data types used to represent different types of data:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680378644305/abbb91a3-12e3-47b8-a87f-2497d3ef756a.png align="center")

1. **Numeric Data Type:** The numeric data type in Python represents the data that has a numeric value. A numeric value can be an integer, a floating number, or even a complex number. They are further subdivided into int, float and complex number classes in python
    
    * **Integers** – This value is represented by int class. It contains positive or negative whole numbers (without fractions or decimals). In Python, there is no limit to how long an integer value can be.
        
    * **Float** – This value is represented by the float class. It is a real number with a floating-point representation. It is specified by a decimal point. Optionally, the character e or E followed by a positive or negative integer may be appended to specify scientific notation.
        
    * **Complex Numbers** – Complex number is represented by a complex class. It is specified as *(real part) + (imaginary part)j*. For example – 2+3j
        
2. **Sequence Data type:** The sequence Data Type in Python is the ordered collection of similar or different data types. Sequences allow storing of multiple values in an organized and efficient fashion. There are several sequence types in Python –
    
    * **String:** in Python are arrays of bytes representing Unicode characters. A string is a collection of one or more characters put in a single quote, double-quote, or triple-quote. In python there is no character data type, a character is a string of length one. It is represented by str class.
        
    * **List:** are just like arrays, declared in other languages which is an ordered collection of data. It is very flexible as the items in a list do not need to be of the same type.
        
    * **Tuple:** Just like a list, it is also an ordered collection of Python objects. The only difference between a tuple and a list is that tuples are immutable i.e. tuples cannot be modified after it is created. It is represented by a tuple class.
        
3. **Boolean Data type**: Data type with one of the two built-in values, True or False. Boolean objects that are equal to True are truthy (true), and those equal to False are falsy (false). But non-Boolean objects can be evaluated in a Boolean context as well and determined to be true or false. It is denoted by the class bool.
    
    **Note** – True and False with capital ‘T’ and ‘F’ are valid booleans otherwise python will throw an error.
    
4. **Set Data type:** It is an unordered collection of data types that is iterable, mutable and has no duplicate elements. The order of elements in a set is undefined though it may consist of various elements.
    
5. **Dictionary Data type:** A dictionary in Python is an unordered collection of data values, used to store data values like a map, unlike other Data Types that hold only a single value as an element, a Dictionary holds a key: value pair. Key-value is provided in the dictionary to make it more optimized. Each key-value pair in a Dictionary is separated by a colon : , whereas each key is separated by a ‘comma’.