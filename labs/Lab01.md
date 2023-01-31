---
layout: default
title: Variables, Input & SSH
type: Lab
number: 01
active_tab: lab
release_date: 2023-01-23

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

The main goals for this lab are for you to get more comfortable with variables, reading in data, and connect to the lab machines. We will be covering the following topics:

- Variables: defining and assigning
- Data types: `String`, `double`, `int`
- `System.out.println()`, `System.out.print()`
- `Scanner` class for reading in data from a user
- arithmetic operators: `+`, `*`, `-`, `\`, `%`
- String concatenation with `+`
- Operators and expressions, order of operations

### Paired Programming rules

This lab is a **paired programming assignment.** What exactly does that mean? You will be working in pairs on the CS lab computers. Each pair will be working on one computer. One person will be the **driver** and the other person will be the **navigator**. Here is the rule: the **driver** controlls the lab computer, but the **driver** can only type what the **navigator** tells them to type. For this to work well, each pair should be constantly talking among themselves. After each problem, you will switch roles, the navigator will become the driver and the driver will become the navigator.

### Finishing the lab

Before leaving the lab, make sure you fill out the attendance sheet and go through your answers with a TA or instructor.

## 1. Expressions 

Each row in the table below represents an expression. Please fill in the **value** and **types** for each expression.

| **Expression** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| **value** 	&nbsp;&nbsp;| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**data type** 	|
|---	|---	|---	|
| 2 + 3 <br> <br>|  	|  	|
| 2.0 + 3 <br> <br>|	|  	|  	|
| 5.5 / 10 <br> <br>|	|  	|  	|
| 5 - 2 * 3 <br> <br>|	|  	|  	|
| "123" <br> <br>|	|  	|  	|
| 48 % 2 <br> <br>|	|  	|  	|
| 55 % 4 <br> <br>|	|  	|  	|
| 2+4*2+1 <br> <br>|	|  	|  	|
| "I" + "love" + "CS113!" <br> <br>|	|  	|  	|


## 2. Sum.java

> Note: The next few problems will require using the `Scanner` class for reading in data from a user. 

### Sum1

Write a program `Sum1.java` that asks the user for two integers and then prints the sum of the numbers. You can assume that the use will put in valid integers. When run, your program should use the same format, i.e. 1) the program asks a user for an integer; 2) the user puts an integer on a new line; 3) the program asks a user for a integer; 4) the user puts a integer on a new line; 5) the program prints the total. In the prompt you show the user, you can use different wording. Below is an exmple. 

```
$ javac Sum1.java; java Sum1
Please give me one number:
5
Please give me a second number:
2
The sum of the two numbers is 7
```


<details><summary><b style="color:DodgerBlue;">HINT</b></summary>

What methods from the Scanner class will scan the next token that a user inputs as an integer? You can check the Java documentation: [https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html)


</details> 



### Sum2

Write a program `Sum2.java` that asks the user for two integers and then prints the sum of the numbers. When run, your program should use the same format, i.e. 1) the program asks a user for an integer; 2) the user gives an integer on the same line; 3) the program asks a user for a integer; 4) the user puts a integer on the same line; 5) the program prints the total. In the prompt you show the user, you can use different wording, *but there should be a space between the prompt and wht the user puts in*. Below is an exmple. 

```
$ javac Sum2.java; java Sum2
Please give me one number: 5
Please give me a second number: 2
The sum of the two numbers is 7
```

<details><summary><b style="color:DodgerBlue;">HINT</b></summary>

You might want to look at Section 1.6 (Displaying two messages) in your textbook.

</details> 

***TODO: Question 1.1:*** Run the `Sum2` program but now input a number with a decimal point. What happens, and why?
<br>
<br>
<br>


### Sum3

Write a program `Sum3.java` that asks the user for two numbers and then prints the sum of the numbers. This time, the numbers should be able to contain decimal points. Below is an exmple. 

```
$ javac Sum3.java; java Sum3
Please give me one number: 5.5
Please give me a second number: 2.6
The sum of the two numbers is 8.1
```

<details><summary><b style="color:DodgerBlue;">HINT</b></summary>

What methods from the Scanner class will scan the next token that a user inputs as a double? You can check the Java documentation: [https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html)


</details> 
<br> <br>

***Checkpoint:*** Before continuing, make sure a TA or instructor has checked your code and answers to the previous part.


## 3. Madlibs

Write a madlib program called `Roses` that asks the user for 2 colors and one adjective, then prints out the filled-in poem. If you are not familiar with madlibs, its the worlds greatest game, at least thats what they say on their [website](https://www.madlibs.com/). Take a quick break and play one with your partner, you'll have fun: [https://www.madtakes.com/](https://www.madtakes.com/)

Below is an example of compiling and running the program:

```
$ javac Roses.java; java Roses
color: pink
color: azure
adjective: funny

Roses are pink
Violets are azure
Sugar is funny
and so are you!
```

<details><summary><b style="color:DodgerBlue;">HINT</b></summary>

There is no method in the Scanner class will scan the next token that a user inputs as a String. Instead, there is another method that we will use to read input as a String. You can check the Java documentation: [https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html)


</details> 

## 4. Hotel Bill

Write a program called `Bill` that takes a user’s hotel room rate and outputs the cost of a 6% sales tax and 10.5% city tourism fee. The program should then output the total bill. Below is an example

```
$ javac Bill.java; java Bill
Room rate: 100
Total nights: 3
-------------------
Tax: $ 18.0
Tourism Fee: $ 31.5
Total: $ 349.50
```

***Checkpoint:*** Before continuing, make sure a TA or instructor has checked your code and answers to the previous part.

## 5. Reading Code

For the rest of the lab, you will be reading and analyzing code. 

## 5.1 Cats

Read the following program called `Cats`. What would the output of this program be?

```
public class Cats {
   public static void main(String[] args) {
       String type = "tuxedo";
       int fish = 3;

       System.out.println("The "+type+" cat caught "+fish+" fish.");
   }
}
```

## 5.2 Errors:

The following programs have a problem. For each program, what is the error? Is error is syntax error, runtime error, or logic error? How can we fix the problem?

- `syntax` errors are issues that a compiler will catch that will prevent the program from compiling
- `runtime` errors are issues that cause the program to crash when the program is running. Above you say an example of a runtime error when the user put in a double but the Scanner expected an integer.
- `logic` errors are issues in the algorithm. For example, say we incorrectly add a 7% sales tax rather than a 6% sales tax above in the `Bill` program.

### 5.2.1 Mystery 1

```
public class Mystery1 {

    public static void main(String[] args) {
    
        Scanner sc = new Scanner(System.in);
        int value = sc.nextInt();
        double fraction = value / 40.4;
        System.out.println("The fraction is "+fraction);
    }
}
```
***TODO: Quesiton 5.2.1.*** 
what is the error? Is the error is syntax error, runtime error, or logic error? How can we fix the problem?
<br><br><br>


### 5.2.2 Mystery 2

```
import java.util.Scanner; 

public class Mystery2 {

    public static void main(String[] args) {
    
        Scanner sc = new Scanner(System.in);
        int value = sc.nextInt();
        double fraction = value / 10;
        System.out.println("The fraction is "+fraction);
    }
}
```

***TODO: Quesiton 5.2.2.*** 
what is the error? Is the error is syntax error, runtime error, or logic error? How can we fix the problem?
<br><br><br>

### 5.2.3 Mystery 3

```
import java.util.Scanner; 

public class Mystery3 {

    public static void main(String[] args) {
    
        Scanner sc = new Scanner(System.in);
        int value = sc.nextInt();
        double fraction = value / 0;
        System.out.println("The fraction is "+fraction);
    }
}
```
***TODO: Quesiton 5.2.3.*** 
what is the error? Is the error is syntax error, runtime error, or logic error? How can we fix the problem?
<br><br><br>


## Wrap up

In todays lab we covered variables, reading input from a user, and erros. 
Originally we planned on covering how to remotely access the lab machines, i.e. how to log into these machines from your own computer. We did not cover it today since it seems like we answered this for most folks last week over Piazza. If you have questions about remotely accessing into the lab machines, please let your TA or instructor in the lab know.

### Signing out
Before leaving, make sure your TA/instructor have signed you out of the lab. If you finish the lab early, you are free to go.
