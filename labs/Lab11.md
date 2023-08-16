---
layout: default
title: Runtime
type: Lab
number: 11
active_tab: lab
release_date: 2023-04-25

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

The main goals for this lab are for you to get more comfortable with sorting algorithms and runtime analysis.

### Paired Programming rules

This lab is a **paired programming assignment.** What exactly does that mean? You will be working in pairs on the CS lab computers. Each pair will be working on one computer. One person will be the **driver** and the other person will be the **navigator**. Here is the rule: the **driver** controlls the lab computer, but the **driver** can only type what the **navigator** tells them to type. For this to work well, each pair should be constantly talking among themselves. After each problem, you will switch roles, the navigator will become the driver and the driver will become the navigator.

> **Partners**
> You will work with your partner from last week. 

### Finishing the lab

Before leaving the lab, make sure you fill out the attendance sheet and go through your answers with a TA or instructor. You will not get full credit otherwise.

## 1. Run time analysis

For the following methods, how many *steps* are required for each of the following? Classify each one 
as either:

- O(N)
- O($N^2$)
- O(log(N)) 
- O(N log(N))
- or O(1)

### 1.1 Example 1

```
int N = getInputSize();
for (int i = 0; i < N; i++) 
{
    for (int j = 0; j < N; j++) 
    {
        println(i, j);
    }
}
```

<br><br>

### 1.2 Example 2

```
int N = getInputSize();
while (N > 1)
{
    print(N)
    N = N/2
}
```
<br><br>

### 1.3 Example 3

```
int N = getInputSize();
for (int i = 0; i < N; i++)
{
    for (int j = 0; j < 10; j++) 
    {
        print(i*j);
    }
}
```
<br><br>

## 2. Sorting

### 2.1 oneLoop 
Consider the following function, `oneLoop(int[] L)`, which is similar to 
the inner loop from bubble sort:

```
void oneLoop(int[] L)
{
   for (int j = 0; j < L.length()-1; j++) 
   {
      if (L[j] > L[j+1])
      {
         int tmp = L[j+1];
         L[j+1] = L[j];
         L[j] = tmp;
      }
   }
}
```

**Question:** Suppose we run `oneLoop` on the list `L={17,4,19,3,11,8}`. What are
the new contents of `L`?

<br><br><br>

**Question:** Suppose we run `oneLoop` on the list `L={8,11,3,19,4,17}`. What are
the new contents of `L`?

<br><br><br>

### 2.2 Selection Sort

**Question:** Show how the list `L={17,4,19,3,11,8}` would be changed 
after selection sort does its first 1 swap:

<br><br><br><br>

**Question:** Show how the list `L={17,4,19,3,11,8}` would be changed 
after selection sort does its first 2 swaps:

<br><br><br><br>

**Question:** Show how the list `L={17,4,19,3,11,8}` would be changed 
after selection sort does its first 3 swaps:


## Wrap up

In today's lab we covered run time and reviewing selection sort algorithms. This will help you for HW09 and the midterm.

Great job on finishing the final lab of the semester! You've accomplished a lot this semester and should be very proud of yourself! Your course staff is very proud of you all!

### Signing out
Before leaving, make sure your TA/instructor have signed you out of the lab. If you finish the lab early, you are free to go.
