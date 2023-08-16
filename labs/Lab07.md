---
layout: default
title: Designing classes
type: Lab
number: 07
active_tab: lab
release_date: 2023-03-21

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

The main goals for this lab are for you to get more comfortable designing classes and working with objects.

### Paired Programming rules

This lab is a **paired programming assignment.** What exactly does that mean? You will be working in pairs on the CS lab computers. Each pair will be working on one computer. One person will be the **driver** and the other person will be the **navigator**. Here is the rule: the **driver** controlls the lab computer, but the **driver** can only type what the **navigator** tells them to type. For this to work well, each pair should be constantly talking among themselves. After each problem, you will switch roles, the navigator will become the driver and the driver will become the navigator.

> **Partners**
> You **must** work with your partner from last weekYou will be working together for one more week. 

### Finishing the lab

Before leaving the lab, make sure you fill out the attendance sheet and go through your answers with a TA or instructor. You will not get full credit otherwise.

## 1. Overview
In this lab you will be designing a student's course schedule. You will be creating two files, `Course.java` and `Schedule.java`. By the end of this lab, you will have written a program to read in a file containing a students schedule, parse the file, and create `Course` objects and a schedule. 

**TODO:** Download the file `schedule.csv` from the course website. Run `wget https://cs.brynmawr.edu/cs113/website/labs/lab07/schedule.csv` to download the file.


## 2. Course

**Question: 2.1:** In the space below, write down what properties a college course has?
<br><br><br><br>
<br><br>

**Question: 2.2:** Look at the file called `schedule.csv`. Each line there represents another course. According to that file, a course has 5 properties. In the space below, write down what those properties are?

<br><br><br><br><br>


Now that we know a course will have 5 properties, we can begin creating `Course.java`.

### 2.1 Instance Variables

First, in the begining of the class (so right below `public class Course.java`), create these 5 instance variables. Make sure the access modifiers for the instance variables are set so that access to the variables is limited to just this object.
*Hint:* Look at page 189 of the textbook for an example.

### 2.2 Constructors

#### 2.2.1 Empty Constructor

Next, create an empty constructor. Remember, an empty constructor does not take in any parameters. The role of the empty constructor is to create an instance of the class where all the instance variables are set to the defaults.

THerefore, in your empty constructor, initialize values for all the instance variables.

#### 2.2.2 Value Constructor

Next, create a value constructor that takes in 5 parameters and sets the instance variables to the values in the parameters.

**Make sure** to use the same variables names for your parameters as the instance variables. In **this** case, dont forget to use a **special keyword** that allows you to access the instance variables when **shadowing** occurs.

*Hint:* Look at section 11.3 of the textbook

### 2.3 Getters and Setters

Next, for each of the instance variables, create a corresponding `getter` and `setter` method. 

**Testing:** In the main method, create a new `Course` object, then use the `getters` to test that the new `Course` object contains all the values specified when you create the new `Course` object.


<b style="color:Red;">DO NOT GO ON IN THIS LAB WITHOUT SHOWING AN INSTRUCTOR YOUR ANSWERS SO FAR. OTHERWISE YOU WILL NOT GET FULL POINTS FOR THIS LAB!</b>

<b style="color:Red;">MAKE SURE YOU WROTE OUT ALL OF YOUR ANSWERS TO ALL OF THE QUESTIONS ABOVE.</b>

### 2.4 toString()

Dont forget that every class needs to have a `toString()` method that returns a string representation of the object. Now implement your `toString()` method.

Then, in `main`, call `toString()` on your object and print out the object.

### 2.5 equals()

If we want to check if two objects are equal to each other, recall that we cannot use `==`. 

**Question 2.5.1:** What does `==` compare?

*Hint:* Look at section 11.7 of the textbook


<br><br><br><br><br>

Instead, we can use the `equals` method to check if two objects are **equivalent**.

Now, create an instance method called `equals()` that takes in another `Course` object as a parameter. The method should return `true` if the values in the objects' instance variables are equivalent. 

Finally, test `equals()` in your main method. The easiest way to test this is to create two empty objects (using the empty constructor) and then compare them.


<b style="color:Red;">DO NOT GO ON IN THIS LAB WITHOUT SHOWING AN INSTRUCTOR YOUR ANSWERS SO FAR. OTHERWISE YOU WILL NOT GET FULL POINTS FOR THIS LAB!</b>

<b style="color:Red;">MAKE SURE YOU WROTE OUT ALL OF YOUR ANSWERS TO ALL OF THE QUESTIONS ABOVE.</b>

## 3. Schedule

Now that we implemented a `Course` class, we can implement a `Schedule` class. 

Create an empty file called `Schedule.java`

### 3.1 Instance Variables.

**Question 3.1.1:** Besides for a list of `Courses`, what else might a `Schedule` have?



<br><br><br><br><br>



 Next, at the top of the class, declare your instance variables, including an array of `Courses` (dont initialize it).

### 3.2 Constructor

Next, create a `Constructor` method. The parameters in the constructor should be values for the instance variables. One of the parameters should indicate how
many `Courses` are in the schedule. 

**Question 3.2.1:** How will you use the number of `Courses` in the schedule in your constructor?

<details><summary><b style="color:DodgerBlue;">Hint</b></summary>

```
What instance variable are you using to represent that 
```

</details> 
<br><br><br><br>

**Now,** implement the constructor

### 3.3 toString()

Implement a `toString()` method that returns a string representation of the schedule. 

In the string representation, Id recommend the string first containing information about the schedule, e.g. the name of the schedule/student, the semester, or whatever instance variables you can up with above. Then, I'd have one new line in the string for each course.

Recall: you can create a string representation for each course by using the course object's `toString()` method.

### 3.4 Adding courses

Next, we need a way to add a course to our schedule.

Implement an instance method called `addCourse()` that takes in a course as a parameter and adds the course to the end of the list of courses. For example, if there are no courses in the list, then we would add a new course to the first slot of the array. If there are 3 courses, we would add the new course to the 4th slot of the array.

If there is no more room for a course, the method should not override any existing courses. Instead the method should print out a message saying that it cant add the new course and then return `false`.

Based on this last instruction, what do you think the return type of `addCourse()` should be? Additionally, what should the method return after successfully adding a course. 

Finally, in `main()`, test `addCourse`.

<b style="color:Red;">DO NOT GO ON IN THIS LAB WITHOUT SHOWING AN INSTRUCTOR YOUR ANSWERS SO FAR. OTHERWISE YOU WILL NOT GET FULL POINTS FOR THIS LAB!</b>

<b style="color:Red;">MAKE SURE YOU WROTE OUT ALL OF YOUR ANSWERS TO ALL OF THE QUESTIONS ABOVE.</b>

### 3.5 Creating courses from a file
If you recall from the begining of the lab, we provided a file that contains a list of courses. 

Look at any of the lines in `schedule.csv`. 

**Question 3.5.1:** Look closely, what character are we using to seperate the different properties of a course? 

<details><summary><b style="color:DodgerBlue;">Answer</b></summary>

We are using a comma. **csv**, stands for comma seperate value. In **csv** files, each value in a row is seperated by a comma.

</details> 

<br><br><br>

That means, we can use the `.split()` method to convert each row into an array of Strings. 

#### 3.5.1 Creating one course from a string

Before parsing the file, I'd recommend copying one line from the file and storing it in a string. **Next,** create a static method called `createCourseFromLine()` that takes in a string as a parameter and creates a new course object from that string.

**Hint:** Since some of a `Course`'s instance variables are not `String`s, your method will probably need to convert some `String`s to other types.

#### 3.5.2 addCoursesFromFile()

Now we can create a new instance method called `addCoursesFromFile()`. This method's parameter should be a String that indicates the file name that contains the schedule.

The method should use the `File` class to create a new `File` object and then use a `Scanner` object to  iterate through the file. When iterating through the file, at each line the method should call `createCourseFromLine()` and then `addCourse()`.

### 3.6 Testing and putting it all together

Finally, in the `main` method, create a new `Schedule` object. Then call `addCoursesFromFile()` to add the courses. Finally, print out the `Schedule` object to confirm that everything works.

Congrats, you have completed the lab!

## Wrap up

In today's lab we covered designing classes and working with objects. You gained more practice with splitting Strings and working with files.

### Signing out
Before leaving, make sure your TA/instructor have signed you out of the lab. If you finish the lab early, you are free to go.
