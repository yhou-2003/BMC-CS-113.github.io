---
layout: default
title: Sorting
type: Lab
number: 10
active_tab: lab
release_date: 2023-04-18

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

The main goals for this lab are for you to get more comfortable with sorting algorithms.

### Paired Programming rules

This lab is a **paired programming assignment.** What exactly does that mean? You will be working in pairs on the CS lab computers. Each pair will be working on one computer. One person will be the **driver** and the other person will be the **navigator**. Here is the rule: the **driver** controlls the lab computer, but the **driver** can only type what the **navigator** tells them to type. For this to work well, each pair should be constantly talking among themselves. After each problem, you will switch roles, the navigator will become the driver and the driver will become the navigator.

> **New Partners**
> This week you can switch partners. You will work with your partner this week and next. Your can work with a partner who you have worked with in the past.

### Finishing the lab

Before leaving the lab, make sure you fill out the attendance sheet and go through your answers with a TA or instructor. You will not get full credit otherwise.

## 1. Bubble Sort

In today's lecture we discussed Bubble Sort. We walked through an example together and discussed the algorithm. 

In this part of the lab, you will implement Bubble Sort. But first, we will walk through another example together. Slide 34 form lecture 23 has the psuedocode/algorithm for Bubblesort. I'd recommend you pull it up as a reference.

### 1.1 Example 1

Consider the following array of just 4 numbers:
`9,8,7,6`. We are going to walk through BubbleSort by hand before we start implementing the algorithm.
We will be using a table to track each step of the algorithm and what the array looks like after each step.

**Question 1:** Fill in just the `len` and `j` columns below. `len` represents the variable in the outerloop and `j` represents the variable in the innerloop. Do not fill in any cells in the `array` column yet. 

*Hint:* You might not need every row below.



<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">len</th>
    <th class="tg-0pky">j</th>
    <th class="tg-0pky">array</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky">4</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky">&nbsp;&nbsp;&nbsp;</td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">&nbsp;&nbsp;&nbsp;</td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">&nbsp;&nbsp;&nbsp;&nbsp;</td>
    <td class="tg-0pky"></td>
  </tr>
</tbody>
</table>

<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">len</th>
    <th class="tg-0pky">j</th>
    <th class="tg-0pky">array</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky">4</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky">3</td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky">3</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky"></td>
  </tr>
</tbody>
</table>

</details> 

<br><br><br>



**Question 2:** Now fill in the values in the `array` column. Each value should show what the `array` now looks like after `len` and `j` are specific values

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
.tg .tg-0lax{text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">len</th>
    <th class="tg-0pky">j</th>
    <th class="tg-0pky">array</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky">4</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky"> 8976&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td>
  </tr>
  <tr>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
  </tr>
</tbody>
</table>



<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">len</th>
    <th class="tg-0pky">j</th>
    <th class="tg-0pky">array</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky">4</td>
    <td class="tg-0pky">1<br></td>
    <td class="tg-0pky">8 9 7 6</td>
  </tr>
  <tr>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky">8 7 9 6</td>
  </tr>
  <tr>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky">3</td>
    <td class="tg-0pky">8 7 6 9</td>
  </tr>
  <tr>
    <td class="tg-0pky">3</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky">7 8 6 9</td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky">7 6 8 9</td>
  </tr>
  <tr>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky">6 7 8 9</td>
  </tr>
</tbody>
</table>

</details> 
<br><br><br>
**Question 3:**
How many swaps do you have to make? How many pairs of elements did we consider?

<br><br><br>
<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

we made 6 swaps. 

We have to compare every pair. We compare:
9 to 8, 7, 6
8 to 7, 6
7 to 6

</details> 



### 1.2 Example 2

Now consider the following array of 5 numbers:
`5,10,6,2,7`. We are going to walk through BubbleSort by hand before we start implementing the algorithm.
We will be using a table to track each step of the algorithm and what the array looks like after each step.

**Question 4:** Fill in just the `len` and `j` columns below. `len` represents the variable in the outerloop and `j` represents the variable in the innerloop. Do not fill in any cells in the `array` column yet. 

*Hint:* You might not need every row below or you might need to add rows.



<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">len</th>
    <th class="tg-0pky">j</th>
    <th class="tg-0pky">array</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky">&nbsp;&nbsp;&nbsp;</td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">&nbsp;&nbsp;&nbsp;</td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">&nbsp;&nbsp;&nbsp;&nbsp;</td>
    <td class="tg-0pky"></td>
  </tr>
</tbody>
</table>

<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
.tg .tg-0lax{text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">len</th>
    <th class="tg-0pky">j</th>
    <th class="tg-0lax">array&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">5</td>
    <td class="tg-0lax">1</td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0lax"></td>
    <td class="tg-0lax">2</td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0lax"></td>
    <td class="tg-0lax">3</td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0lax"></td>
    <td class="tg-0lax">4</td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0pky">4</td>
    <td class="tg-0pky">1<br></td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky">2</td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky">3</td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0pky">3</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">2</td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0lax"></td>
  </tr>
</tbody>
</table>
</details> 

<br><br><br>



**Question 5:** Now fill in the values in the `array` column. Each value should show what the `array` now looks like after `len` and `j` are specific values

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
.tg .tg-0lax{text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">len</th>
    <th class="tg-0pky">j</th>
    <th class="tg-0pky">array</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td>
  </tr>
  <tr>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
  </tr>
</tbody>
</table>



<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
.tg .tg-0lax{text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">len</th>
    <th class="tg-0pky">j</th>
    <th class="tg-0pky">array</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">5</td>
    <td class="tg-0lax">1</td>
    <td class="tg-0lax">5 10 6 2 7</td>
  </tr>
  <tr>
    <td class="tg-0lax"></td>
    <td class="tg-0lax">2</td>
    <td class="tg-0lax"><span style="font-weight:400;font-style:normal">5 6 10 2 7</span></td>
  </tr>
  <tr>
    <td class="tg-0lax"></td>
    <td class="tg-0lax">3</td>
    <td class="tg-0lax">5 6 2 10 7</td>
  </tr>
  <tr>
    <td class="tg-0lax"></td>
    <td class="tg-0lax">4</td>
    <td class="tg-0lax">5 6 2 7 10</td>
  </tr>
  <tr>
    <td class="tg-0pky">4</td>
    <td class="tg-0pky">1<br></td>
    <td class="tg-0pky">5 6 2 7 10</td>
  </tr>
  <tr>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky">5 2 6 7 10</td>
  </tr>
  <tr>
    <td class="tg-0pky"> </td>
    <td class="tg-0pky">3</td>
    <td class="tg-0pky">5 2 6 7 10</td>
  </tr>
  <tr>
    <td class="tg-0pky">3</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky">2 5 6 7 10</td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky">2 5 6 7 10</td>
  </tr>
  <tr>
    <td class="tg-0pky">2</td>
    <td class="tg-0pky">1</td>
    <td class="tg-0pky">2 5 6 7 10</td>
  </tr>
</tbody>
</table>

</details> 
<br><br><br>
**Question 6:**
How many swaps do you have to make? How many pairs of elements did we consider?

<br><br><br>
<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

we made just 5 swaps: (5,2), (5,3), (5,4),
(4,2), (3,1) 

We have to compare every pair. We compared:
10 to 5, 6, 2, 7
5 to 6
6 to 2, 7
2 to 5
5 to 6
2 to 5

thus we made 10 comparisons

</details> 

**Question 7:**
When we had an array of size 4, we made 6 comparisons, 
when we had an array of size 5, we made 10 comparisons. 

Imagine we have an array of size *n*. How many comparisons will we have to make?
<br><br><br>
<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

$$\dfrac{n * (n-1)}{2}$$

This is because we compare each element to every other element. thats where we get the $$n(n-1)$$.

We can divide that number by 2 since we just care about comparing each pair. For example, we care about comparing A and B, so if we consider A-B, we dont need to check B-A.

Therefore, the total number of comparisons we need to make is $$\dfrac{n^{2} - n}{2}$$
</details> 

<br><br>

**Question 8:**
In what scenario would we make the fewest number of swaps? In what scenario would we make the most number of swaps?

<br><br><br>
<details><summary><b style="color:DodgerBlue;">Solution</b></summary>
If the list was sorted (in ascending order) then we dont need to make any swaps.

If the list was sorted (in descending order) then we need to swap whenever we compare two items in the list.
</details> 


### 1.3 Implementation time

We have provided starter code in `Bubble.java` for you to implement. You can access the [code here]({{ site.url }}{{ site.baseurl }}/labs/lab10/Bubble.java).

There are two methods for you to implement, `swap()` and `bubbleSort()`.

<br><br><br>
<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

We have provided the solution in BubbleSolution.java. You can access the <a href="{{ site.url }}{{ site.baseurl }}/labs/lab10/BubbleSolution.java">code here</a>.

</details> 





## 2. Selection Sort

In today's lecture we discussed Bubble Sort. We walked through an example together and discussed the algorithm. 

In this part of the lab, you will implement Selection Sort. But first, we will walk through another example together. Slide 69 form lecture 23 has the psuedocode/algorithm for finding the minimum value, slide 37 has the algorithm for selection sort. I'd recommend you pull it up as a reference.

### 2.1 Example 1

Consider the following array of just 4 numbers:
`9,8,7,6`. We are going to walk through SelectionSort by hand before we start implementing the algorithm.
We will be using a table to track each step of the algorithm and what the array looks like after each step.

**Question 9:** Fill in the `startIdx`, `minIdx`, `minVal`, and `array` columns below. `startIdx` represents the variable in the outerloop, `minIdx` represents the index of the smallest value in the remaining parts of the list, `minVal` represents the value at `minIdx`, and `array` represents the list after the minimum value has been moved to the current `startIdx` (if needed).  

*Hint:* You might not need every row below or you might need to add a row.

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
.tg .tg-0lax{text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">startIdx</th>
    <th class="tg-0pky">minIdx</th>
    <th class="tg-0lax">minVal</th>
    <th class="tg-0lax">array                    </th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">0</td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0lax">1</td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0lax">2</td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0lax">3</td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
  </tr>
</tbody>
</table>


<br><br><br>
<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
.tg .tg-0lax{text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">startIdx</th>
    <th class="tg-0pky">minIdx</th>
    <th class="tg-0lax">minVal</th>
    <th class="tg-0lax">array                    </th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">0</td>
    <td class="tg-0lax">3</td>
    <td class="tg-0lax">6</td>
    <td class="tg-0lax">6 8 7 9</td>
  </tr>
  <tr>
    <td class="tg-0lax">1</td>
    <td class="tg-0lax">2</td>
    <td class="tg-0lax">7</td>
    <td class="tg-0lax">6 7 8 9</td>
  </tr>
  <tr>
    <td class="tg-0lax">2</td>
    <td class="tg-0lax">2</td>
    <td class="tg-0lax">8</td>
    <td class="tg-0lax">6 7 8 9</td>
  </tr>
</tbody>
</table>

</details> 

**Question 10:** How many swaps do you have to make? How many pairs of elements did we consider?


<br><br><br>
<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

Just 2 swaps, 6 with 9 and then 7 with 8.

Comparisons, is a bit tricky. We are making comparisons when we find the minIndex. When startIndex is 0, we have to compare 4 elements (9,8,7,6), when startIndex is 1, we have to compare 3 elements (7,8,9). When startIndex is 2, we have to compare 2 elements (8,9). When startIndex is 3, we dont need to compare any elements because the reminaing list of unsorted numbers has just one number. 

In total this is 4 + 3 + 2 = 9

</details> 

### 2.1 Example 2

Consider the following array of 5 numbers:
`5,10,6,2,7`. We are going to walk through SelectionSort by hand before we start implementing the algorithm.
We will be using a table to track each step of the algorithm and what the array looks like after each step.

**Question 11:** Fill in the `startIdx`, `minIdx`, `minVal`, and `array` columns below. `startIdx` represents the variable in the outerloop, `minIdx` represents the index of the smallest value in the remaining parts of the list, `minVal` represents the value at `minIdx`, and `array` represents the list after the minimum value has been moved to the current `startIdx` (if needed).  

*Hint:* You might not need every row below or you might need to add a row.


<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
.tg .tg-0lax{text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">startIdx</th>
    <th class="tg-0pky">minIdx</th>
    <th class="tg-0lax">minVal</th>
    <th class="tg-0lax">array                    </th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">0</td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0lax">1</td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0lax">2</td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0lax">3</td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
    <td class="tg-0lax"></td>
  </tr>
</tbody>
</table>


<br><br><br>
<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
.tg .tg-0lax{text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">startIdx</th>
    <th class="tg-0pky">minIdx</th>
    <th class="tg-0lax">minVal</th>
    <th class="tg-0lax">array: 5, 10, 6, 2, 7</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">0</td>
    <td class="tg-0lax">3</td>
    <td class="tg-0lax">2</td>
    <td class="tg-0lax">2 10 6 5 7</td>
  </tr>
  <tr>
    <td class="tg-0lax">1</td>
    <td class="tg-0lax">3</td>
    <td class="tg-0lax">5</td>
    <td class="tg-0lax">2 5 6 10 7</td>
  </tr>
  <tr>
    <td class="tg-0lax">2</td>
    <td class="tg-0lax">2</td>
    <td class="tg-0lax">6</td>
    <td class="tg-0lax">2 5 6 10 7</td>
  </tr>
  <tr>
    <td class="tg-0lax">3</td>
    <td class="tg-0lax">4</td>
    <td class="tg-0lax">7</td>
    <td class="tg-0lax">2 5 6 7 10</td>
  </tr>
</tbody>
</table>

</details> 

**Question 12:** How many swaps do you have to make? How many pairs of elements did we consider?


<br><br><br>
<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

Just 3 swaps, 2 with 5, 5 with 10, 7 with 10

Comparisons, is a bit tricky. We are making comparisons when we find the minIndex. When startIndex is 0, we have to compare 5 elements, when startIndex is 1, we have to compare 4 elements. When startIndex is 2, we have to compare 3 elements (8,9). When startIndex is 3, we compare 2 elements. When startIndex is 4, we dont need to compare any elements because the reminaing list of unsorted numbers has just one number. 

In total this is 5 + 4 + 3 + 2 = 14

</details> 

<br><br>
SelectionSort also is an quadratic algorithm, meaning that as the size of the list increases, the amount of steps the algorithm will take in the worst case scenario increases  a *squared* amount of times. We will discuss this in more detail on Thursday or next week.

The idea of how long an algorithm will take (or how many steps it must perform) in the worst case scenario is an important concept in Computer Science. It will be covered in detail in Data Structures and Discrete Math!


### 2.3 Implementation time

We have provided starter code in `Selection.java` for you to implement. You can access the [code here]({{ site.url }}{{ site.baseurl }}/labs/lab10/Selection.java).

There are two methods for you to implement, `swap()` and `selectionSort()`.

<br><br><br>
<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

We have provided the solution in SelectionSolution.java. You can access the <a href="{{ site.url }}{{ site.baseurl }}/labs/lab10/SelectionSolution.java">code here</a>.

</details> 

## Wrap up

In today's lab we covered two sorting algorithms. This will help you for HW09.

### Signing out
Before leaving, make sure your TA/instructor have signed you out of the lab. If you finish the lab early, you are free to go.
