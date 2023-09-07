---
layout: default
title: Variables, Converting Data Types, Input
type: Lab
number: 01
active_tab: lab
release_date: 2023-09-04

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
- `System.console().readLine()` for reading in data
- arithmetic operators: `+`, `*`, `-`, `\`, `%`
- String concatenation with `+`
- Operators and expressions, order of operations

### Paired Programming rules

This lab is a **paired programming assignment.** What exactly does that mean? You will be working in pairs on the CS lab computers. Each pair will be working on one computer. One person will be the **driver** and the other person will be the **navigator**. Here is the rule: the **driver** controlls the lab computer, but the **driver** can only type what the **navigator** tells them to type. For this to work well, each pair should be constantly talking among themselves. After each problem, you will switch roles, the navigator will become the driver and the driver will become the navigator.

### Finishing the lab

Before leaving the lab, make sure you fill out the attendance sheet and go through your answers with a TA or instructor.

## 0. CS Lab Machine Setup
Hopefully you completed Lab00 so far. If not, then run the following commands on the terminal 
on the lab machine:

```
mkdir cs113
cd cs113
mkdir labs
cd labs
mkdir lab01
cd lab01
```

To confirm this works, you should see something like
`apoliak@julia:~/cs113/labs/lab01$ ` on the command prompt.
You will hopefully see your username instead of `apoliak` and different
name after the `@` symbol besides for `julia`. Lab00 explains what the second
name means.

Another way to confirm you followed the steps above correctly is to run 
`pwd`. You should the see something like `/home/apoliak/cs113/labs/lab01` (where
again it will say your username rather than `apoliak`.

## 1. Expressions 

Each row in the table below represents an expression. Please fill in the **value** and **types** for each expression.

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-c3ow{border-color:inherit;text-align:center;vertical-align:top}
.tg .tg-7btt{border-color:inherit;font-weight:bold;text-align:center;vertical-align:top}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-7btt"><span style="font-weight:bold;font-style:normal">Expression</span></th>
    <th class="tg-7btt">Value</th>
    <th class="tg-7btt">Type</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-c3ow">2+3</td>
    <td class="tg-c3ow">                                         '              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td>
    <td class="tg-c3ow">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td>
  </tr>
  <tr>
    <td class="tg-c3ow">2.0 + 3</td>
    <td class="tg-c3ow"></td>
    <td class="tg-c3ow"></td>
  </tr>
  <tr>
    <td class="tg-c3ow">5.5 / 10</td>
    <td class="tg-c3ow"></td>
    <td class="tg-c3ow"></td>
  </tr>
  <tr>
    <td class="tg-c3ow"><span style="font-weight:400;font-style:normal;text-decoration:none">5 - 2 * 3</span></td>
    <td class="tg-c3ow"></td>
    <td class="tg-c3ow"></td>
  </tr>
  <tr>
    <td class="tg-c3ow">"123"</td>
    <td class="tg-c3ow"></td>
    <td class="tg-c3ow"></td>
  </tr>
  <tr>
    <td class="tg-c3ow"><span style="font-weight:400;font-style:normal">48 % 2</span></td>
    <td class="tg-c3ow"></td>
    <td class="tg-c3ow"></td>
  </tr>
  <tr>
    <td class="tg-c3ow">55 % 4</td>
    <td class="tg-c3ow"></td>
    <td class="tg-c3ow"></td>
  </tr>
  <tr>
    <td class="tg-c3ow"><span style="font-weight:400;font-style:normal">2+4*2+1</span></td>
    <td class="tg-c3ow"></td>
    <td class="tg-c3ow"></td>
  </tr>
  <tr>
    <td class="tg-0pky"><span style="font-weight:400;font-style:normal">“I” + “love” + “CS113!”</span></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
</tbody>
</table>

## 2. VIM editor

_credit: Swarthmore CS21 Lab 0_

This semester wewill use the vim editor for editing files on our system. You will primarily use vim to create and edit files containing the python program code to run on our system.

The `vi` and `vim` (Vi IMproved) editors are available on every Unix system. `vim` is an efficient and lightweight text editor that is easy to use after learning a few basic commands, which you can learn by running though the `vimtutor` tutorial.

`vim` is particularly useful when working remotely over an ssh connection (an ssh connection is
how you will connect to the lab machines remotely).

`vim` also has many advanced features and is very configurable through, e.g., the use of a `.vimrc` file. However, just a few basic commands are enough to get you started.

<b>Creating and opening a file in Vim</b>

Start by typing `vim example.txt`. This will create a new file called
`example.txt` and will open it up in vim.

<b>Vim operates in two modes:</b>
1. <b>insert mode</b>: keystrokes are interpreted as inserts into the file contents at the point of the cursor.
2. <b>command or escape mode</b>: keystrokes are interpreted as vim commands, which allow a user to do such things as saving, exiting, searching, or moving around in the file.

To switch from <i>insert mode</i> to <i>command mode</i>, press the ESC key.

There are many ways to switch from <i>command mode</i> to <i>insert mode</i>. One way is to press the `i` key.

To save a file make sure you are in <i>command mode</i>. Then type <i>:</i>, this will allow you to run a command. Then type <i>wq</i>. This will
save the changes to the file and then quit the file.

**Some Vim Resources and Links**

Here are som helpful resources:

- [vi (and vim) quick reference](https://www.cs.swarthmore.edu/~newhall/unixhelp/viquickref.pdf)
- [vim links and references](https://www.cs.swarthmore.edu/~newhall/unixlinks.html#edit)
- [Swathmore CS help pages vim info](https://www.cs.swarthmore.edu/newhelp/vim.html)

## 2. Sum.java

> Note: The next few problems will require asking the user for information, storing the information, and then doing something with it.
> Look at slide 8 from the 2nd lecture on how to read in what the user writes in the console.

### Sum1

Write a program `Sum1.java` that asks the user for two integers and then prints the sum of the numbers. You can assume that the user will put in valid integers. When run, your program should use the same format, i.e. 1) the program asks a user for an integer; 2) the user puts an integer on a new line; 3) the program asks a user for a integer; 4) the user puts a integer on a new line; 5) the program prints the total. In the prompt you show the user, you can use different wording. Below is an exmple. 

```
$ javac Sum1.java; java Sum1
Please give me one number:
5
Please give me a second number:
2
The sum of the two numbers is 7
```


<details><summary><b style="color:DodgerBlue;">HINT ABOUT CONVERTING DATA TYPES</b></summary>

Look at slide 30 for how to convert Strings to integers or doubles.


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
- `runtime` errors are issues that cause the program to crash when the program is running. 
- `logic` errors are issues in the algorithm. For example, say we incorrectly add a 7% sales tax rather than a 6% sales tax above in the `Bill` program.

### 5.2.1 Mystery 1

```
public class Mystery1 {

    public static void main(String[] args) {
    
        String input = System.console().readLine()
        int value = Integer.parseInt(input);
        double fraction = value / 10
        System.out.println("The fraction is "+fraction);
    }
}
```

***TODO: Quesiton 5.2.1.*** 
what is the error? Is the error is syntax error, runtime error, or logic error? How can we fix the problem?
<br><br><br>


### 5.2.2 Mystery 2

```
public class Mystery2 {

    public static void main(String[] args) {
    
        String input = System.console().readLine();
        int value = Integer.parseInt(input);
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
public class Mystery3 {

    public static void main(String[] args) {
    
        String input = System.console().readLine();
        int value = Integer.parseInt(input);
        double fraction = value / 0;
        System.out.println("The fraction is "+fraction);
    }
}
```
***TODO: Quesiton 5.2.3.*** 
what is the error? Is the error is syntax error, runtime error, or logic error? How can we fix the problem?
<br><br><br>


## Wrap up

In todays lab we covered variables, reading input from a user, and errors. 

### Signing out
Before leaving, make sure your TA/instructor have signed you out of the lab. If you finish the lab early, you are free to go. If you did not finish, make sure you attend office hours where a TA will sign off that you completed the lab.
