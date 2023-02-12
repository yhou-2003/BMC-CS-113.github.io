---
layout: default
title: Conditionals, Strings, Recursion
type: Lab
number: 03
active_tab: lab
release_date: 2023-02-07

---

<!-- Check whether the assignment is ready to release -->
{% capture today %}{{'now' | date: '%s'}}{% endcapture %}
{% capture release_date %}{{page.release_date | date: '%s'}}{% endcapture %}
{% if release_date > today %} 
<div class="alert alert-danger">
Warning: this assignment is out of date.  It may still need to be updated for this year's class.  Check with your instructor before you start working on this assignment.
</div>
{% endif %}
<!-- End of check whether the assignment is up to date -->


<!-- Check whether the assignment is up to date -->
<!--{% capture this_year %}{{'now' | date: '%Y'}}{% endcapture %}
{% capture due_year %}{{page.due_date | date: '%Y'}}{% endcapture %}
{% if this_year != due_year %} 
<div class="alert alert-danger">
Warning: this assignment is out of date.  It may still need to be updated for this year's class.  Check with your instructor before you start working on this assignment.
</div>
{% endif %}-->
<!-- End of check whether the assignment is up to date -->



{% if page.materials %}
<div class="alert alert-info">
You can download the materials for this assignment here:
<ul>
{% for item in page.materials %}
<li><a href="{{item.url}}">{{ item.name }}</a></li>
{% endfor %}
</ul>

</div>
{% endif %}





{{page.type}} {{page.number}}: {{page.title}}
=============================================================

## Objectives:

The main goals for this lab are for you to get more comfortable with conditionals, string methods, and recursion.


### Paired Programming rules

This lab is a **paired programming assignment.** What exactly does that mean? You will be working in pairs on the CS lab computers. Each pair will be working on one computer. One person will be the **driver** and the other person will be the **navigator**. Here is the rule: the **driver** controlls the lab computer, but the **driver** can only type what the **navigator** tells them to type. For this to work well, each pair should be constantly talking among themselves. After each problem, you will switch roles, the navigator will become the driver and the driver will become the navigator.

> **Switching Partners This Week**
> Please find a new partner. You will working with this partner for the next 3 weeks. In 3 weeks time we will switch partners again.

### Finishing the lab

Before leaving the lab, make sure you fill out the attendance sheet and go through your answers with a TA or instructor.

## 1. Expressions 

Each row in the table below represents an expression. Please fill in the **value** and **types** for each expression.

```
int x = 5;
int y = 13;
int z = 15;
String message = "cat!";
boolean Done = false;
```

| **Expression** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| **value** 	&nbsp;&nbsp;| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**data type** 	|
|---	|---	|---	|
| x < 10 && y < 10 <br> <br>|  	|  	|
| x < 10 \|\| y < 10 <br> <br>|	|  	|  	|
| x < 10 && x > 0<br> <br>|	|  	|  	|
|x > 10 \|\| x < 0 <br> <br>|	|  	|  	|
| (5/x) > 7.0 <br> <br>|	|  	|  	|
| (z/2) > 7.0 <br> <br>|	|  	|  	|
| message.compareTo("cats") == 0 <br> <br>|	|  	|  	|
| !Done <br> <br>|	|  	|  	|
| Done \|\| (x < 6 && y > 10) <br> <br>|	|  	|  	|

# 2. Colors

Consider the following code:

```
String colorName = "purple";

if (colorName.compareTo("red") != 0) {
  System.out.println(colorName + " is not primary");
}
else if (colorName.compareTo("blue") != 0 {
  System.out.println(colorName + " is not primary");
}
else if (colorName.compareTo("yellow") != 0) {
  System.out.println(colorName + " is not primary");
}
else {
  System.out.println(colorName + " is primary");
}
```

### 2.1 Decision Diagram
**TODO:** Draw a decision diagram corresponding to this if statement.

<br><br><br><br><br>

### 2.2 Result of code

**TODO: Question 2.2.1:** 
What does the above code print out when `colorName = "purple"`
<br><br><br>

**TODO: Question 2.2.2:** 
What does the above code print out when `colorName = "red"`
<br><br><br>

**TODO: Question 2.2.3:** 
What does the above code print out when `colorName = "yellow"`
<br><br><br>


# 3. Calendar

## 3.1 Month Number to Name

Write a program that inputs a month as an integer and returns a string name for that month. For example, if we call the function with the number 1, the program should print "January".

```
$ java Month
Enter an integer: 1
January

$ java Month
Enter an integer: 10
October
```

If the user inputs a number that is not between 1 and 12 (inclusive), then make sure to print out a message.

## 3.2 Month Name to Quarter

Write a program that inputs a month as a string and returns the quarter number that the month is in. For example, if we call the function with the month "January", the program should print 1.

> Requirement: Make sure you use a `switch/case` statement here rather than an if/else.
> Make sure to read section 5.4 of the textbook first.


# 4. Strings

Write the following methods in a file named `StringExamples.java`. Test the methods in the `main` method.

## 4.1 Even Length

Write a method, `isEvenLength`, which returns true if the given String has an even number of characters and false otherwise. Implement tests in main to check your answer. For example,

- `isEvenLength("cat")` returns false

- `isEvenLength("")` returns true

- `isEvenLength("a")` returns false


## 4.2 Substrings

> Make sure to read section section 7.9: Substring before completing this section.

Write a method called `subStringN` with 2 paramaters, a string and an integer `n`.

The method should print 2 substrings: 1) the first `n` characters of the string and 2) the last `n` characters of the string. For example,

- `subStringN("hello", 2)` should print `he` on one line and then `lo` on another
- `subStringN("Antidisestablishmentarianism", 4)` should print `Anti` on one line and then `nism` on another.

If the length of the string is shorter than `N`, print an message telling the user.

# 5. Recursion

As discussed in class, recursion is the process of a method invoking itself over and over again. There are two components to a recursive method:

1. A base case that determines when to stop recursively invoking the method
2. a step to perform some computation and make a recursive call to the method. The computation usually involves the results of the recursive call

> Note, make sure to have gone through Chapter 6 before completing the next part of the lab.


##  Sum of numbers
Given a String of numbers, write a method called `sum` that returns the sum of all the numbers in the String. `sum` should have one parameter, the string of numbers

For example `sum(1234)` should return 10.

Below we are going to implement this together. The following questions will help guide you.

### Overview of approach

**TODO:** In class we motivated recursion by discussing a lazy way to do the dishes, i.e. wash one dish, then ask someone to wash the rest of the dishes. **Question:** How would we extend that analogy to this situation here of finding the sum of all the numbers in a string?

<br><br><br>

### Base case 


**TODO: Question:** Let's now think about our base case, i.e. when we no longer want to make a recursive call. What would be special about the value assigned to this parameter (the String that is passed in to the method) to tell us to stop making a recursive call? 

<br><br>

Now implement that base case in the method. 

<br><br>

### Recursive step

**TODO: Question:** During each recursive step, what do we want to keep track off, and what do we want to punt down the line?

<details><summary><b style="color:DodgerBlue;">HINT</b></summary>
What is the result of `1 + sum(234)`
</details> 
<br><br>

We are almost there but there are a few things we still need to do. 
**TODO: Question:** Given the string `1234`, how can we extract the `1`?

<details><summary><b style="color:DodgerBlue;">HINT</b></summary>
Look at the example on page 105 of the textbook.
</details> 
<br><br>

**TODO: Question:** Given the character `1`, how can we get the integer value `1`

<details><summary><b style="color:DodgerBlue;">HINT</b></summary>
What is the ASCII value of `'0'`, what about `'9'`? You can look them up here: https://www.cs.cmu.edu/~pattis/15-1XX/common/handouts/ascii.html</details> 
<br><br>

**TODO: Question:** Given the String `1234`, how can we get the substring `234`?

<details><summary><b style="color:DodgerBlue;">HINT</b></summary>
Checkout the substring methods on the java docs: https://docs.oracle.com/javase/7/docs/api/java/lang/String.html </details> 
<br><br>


Now we are ready to combine these answers to implement our recursive step right after our base case.

### Testing

In your main method, test `sum()` by invoking the method with the following arugments:

- `sum(234)` should return 9
- `sum(2222)` should return 8
- `sum(19802)` should return 20
- `sum(00020)` should return 2

##  Product of numbers
Given a String of numbers, write a method called `product` that returns the sum of all the numbers in the String. `product` should have one parameter, the string of numbers

For example `product(1234)` should return 12.


## Wrap up

In todays lab we covered conditionals, string methods (including comparisons), and recursion.


### Signing out
Before leaving, make sure your TA/instructor have signed you out of the lab. If you finish the lab early, you are free to go.
