---
title: "Day 14 : Python Data Types and Data 
  Structures for DevOps"
datePublished: Fri Aug 04 2023 19:41:06 GMT+0000 (Coordinated Universal Time)
cuid: clkwzr7v2000b09la0vyref0n
slug: day-14-python-data-types-and-data-structures-for-devops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691177794567/eb9c1eae-b107-4f39-a837-22e84faded47.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1691178039560/ae92aec8-3f34-4807-9bbf-12038314bde0.png
tags: python, devops, 2articles1week, 90daysofdevops

---

### **🛞Introduction**:

Welcome to Day 14 of the #90DaysOfDevOps challenge! Python is a very high-level object-orient programming language it's very easy to use and the name Python is taken from a show tv show monty python. Today In this blog, we will learn data types in Python what are data types and learn more about data Structures, the difference between list and tuple and learn about sets data type and dictionaries etc...

### **📑Data Types:**

Datatype represents the type of data stored in a variable or memory.

There are two types of Data Type:-

1. Built-in Data type.
    
2. User Defind data type.
    

**Built-in Data type:-**

1. None type
    
2. numeric type
    
3. sequence
    
4. sets
    
5. mappings
    

**User Defined data type:**

1. Array
    
2. class
    
3. module
    
4. <mark>None Type:</mark> None datatype represents an object that doesn’t contain any value
    
5. <mark>Numeric Type:</mark> In the numeric data type there are three types of data types.
    
6. integer(Int)
    
7. float
    
8. complex
    

**<mark>Int</mark>**: The int datatype represents an integer number. An integer number without any decimal point or fraction part. In Python, It is possible to store very large integer numbers as there is no limit to the size of an int datatype.

Ex:-20, 10, -50, -1002

y = 10

**<mark>Float</mark>** – The float data type represents floating point numbers. A floating point number is a number that contains a decimal point.

Ex:-25.56, 10.5, -45.69, -0.8

price = 25.56

run\_rate = -0.8

**<mark>Complex</mark>** – A complex number is a number that is written in the form of a + bj or a + bJ. Where,

a = Real Part of the number

b = Imaginary part of the number

j or J = Square root value of -1

a and b may contain integer or float numbers.

Ex:- 5+7j, 0.8+2j

com = 5+7j

**<mark>Bool</mark>**: The bool datatype represents a boolean value True or False. Python internally represents True as 1 and False as 0.

Ex:- True, False

True + True = 2

True – False = 1

3\. **<mark>Sequence type</mark>**: Following are sequence types:-

(i) String (ii) List (iii) Tuple (iv) Range

**<mark>String</mark>** – String represents a group of characters. Strings are enclosed in double quotes or single quotes.

Ex:- “Hello”, ‘Rahul’

str1 = “DevOps”

str1 = ‘great"

**<mark>List</mark>** – A list represents a group of elements. A list can store different types of elements that can be modified. Lists are dynamic which means size is not fixed. Lists are represented using square brackets \[ \].

Ex:-  data = \[10, 20, -50, 21.3\]

**<mark>Tuple</mark>** – A tuple contains a group of elements that can be of different types. It is similar to List but Tuples are read-only which means we can not modify its element. Tuples are represented using parentheses ( ).

Ex:- data = (10, 20, -50, 21.3)

**<mark>Range</mark>** – Range represents a sequence of numbers. The numbers in the range are not modifiable.

Ex:- rg = range(5)   0 1 2 3 4

rg = range(10, 20, 2)  10 12 14 16 18

**<mark>Set</mark>**: A set is an unordered collection of elements much like a set in mathematics. The order of elements is not maintained in the sets. It means the elements may not appear in the same order as they are entered into the set. A set does not accept duplicate elements. Sets are unordered so we can not access its element using index. Sets are represented using curly brackets { }.

Ex:-data = {10, 20, 30, “GeekyShows”, “Raj”, 40}

data = {10, 20, 30, “GeekyShows”, “Raj”, 40, 10, 20}

### **📌Tasks:**

1. **Give the Difference between List, Tuple and Set. Do Handson and put screenshots as per your understanding.**
    

Lists and tuples are two fundamental data structures in Python, and they have some similarities but also some key differences. Here's a comparison between lists and tuples:

**Mutability:**

(i). Lists are mutable, meaning you can modify, add, or remove elements after the list is created. You can change the values of individual elements or even change the length of the list.

(ii). Tuples, on the other hand, are immutable, meaning once you create a tuple, you cannot change its elements or length. Tuples are fixed and cannot be modified.

**Syntax:**

Lists are defined using square brackets `[]`, e.g., `my_list = [1, 2, 3]`.

Tuples are defined using parentheses `()`, e.g., `my_tuple = (1, 2, 3)`.

Here's a brief example of using lists:

```bash
my_list = [1, 2, 3]
my_list.append(5)  # [1, 2, 3, 5]
my_list[0] = 15    # [15, 2, 3, 4]
```

Here's a brief example of using tuples:

```bash
my_tuple = (1, 2, 3)
# Trying to modify a tuple will raise an error, e.g., my_tuple[0] = 15 will result in TypeError.
```

1. **Create the below Dictionary and use Dictionary methods to print your favorite tool just by using the keys of the Dictionary.**
    

```bash
my_cloud_tools = { 
  1:"Linux", 
  2:"Git", 
  3:"Docker", 
  4:"Kubernetes", 
  5:"Terraform", 
  6:"Ansible", 
  7:"Chef"
}

#print my_fav_tool is "docker"
my_fav_cloud_key = 3
my_fav_cloud_key=my_cloud_tools.get(my_fav_cloud_key)

if my_fav_cloud_key:
    print("my_cloud_tool is:", my_fav_cloud_key)

else:
    print("key is not find in the dictonary")
```

**Output**:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691175222726/b12c411d-e30f-472a-a07d-019edf621e58.png align="center")

```bash
my_cloud_tools = { 
  1:"Linux", 
  2:"Git", 
  3:"Docker", 
  4:"Kubernetes", 
  5:"Terraform", 
  6:"Ansible", 
  7:"Chef"
}

#print my_fav_tool is "docker"
my_fav_cloud_key = 10
my_fav_cloud_key=my_cloud_tools.get(my_fav_cloud_key)

if my_fav_cloud_key:
    print("my_cloud_tool is:", my_fav_cloud_key)

else:
    print("key is not find in the dictonary")
```

**Output:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691175329699/a6736794-f237-4a9b-b6db-09599154effb.png align="center")

**Create a List of cloud service providers eg.**

```bash
cloud_servers =["AWS","Azure","GCP"]
print("these are the most populor cloud service Provider: ", cloud_servers)
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691175593954/7f448389-9606-4c58-929c-e3a3b9929206.png align="center")

**Write a program to add** `Digital Ocean` **to the list of cloud\_providers and sort the list in alphabetical order.**

Now in this task, we will add "Digital Ocean" to the above program

```bash
cloud_servers =["AWS","Azure","GCP"]
print("these are the most populor cloud service Provider: ", cloud_servers)

new_cloud="digit"
cloud_servers.append(new_cloud)
print("updated list of cloud_servers: ")
print(cloud_servers)

cloud_servers.sort()
print("updated list of cloud_servers in the alphabatical orders")
print(cloud_servers)
```

**Output**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691175098539/5b3bdf18-e0e0-443d-8373-304ad71f1c57.png align="center")

### **📍Conclusion:**

Above mentioned information is much important for a DevOps engineer as he has You’ve mastered the art of the use of data types in Python and the use of list and dictionary differences between list and tuple, joining the ranks of legendary DevOps engineers! Embrace version control and collaboration, and your coding adventures shall know no bounds!

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: **akashsingh6474@gmail.com**