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

***TODO 1:*** Log into the Linux (Ubuntu) OS using the credentials you received from David. **Note:** These are not your BMC/HC credentials that you normally use.

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

<details><summary><b style="color:DodgerBlue;">Click me for help if you get stuck</b></summary>

Yes, `psswd` is not a valid command. You should see an error message in the terminal that tells you the correct command. 
</details> 

<br>

#### Command Line Prompt
All of the text thats on the left of where you are typing commands is called the `prompt`. You should notice that there are two words in the prompt that are seperated by an `@` symbol.
For example, my prompt says `apoliak@tsunami:~$`. 

***TODO: Question 1.2:*** What are the two words in your prompt? What does the first word indicate (the word infront of the `@`)? What does the second word indicate (the word after the `@`)?

<details><summary><b style="color:DodgerBlue;">HINT</b></summary>

To find out what the second word represents, look around the lab computer you are using for an idea.
</details> 

<br>


#### Navigation Commands!
Now we are ready to start using command line arguments:
- ls
- cd
- mkdir 
- rm
- man
- wget 
- cat

##### **`pwd` command**

The first command we'll look at is `pwd`. This command prints the __p__ath to the __w__orking __d__irectory.

Computers are sturctured in a directory hierarchy where directories can contain other directories or files. A directory is just another way of saying a folder.

Run the command `pwd` (this means type `pwd` in the command line and click `Enter` - we'll be moving to this terminology).

***TODO Question 1.3:*** What gets printed out? What do you think it means?

##### **`ls` command**
The next command will look at is `ls`. Instead of us first describing this command, we'll let you try it out yourself. Run the command `ls`.

***TODO: Question 1.4:*** What do you see printed out on in the terminal? What do you think all of that means?

<details><summary><b style="color:DodgerBlue;">HINT</b></summary>
On your desktop, you likely have a folder with your username. Click on that and compare what opens up with what you see in your terminal.
</details> 

We can add arguments to the `ls` command. After typing in `ls`, type the output of the `pwd` command. For example, I would run the following command:

```
ls /home/apoliak/
```

***TODO: Question 1.5:*** When you run `ls` with the path to your working directory, what do you see? Do you see anything different than before when you ran just `ls`? Why or why not?


##### Piping

We can pass the output from one command as an argument to another command by using the `|` symbol.
Run the following command 

```
pwd | ls
```

***TODO: Question 1.6:*** What do you see? Do you see anything different than before when you ran just `ls`?
Why or why not?

#### Home directory

So far we've used `ls` to look at the files and folders in our ***home*** directory. A home directory is where all the files and folders that belong to a specific user exists. 

***TODO:*** Look carefully again at the command line prompt. At the end of the line after the name of the machine you are working on, you should see two characters. What symbols do you see? One of those represents your home directory - which one do you think it might be?

We can answer this question by using the `ls` command.
***TODO:*** Run the ls command twice, each time add one of the characters/symbols as an argument to ls. For example, if the characters were `A` and `B` (they are not), you would run

```
ls A
ls B
```
The output of running `ls` with each character would give you a hint of which of the two symbols represents your home directory.

***TODO Question 1.7:*** So, which of the two characters/symbols represent your home directory? 

#### Absolute vs Direct Paths

So far we used `ls` to look at files in our own directory. When we run the command `ls /home/<USERNAME>` (here <USERNAME> is a place holder for your actual username), the argument was an **absolute path**. An absolute path is the path from the root (or top) of the computer/file system. We can also specify **relative paths**. These are paths that go from the current working directory to another folder that we specify. For example, when we run `ls Downloads/`, that will tell us what files and folders exist in the Downloads directory.

***TODO Question 1.8:*** If we wanted to see what files exist in the Downloads directory but using an absolute path, what argument would we pass to `ls`?


#### Viewing other directories 

From `pwd`, we see that the path to our home directory was `/home/<USERNAME>`.

***TODO Question 1.9:*** How do you think we could use `ls` to find out what other users have an account on the CS lab machines?

<details><summary><b style="color:DodgerBlue;">HINT 1</b></summary>

We can add a specific absolute path as an argument to the `ls` command

</details>

<details><summary><b style="color:DodgerBlue;">HINT 2</b></summary>

The absolute path to your home directory was `/home/<USERNAME\>/`, so what directory does your home directory live in?

</details> 

<br>


We can also use a relative path. From your own directory, run the following command:

```
ls ../
```

***TODO Question 1.10:*** What do you think that did? What do you think `../` means?

<details><summary><b style="color:DodgerBlue;">Answer</b></summary>
That command printed out the contents of the parent directory. `../` represents that parent directory.
</details> 



##### **`cd` command**
The next command will look at is `cd`, which stands for change directory. 

##### **`mkdir` command**

Creating your own CS113 directory.

##### **`rm` command**

##### **`man` command**

##### **`wget` command**

##### **`cat` command**



## 2. vim
For the remainder of the lab, you will go through the vimtutor. In the command line, type `vimtutor`. This will launch a tutorial on using vim.

## Wrap up

In the next lab we will 1) learn how to remotely access the lab machines, i.e. how to log into these machines from your own computer, 2) how to configure your terminal, and 3) write Java programs.
