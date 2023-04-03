---
title: "#Day14: Python Data Types and Data Structures for DevOps #90DaysofDevOps"
datePublished: Mon Apr 03 2023 16:31:29 GMT+0000 (Coordinated Universal Time)
cuid: clg11tlau000f0alagbz1hu9c
slug: day14-python-data-types-and-data-structures-for-devops-90daysofdevops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680539432098/7dd1ef59-b25a-4239-8e0e-0acb9a5763db.png
tags: python, data-structures, python3, devops, data-types

---

### Data Types

* Data types are the classification or categorization of data items. It represents the kind of value that tells what operations can be performed on a particular data.
    
* Since everything is an object in Python programming, data types are actually classes and variables are instance (object) of these classes.
    
* Python has the following data types built-in by default: Numeric(Integer, complex, float), Sequential(string,lists, tuples), Boolean, Set, Dictionaries, etc
    

To check what is the data type of the variable used, we can simply write: `your_variable=100` `type(your_variable)`

### Data Structures

Data Structures are a way of organizing data so that it can be accessed more efficiently depending upon the situation. Data Structures are fundamentals of any programming language around which a program is built. Python helps to learn the fundamental of these data structures in a simpler way as compared to other programming languages.

* Lists Python Lists are just like the arrays, declared in other languages which is an ordered collection of data. It is very flexible as the items in a list do not need to be of the same type
    
* Tuple Python Tuple is a collection of Python objects much like a list but Tuples are immutable in nature i.e. the elements in the tuple cannot be added or removed once created. Just like a List, a Tuple can also contain elements of various types.
    
* Dictionary Python dictionary is like hash tables in any other language with the time complexity of O(1). It is an unordered collection of data values, used to store data values like a map, which, unlike other Data Types that hold only a single value as an element, Dictionary holds the key:value pair. Key-value is provided in the dictionary to make it more optimized
    

## Task1

1. ### Give the Difference between List, Tuple and set. Do Handson and put screenshots as per your understanding.
    

Features of list are:

**List** -

1. It is a data type in Python which can be written as a list of comma-separated values(items) between square brackets\[\].
    
2. Lists are mutable .i.e it can be converted into another data type and can store any data element in it.
    
3. Lists can store any type of element.
    

**Hands-on**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680532326963/887cb57f-de22-434b-aebb-27af6b035822.png align="center")

**Tuple -**

1. Tuple is an immutable sequence in python.
    
2. It cannot be changed or replaced since it is immutable.
    
3. It is defined under parenthesis().
    
4. Tuples can also store any type of element
    

**Hands-on -**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680533464505/02241fac-d1ef-42ef-a7f8-3510735c27ce.png align="center")

**Sets -**

1. Sets are unordered collection of elements or unintended collection of items in Python.
    
2. Here, the order in which the elements are added into a set is not fixed, it can change frequently.
    
3. It is defined under curly braces{}
    
4. Sets are mutable, however only immutable objects can be stored in it
    

**Summary of differentiation:**

| **List** | **Set** | **Tuple** |
| --- | --- | --- |
| Lists is Mutable | Set is Mutable | Tuple is Immutable |
| It is Ordered collection of items | It is Unordered collection of items | It is Ordered collection of items |
| Items in list can be replaced or changed | Items in set cannot be changed or replaced | Items in tuple cannot be changed or replaced |

### Task2

**Create below Dictionary and use Dictionary methods to print your favourite tool just by using the keys of the Dictionary.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680537797561/b27d20c7-1a33-4041-8e0c-0d861656e199.png align="center")

### Task3

**Create a list of cloud service providers. Write a program to add** `Digital Ocean` **to the list of cloud\_providers and sort the list in alphabetical order.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680538527472/613bb69d-b77a-49f8-8526-2e90f174c9ee.png align="left")

**Executing it using python3**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680538631382/9cae33dd-4aae-40be-af0b-c2e090518d04.png align="left")

**Digital\_Ocean is appended an the list is sorted alphabetically.**