---
layout: default
title: Methods
type: Lab
number: 02
active_tab: lab
release_date: 2023-01-31

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

The main goals for this lab are for you to get more comfortable with methods. We will also be covering String methods.


### Paired Programming rules

This lab is a **paired programming assignment.** What exactly does that mean? You will be working in pairs on the CS lab computers. Each pair will be working on one computer. One person will be the **driver** and the other person will be the **navigator**. Here is the rule: the **driver** controlls the lab computer, but the **driver** can only type what the **navigator** tells them to type. For this to work well, each pair should be constantly talking among themselves. After each problem, you will switch roles, the navigator will become the driver and the driver will become the navigator.

> **Switching Partners Next Week**
> This is the last week you will be working with your current partner.

### Finishing the lab

Before leaving the lab, make sure you fill out the attendance sheet and go through your answers with a TA or instructor.

## 1. Stack Diagram

For each of the follow programs, draw a stack diagram to trace out what happens as the program executes. We removed the `class` just for simplicity

### 1.1 Add
```
  public static int Add(int a, int b) {
    int result = a + b;
    return result; 
  }
  public static void main(String[] args) {
    int a = 4;
    int b = 8;
    int c = Add(b, a);
    System.out.printf("%d + %d = %d\n", a, b, c);
  }

```
<br>
<br>
<br>

### 1.2 Add2

```
  public static int Add(int a, int b) {
    a = 2;
    int result = a + b;
    return result; 
  }
  public static void main(String[] args) {
    int a = 4;
    int b = 8;
    int c = Add(a, b);
    System.out.printf("%d + %d = %d\n", a, b, c);
  }
```
<br>
<br>
<br>

**Checkpoint:** Before continung, have your TA review your stack diagrams with you.


## 2. Average.java

Last week we asked a user for numbers and computed the sum of the numbers. This week we will compute the average of a set of numbers. Instead of implementing our entire algorithm in the main method, we will break out program down into multiple methods.

In 2.1 - 2.x, you will be creating simple methods based on the documentation we provide below.

> Make sure to test each method individually in your main method before moving onto the next method.

### 2.1 Prompt user for number

Write a method called `getUserNumber()` that follows the specification.

```
/**
Asks user for a number

@return the number that a user put in
*/

public static double getUserNumber()
``` 

<details><summary><b style="color:DodgerBlue;">HINT</b></summary>
You can use the `Scanner` class for reading in data from a user. 


</details> 


### 2.1 Sum 2 numbers
```
/**
Sums three numbers
@param a the first number
@param b the second number

@return the sum of two numbers
*/

public static double Sum(double a, double b)
``` 

### 2.3 Sum 3 numbers

Before implementing this function, answer the question below.

```
/**
Sums three numbers
@param a the first number
@param b the second number
@param b the third number


@return the sum of the three numbers
*/

public static double Sum(double a, double b, double c)
``` 


**TODO: Question:** What is different between the methods in 2.2 and 2.3?  

> Try calling `Sum(double a, double b)` when implementing this new function `Sum(double a, double b, double c).

### 2.4 Average
```
/**
Computes an average based on
a sum and total number of items
@param total the sum
@param numItem the number of items that made the sum


@return the average value 
*/

public static double Sum(double total, int NumItem)
``` 



### 2.5 Putting in all together
 
Now in your main method, use these methods to ask a user for 5 numbers and print out the average.

`*` represents user input. 


```
$ javac Average.java; java Average
Please give me a number: *2.5*
Please give me a number: *3.6*
Please give me a number: *9.2*
Please give me a number: *2.2*
Please give me a number: *0*

The average of your numbers is 3.5
```

## 3. Strings

In class we saw how to use Math methods. Now we will look at a few `String` methods. 

If we have a `String`, we can determine the following information:

- how long the string is
- how many times a certain character appears in a string

Look at section 7.8 and 7.9 of the textbook for some more String methods.

> Note: there is another data type in java called a `character`. This is just one single character and we denote it by putting the character between single quotes, e.g. `'a'`. `"a"` would be a `String`, not a `character`. 


**TODO:** Write a program called `WordInfo.java` where you will ask a user for a word and then a character.
The program will then tell the user:
1. how long the word is
2. where in the word that character appears. By where we mean is it the 1st letter, the 2nd letter, etc. 

## Wrap up

In todays lab we covered methods.

If you are using a windows and want to remotely access the lab machines, you should be able to use the application called `Powershell`. I believe most windows machines come with `Powershell` these days. 
### Signing out
Before leaving, make sure your TA/instructor have signed you out of the lab. If you finish the lab early, you are free to go.
