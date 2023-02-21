---
layout: default
title: Tic Tac Toe
type: Lab
number: 05
active_tab: lab
release_date: 2023-02-21

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

The main goals for this lab are for you to get more comfortable with arrays and loops.
In this lab we are going to implement tic tac toe! By the end of this lab you will have a program that will allow two people to play tic-tac-toe.


### Paired Programming rules

This lab is a **paired programming assignment.** What exactly does that mean? You will be working in pairs on the CS lab computers. Each pair will be working on one computer. One person will be the **driver** and the other person will be the **navigator**. Here is the rule: the **driver** controlls the lab computer, but the **driver** can only type what the **navigator** tells them to type. For this to work well, each pair should be constantly talking among themselves. After each problem, you will switch roles, the navigator will become the driver and the driver will become the navigator.

> **Partners**
> You **must** work with your partner last week. If your partner is not here (or you did not switch last week, let your instructor know). This week will be the last time you work with this partner this semester. Next week you will switch partners again.

### Finishing the lab

Before leaving the lab, make sure you fill out the attendance sheet and go through your answers with a TA or instructor.

## 1. Play with your partner!

Lets begin by making sure you are familiar with tic tac toe. If you arent, briefly look at [wikipedia](https://en.wikipedia.org/wiki/Tic-tac-toe). 

Play 3 games of tic-tac-toe with your partner. 

**Question: 1.1** Out of the three games, who won the most?

## 2. Top Down Approach

When designing a program, its a good idea to take a top-down approach. In a top down approach, we use the following steps:

1. Identify features of the program
2. Identify the verbs and nouns in the feature list
3. Sketch out major steps
4. Write the program skeleton
5. Implement and test functions one at a time. 

Before we begin implementing tic-tac-toe, lets follow the steps of our top down approach.

### 2.1 - Identify features of the program

What are the features necessary for tic-tac-toe. Some ideas to consider are what do we need to keep track of what, what does each player need to do, when does the game end? So on and so for.

**TODO: 2.1.1:**
Below, write out the list of features that this program needs for 2 users to play tic-tac-toe.


<details><summary><b style="color:DodgerBlue;">Hint</b></summary>
1. How can we keep track of the board?
2. How can we show the users the board?
3. When should we show the users the board?
</details> 
<br><br>

<br><br><br><br><br>

### 2.2 - Categorize our features

After listing our features, we need to figure out which of our features should be variables and which of the features should be methods.

**TODO Question 2.2.1:** How do we figure out which features are methods, and which are variables? 

<details><summary><b style="color:DodgerBlue;">Answer</b></summary>
Look at the last slide from lecture 05.
</details> 
<br><br><br>


**TODO Question 2.2.2:** Now, in the space below, write out which features we should represent as variables and which feature we should implement as methods.

<br><br><br><br><br>

<b style="color:Red;">DO NOT GO ON IN THIS LAB WITHOUT SHOWING AN INSTRUCTOR YOUR ANSWERS SO FAR. OTHERWISE YOU WILL NOT GET FULL POINTS FOR THIS LAB!</b>

<b style="color:Red;">MAKE SURE YOU WROTE OUT ALL OF YOUR ANSWERS TO ALL OF THE QUESTIONS ABOVE.</b>

### 2.3 Algorithm time!
Now that we outlined what our methods and variables should be, we can go ahead and sketch out the major steps of the program. In esence, we are outlining how the features should fit together.

**TODO Question 2.3.1:** List out the steps for your algorithm. I'll start by giving the first three steps (you will likely have more than 6 steps):

1. Ask the two players for their name
2. Create an empty board
3. Display an empty board
4. ...
5. ...
6. ...


<br><br><br><br><br><br><br>

After you write out the algorithm by hand (or if you get stuck writing out the algorithm), play tic-tac-toe again with your partner, but this time follow every step in your algorithm. This will help you find errors and mistakes in your algorithm. 

**TODO QUESTION 2.3.2:** How did your algorithm above change when you played tic-tac-toe with your partner using the algorithm you came up with.

<br><br><br><br><br><br><br>

<b style="color:Red;">DO NOT GO ON IN THIS LAB WITHOUT SHOWING AN INSTRUCTOR YOUR ANSWERS SO FAR. OTHERWISE YOU WILL NOT GET FULL POINTS FOR THIS LAB!</b>

<b style="color:Red;">MAKE SURE YOU WROTE OUT ALL OF YOUR ANSWERS TO ALL OF THE QUESTIONS ABOVE.</b>

### 2.5 Designing variables

Before we write out our methods in our code, its important think about what type of variables should we use. The most complicated variable we will need to keep track of is the board.


**TODO: Question 2.5.1:** What type of variable should we use to represent our board? 

<details><summary><b style="color:DodgerBlue;">Hint</b></summary>
A board is a 2D grid. What type of variable could we use to represent a 2D grid?
</details> 
<br><br>


### 2.6 Skeleton time!

Now that we have convinced ourselves that we have a sufficient algorithm for implementing tic-tac-toe, its time to start programming! But, we dont want to program everything at once, instead we will implement one method at a time. 

Lets begin by writing out the skeleton of the program. A skeleton of a program is a list of method stubs (these are placeholders for our functions).

**TODO: Question 2.6.1:** What is different about a method stub compared to an implemented method?

<br><br><br>

**TODO: Question 2.6.2:** Now go ahead and write out the skeleton of the program called `TicTacToe.java`. Make sure to have a method stub for each of the methods (verbs) you identified in 2.2.

<br><br><br>

<b style="color:Red;">DO NOT GO ON IN THIS LAB WITHOUT SHOWING AN INSTRUCTOR YOUR ANSWERS SO FAR. OTHERWISE YOU WILL NOT GET FULL POINTS FOR THIS LAB!</b>

<b style="color:Red;">MAKE SURE YOU WROTE OUT ALL OF YOUR ANSWERS TO ALL OF THE QUESTIONS ABOVE.</b>


### 2.7 Implementation!

Now that we've written out our skeleton, we can implement each method. 

**TODO: Question 2.7.2:** In your java program, now implement each method. When you implement one method, make sure to test it in the main method. 


### 2.8 Gametime!

Congrats! you have impelemnted TicTacToe and can play with your partner! 

<b style="color:Red;">NOW TRY BEATING YOUR INSTRUCTOR!</b>

<b style="color:Red;">DO NOT GO ON IN THIS LAB WITHOUT SHOWING AN INSTRUCTOR YOUR ANSWERS SO FAR. OTHERWISE YOU WILL NOT GET FULL POINTS FOR THIS LAB!</b>

<b style="color:Red;">MAKE SURE YOU WROTE OUT ALL OF YOUR ANSWERS TO ALL OF THE QUESTIONS ABOVE.</b>

## 3. Bells and whistles! (Optional)

We can add bells and whistles to our `TicTacToe.java.

Here are some options to consider:

### 3.1 Multiple rounds

So far we only implemented one round of tic-toc-toe, how can we modify our program such that 2 users can play multiple rounds?

### 3.2 Computer player
Our implementation requires two users. However, sometimes we might not have any friends who want to play with us. Add an option for a user to play against a computer. Now we need to make choices for a computer.

I'd recommend starting by implementing a naive computer that just chooses squares at random.

## Wrap up

In todays lab we covered arrays and top-down design. 


### Signing out
Before leaving, make sure your TA/instructor have signed you out of the lab. If you finish the lab early, you are free to go.
