---
layout: default
title: Arrays, Recursion
type: Lab
number: 04
active_tab: lab
release_date: 2023-02-14

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

> **Partners**
> You **must** work with your partner last week. If your partner is not here (or you did not switch last week, let your instructor know). Next week will be the last time you work with this partner this semester. In 2 weeks you will switch partners again.

### Finishing the lab

Before leaving the lab, make sure you fill out the attendance sheet and go through your answers with a TA or instructor.

## 1. Expressions 

Each row in the table below represents an expression. Please fill in the **value** and **types** for each expression. If the value is an array, write out what the array would look like (i.e. the values in each index of the array). If the expression will result in an error, please specify that and the error will be.

```
int[] x = new int[5];
int[] y = {4, 2, 5};
String[] messages = new String[2];
String message = "cat!";
boolean Done = false;
```

| **Expression** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| **value** 	&nbsp;&nbsp;| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**data type** 	|
|---	|---	|---	|
|   x  <br> <br> |    |     |
|   y  <br> <br> |    |     |
|   messages  <br> <br> |    |     |
| x[0] < y[0] <br> <br>|  	|  	|
| x[3] > y[3] <br> <br>|  	|  	|
| messages[0] <br> <br>|  	|  	|
| x.length <= y.length <br> <br> | | |
| messages[1] = message <br> <br>|	|  	|  	|
| messages <br> <br>|	|  	|  	|

# 2. Distances

In this question we will implement a method called `distances` based on the following specification.

```
/**
  Determines how far away each letter in a string is from `A` or `a` depending on if the letter is capitalized or not.
  @param word - an input string of 5 characters
  @return an array of integers. The value at each index determines how far away the corresponding character in `word` is from either `a` or `A`.
*/

public static int[] distances(String word);

```

For the sake of this problem, we can assume that `word` will only contain English letters `a-z` or `A-Z`. Later in the lab we will get rid of this assumption.

### 2.1 Method stub

Lets begin by first writing the method signature in a program called `WordDistances.java`. 

**Question:** To ensure the program compiles, what do we need to add to the method?

<details><summary><b style="color:DodgerBlue;">Answer</b></summary>
We need a return statement. We can either return `null` or just a new empty array of integers.
</details> 
<br><br>


### 2.2 Testing our method

Before we even begin to implement our method, its a good idea to write test cases. 
In the main method, lets invokes this method multiple times. Each time we will pass in a different string. In the table below, fill in the return value that the method should return if we pass in the following strings: 

| **Argument** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| **Return value** 	&nbsp;&nbsp;|
|---	|---	|
|   "aaaaa"  <br> <br> |    |    
|   "AAAAA"  <br> <br> |    | 
|   "abcde"  <br> <br> |    |  
|   "AbCdE"  <br> <br> |    |  
|   "zyxvw"  <br> <br> |    |     


### 2.3 Algorithm

Before implementing any method, it is important to come up with an algorithm. You should write out what steps are necessary in order to solve this problem. 

#### 2.3.1 Subdiving the problem - distanceFromA

Instead of tackling the entire problem at once, lets first tackle one part of the problem. For a given lowercase character, we need to determine how far away the character is from `a`.

Which of the following statements below will do that for us?

 In the table below, fill in the value for each expression. You might want to look up the ASCII value of the letters `a` or `s`.

| **Expression** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| **Value** 	&nbsp;&nbsp;|
|---	|---	|
|   `s` - `a`  <br> <br> |    |    
|   `s` + `a` <br> <br> |    | 
|   `s` * `a`  <br> <br> |    |  
|   `s` \ `a`  <br> <br> |    |  
|   `s` % `a`  <br> <br> |    |    

**Question:** So, which operator should we use to determine how far a lowercase character is from `a`.

<details><summary><b style="color:DodgerBlue;">Answer</b></summary>
subtraction.
</details> 
<br><br>

**Question:** When we apply that operator, does the order of the operands matter? Why or why not? 

<details><summary><b style="color:DodgerBlue;">Answer</b></summary>
Yes! What is `s - a` compared to `a - s`?
</details> 
<br><br>

#### 2.3.2 Implementing distanceFromA

Now that we know we will need to compute the distance of a lower case character from `a`, lets implement a method to do this.

**Question:** Implement the following method

```
/**
  Determines how far a characer is from a
  
  @param letter - the character we are considering
  @return the distance from character to a as an integer

*/
public static int distanceFromA(char letter)
```

#### 2.3.3 Testing distanceFromA

In your main method, make sure to test that this method works as desired. I'd recommend invoking the method with the following arugments: `a`, `z`, `b`, `c`. 


**Question** What should the return value of the function be when we use each of these characters as arguments?

<details><summary><b style="color:DodgerBlue;">Answer</b></summary>
`a`: 0, `z`: 25, `b`: 1, `c`: 2.
</details> 
<br><br>

#### 2.3.4 Imporving distanceFromA
We'd like this method to work for upper case letters as well.

**Question:** How can we modify this method so that it works with lowercase and uppercase English letters? We do not want to change the method signature, that is we want to still be able to pass in a single character and return the distance between that character and `a` or `A`. 

**Write out your algorithm here in simple steps. Then update the body in `distanceFromA`. Finally, add tests to your main method to make sure `distanceFrom` works correctly for uppercase and lower case characters.**

<br><br><br><br>

#### 2.3.5 Continuing the algorithm

Now that we've figured out how to compute the distance between a single character and either `A` or `a`, let's write out or algorithm for solving the larger problem. 
The following steps are out of order, put them in the correct order.

1. Update the value of the 4th index of the array
2. Determine the distance between the 3rd character and `a` or `A`
3. return the array of integers
3. Determine the distance between the 2rd character and `a` or `A`
4. Determine the distance between the 4rd character and `a` or `A`
5. Update the value of the 5th index of the array
5.  Update the value of the 3rd index of the array
5.  Determine the distance between the 5th character and `a` or `A`
6. Initialize an emtpy integer array of length 5
6. Determine the distance between the 1st character and `a` or `A`
7.  Update the value of the 2nd index of the array
8. Update the value of the 1st index of the array

### 2.4 Implementing the method

Now that you correctly ordered the steps of the algorithm, its time to implement our method.

**QUESTION::** Implement the method and then run the tests you wrote earlier in the main method to test your implementation. 


# 4. Strings

This is from last week's lab, make sure you completed this last week. If you did, you can skip to the next section. However, you will find some of the string methods discussed in this section helpful when completing the next section.

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


## 5.1 Sum of numbers
Given a String of numbers, write a method called `sum` that returns the sum of all the numbers in the String. `sum` should have one parameter, the string of numbers

For example `sum(1234)` should return 10.

Below we are going to implement this together. The following questions will help guide you.

### 5.1.1 Overview of approach

**TODO:** In class we motivated recursion by discussing a lazy way to do the dishes, i.e. wash one dish, then ask someone to wash the rest of the dishes. **Question:** How would we extend that analogy to this situation here of finding the sum of all the numbers in a string?

<br><br><br>

### 5.1.2 Base case 


**TODO: Question:** Let's now think about our base case, i.e. when we no longer want to make a recursive call. What would be special about the value assigned to this parameter (the String that is passed in to the method) to tell us to stop making a recursive call? 

<br><br>

Now implement that base case in the method. 

<br><br>

### 5.1.3 Recursive step

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

### 5.1.4 Testing

In your main method, test `sum()` by invoking the method with the following arugments:

- `sum(234)` should return 9
- `sum(2222)` should return 8
- `sum(19802)` should return 20
- `sum(00020)` should return 2

## 5.2 Recursion with arrays

Now imagine we want to compute the sum of integers in an array using a recursive solution. Unlike `.substring(...)` for strings, there is not simple/straight forward method extracting a subarray. Therefore, the signature for the recursive method might look like `public static int sumArray(int[] numbers, int index)`.

When we call this method recursively, we will pass in the same array but will update the `index`.

### 5.2.1 Base Case

**Question:** What do you think is the base case where we will stop making recursive calls? Explain your answer.

<details><summary><b style="color:DodgerBlue;">ANSWER</b></summary>
When `index` is the length of the array - 1. <br>Alternatively when `index` is 0.
 </details> 
<br><br>

**Question:** Now implement the base case.


### 5.2.2 Recursive step

**QUESTION** During each recursive step, what do we want to keep track off, and what do we want to punt down the line?
<br><br><br>

**QUESTION** We gave two possible answers to the quesiton in 5.3.1. How would we update `index` in each recursive call for the first answer and for the second answer above?

<br><br>

**Question:** Now implement the recursive step.

### 5.2.4 Testing

In your main method, test `sumArray(int[] numbers)` by invoking the method with the following arugments:

- `sum([2,3,4)` should return 9
- `sum([2,2,2,2])` should return 8
- `sum([1,9,8,0,2])` should return 20
- `sum([0,0,0,2,0])` should return 2

`sumArray()` should then call and return the value from `sumArray(int[] numbers, int index)`.

## 5.3 Product of numbers
Given an array of integers, write a method called `product` that returns the product of all the numbers in the array. `product` should have one parameter, the string of numbers. Your solution should be recursive.

For example `product([1,2,3,4])` should return 12.

Use the same procedure we outlined in Section 5.2 to complete this problem.

## Wrap up

In todays lab we covered indexing arrays and recursion and practice more working with Strings.


### Signing out
Before leaving, make sure your TA/instructor have signed you out of the lab. If you finish the lab early, you are free to go.
