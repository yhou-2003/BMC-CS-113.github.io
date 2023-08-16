---
layout: default
title: Interfaces
type: Lab
number: 08
active_tab: lab
release_date: 2023-03-28

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

The main goals for this lab are for you to get more comfortable implementing interfaces and working with classes.

### Paired Programming rules

This lab is a **paired programming assignment.** What exactly does that mean? You will be working in pairs on the CS lab computers. Each pair will be working on one computer. One person will be the **driver** and the other person will be the **navigator**. Here is the rule: the **driver** controlls the lab computer, but the **driver** can only type what the **navigator** tells them to type. For this to work well, each pair should be constantly talking among themselves. After each problem, you will switch roles, the navigator will become the driver and the driver will become the navigator.

> **Partners**
> You **must** work with your partner from last week. If they are not here, please see your instructor.

### Finishing the lab

Before leaving the lab, make sure you fill out the attendance sheet and go through your answers with a TA or instructor. You will not get full credit otherwise.

## 1. Overview
In this lab you will be adding some features to a Bank. 
You will be creating a file, called `MyBank.java`. By the end of this lab, you will have written a program to that implements a working Bank.

**TODO:** Download the files `BankAccount.java` and `BankActions.java` from `https://cs.brynmawr.edu/cs113/website/labs/lab08/`.

## 2. MyBank

Create a new class called `MyBank`. The class should contain the following instance methods:

- array of BankAccounts as an instance variable. 
- a name of the bank.

For this lab, it is okay if you do not implement getters or setters.

**Hint:** Make sure the access modifiers for the instance variables ensure that no other class can directly access the instance variables.

**TODO:** Implement a constructor that specifies the size of the Bank, i.e. how many accounts it can store. 

**TODO:** Implement a toString() method. The String should indicate the name of the bank and how many accounts it stores and how many maximum accounts it can currently store.



## 3. BankActions

**Question: 3.1:** In the space below, write down what actions should a bank support (i.e. what are the actions a bank should be able to do)? 
<br><br><br><br>
<br><br>

**Question: 3.2:** Look at the file called `BankActions.java`. Do the actions in the file align with what you wrote above?

<br><br><br><br><br>

### 3.2 Implementing BankActions

Now modify the line in `MyBank.java` where you declare the class so that it looks like this:

```
public class MyBank implements BankActions
```

Now compile `MyBank.java`. 

**Question: 3.2.1:** In the space below, write down the error message you see and what you think this means. 
<br><br><br><br>
<br><br>


Now, lets **add method stubs to our class.**
**Question: 3.2.1:** After adding method stubs, compile `MyBank.java`. In the space below, write down if the error message no longer appears. If it does, why do you think its the case? If you are not sure, please reach out to your instructor or TAs.
<br><br><br><br>
<br><br>


Now, one by one begin **implementing the methods**. When implementing the methods in an interface, you are free to choose the implementation details as long as you obey the contract specified by the interface. 

For example, this means that when you create a new account, you are free in your own bank to decide the initial balance. If you want to attract customers, you can give them more money than your competing bank.

Another example is that when you add a new account to the list of accounts, you are free to add the account to the begining of the list, the end of the list, the middle of the list - whereever you like! Next week we'll learn about different drawbacks to this decision.

**Requirements:**

- The bank cannot turn away a customer when there is no more room, thats bad business!
- Test each of the methods in your main method. 
- First create an instance of `MyBank` that has room for one account.
- Then, using a loop, add 8 accounts. After you add an account, make sure to print out the `MyBank` object so we can see the status of the Bank.

## Wrap up

In today's lab we covered interfaces and searching. You gained more practice working across multiple files and growing arrays!

### Signing out
Before leaving, make sure your TA/instructor have signed you out of the lab. If you finish the lab early, you are free to go.
