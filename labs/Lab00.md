---
layout: default
title: Hello World & Errors
type: Lab
number: 00
active_tab: lab
release_date: 2023-01-17

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
{% capture this_year %}{{'now' | date: '%Y'}}{% endcapture %}
{% capture due_year %}{{page.due_date | date: '%Y'}}{% endcapture %}
{% if this_year != due_year %} 
<div class="alert alert-danger">
Warning: this assignment is out of date.  It may still need to be updated for this year's class.  Check with your instructor before you start working on this assignment.
</div>
{% endif %}
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

The main goals for this lab are:

1. Get familiar with the command line
2. Set up your course directory on the CS machines
3. Start using vim


## 1. CS Lab Machines & The Command Line
The computers in the lab rooms (Park 230 and 231) are dual booted with Windows 10 and Ubuntu (a version of linux). This means that you can use either the Windows or Linux operating systems (OS). For this course, we will be using Linux. 

You should have received an email from David Diaz with your credentials to the Computer Science lab machines. If you did not receive credentials from him, immediately stop by his office in Park 294.

***TODO 1:*** Log into the Linux (Ubuntu) OS using the credentials you received from David. 

After logging in, click on the grid on the bottom left of the screen. This will launch a screen showing all the applications. In the search bar on top, type `terminal`, and then click on the application. This will launch the terminal. In this semester we will be working primarily in the terminal.  

### Understanding the Command Line
As soon as the terminal application launches, you should see a black screen. This is where you will type command line commands. For now, we haven't covered any commands in detail so just type anything into the terminal. 


> Note: there is a difference between the terms *terminal*, *command line*, and *shell*, but we will be using them interchangeably. See [GeekForGeeks](https://www.geeksforgeeks.org/difference-between-terminal-console-shell-and-command-line/) if you are curious about the differences.


To run a command in the terminal, click `Enter`. After typing anything into the terminal (here I mean actually mean anything), click `Enter`.

***TODO: Question 1.1:*** After you click `Enter`, what does the terminal tell you?
<br>
<br>
<br>

#### Change your password
You can completely interact with your computer using just the terminal! When a new account is created for you on any computer system, you should always change your password.

***TODO: Change your password!*** In terminal, type the command `psswd` and then press `Enter` and then follow the instructions to change your password.

<details><summary><b style="background-color:DodgerBlue;">Click me for help if you get stuck</b></summary>

Yes, `psswd` is not a valid command. You should see an error message in the terminal that tells you the correct command. 
</details> 

<br>

#### Command Line Prompt
All of the text thats on the left of where you are typing commands is called the `prompt`. You should notice that there are two words in the prompt that are seperated by an `@` symbol.
For example, my prompt says `apoliak@tsunami:~$`. 

***TODO: Question 1.2:*** What are the two words in your prompt? What does the first word indicate (the word infront of the `@`)? What does the second word indicate (the word after the `@`)?

<details><summary><b style="background-color:DodgerBlue;">HINT</b></summary>

To find out what the second word represents, look around the lab computer you are using for an idea.
</details> 

<br>
<br>
<br>




## 2. vim
For the remainder of the lab, you will go through the vimtutor. In the command line, type `vimtutor`. This will launch a tutorial on using vim.

## Wrap up

In the next lab we will 1) learn how to remotely access the lab machines, i.e. how to log into these machines from your own computer, and 2) write Java programs.
