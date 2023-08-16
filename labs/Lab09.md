---
layout: default
title: Midterm II review
type: Lab
number: 09
active_tab: lab
release_date: 2023-04-11

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

## 1. Flow of Execution

```
  1 class Bounds {
  2    private int min;
  3    private int max;
  4 
  5    public Bounds(int min, int max) {
  6       this.min = min;
  7       this.max = max;
  8       // A) Draw the stack diagram here
  9    }
 10 
 11    public void extend(Bounds other) {
 12       if (other.min < this.min) {
 13          this.min = other.min;
 14       }
 15       if (other.max > this.max) {
 16          this.max = other.max;
 17       }
 18       // C) Draw the stack diagram here
 19    }
 20 
 21    public String toString() {
 22       return "[" + this.min + ", " + this.max + "]";
 23       // B) Draw the stack diagram here
 24    }
 25 
 26    public static Bounds Add(Bounds a, Bounds b) {
 27       int min = a.min + b.min;
 28       int max = a.max + b.max;
 29       // D) Draw the stack diagram here
 30       return new Bounds(min, max);
 31    }
 32 
 33    public static void main(String[] args) {
 34       Bounds b1 = new Bounds(-4, 7);
 35       Bounds b2 = new Bounds(2, 9);
 36       System.out.println("Bounds 1: " + b1);
 37       System.out.println("Bounds 2: " + b2);
 38 
 39       b1.extend(b2);
 40       System.out.println("Extended: " + b1);
 41 
 42       Bounds c = Bounds.Add(b1, b2);
 43       System.out.println("Add: " + c);
 44       // E) Draw the stack diagram here
 45    }
 46 }
```

### 1.1 Stack Diagrams
- A)  Draw the stack diagram for the first call to the Bounds constructor in main 
- B) Draw the stack diagram for the first call to the toString() in main 
- C) Draw the stack diagram for the call to extend() in main 
- D) Draw the stack diagram for the call to Add() in main 
- E) Draw the stack diagram at the end of main 

### 1.2 Execution

Imagine we ran this program called `Bounds`. Below, write down the lines numbers in the order that they are executed.


<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

```
['6', '7', '34', '6', '7', '35', '22', '36', '22', '37', '16', '39', '22', '40', '27', '28', '6', '7', '42', '22', '43']
```

</details> 




### 1.3 Output
What is the output of the above program?

<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

```
Bounds 1: [-4, 7]
Bounds 2: [2, 9]
Extended: [-4, 9]
Add: [-2, 18]
```

</details> 



## 2. Search

### 2.1 Binary Search

#### 2.1.1 Tracing Binary Search 1

For each iteration of the loop in `binarySearch(int x, int[] lst)`, show the index values for low, high, and mid, and the value stored at location mid. What will be returned by this function call?

```
int x = 67;
int[] lst = {10, 12, 14, 21, 37, 44, 45, 46, 58, 67, 99};
            0   1   2   3   4   5   6   7   8   9  10

low | high | mid | L[mid]
- - - - - - - - - - - - -
    |      |     |
    |      |     |
    |      |     |
    |      |     |
```

<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

```
low | high | mid | L[mid]
- - - - - - - - - - - - -
 0   |  10    |  5   |  44
 6   |  10    |  8   |  58
 9   |  10    |  9   |  67
```

</details> 

#### 2.1.2 Tracing Binary Search 2

For each iteration of the loop in `binarySearch(int y, int[] lst)`, show the index values for low, high, and mid, and the value stored at location mid. What will be returned by this function call?

```
int y = 4;
int[] lst = [10, 12, 14, 21, 37, 44, 45, 46, 58, 67, 99];
            0   1   2   3   4   5   6   7   8   9  10

low | high | mid | L[mid]
- - - - - - - - - - - - -
    |      |     |
    |      |     |
    |      |     |
    |      |     |
```

<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

```
low | high | mid | L[mid]
- - - - - - - - - - - - -
 0   |  10   |  5   |  44
 0   |  4    |  2   |  14
 0   |  1    |  0   |  10
 0   |  0    |  0   |  10
 0   |  -1   |      | 
```

</details> 

### 2.2 Linear Search

#### 2.2.1 indexOfLargest
Write a function to return the index of the largest item in a given list.

```
// Input:  An array of integers
// Returns: The index of the largest item in the list,
//    -1 if the list is empty

int indexOfLargest(int[] ls) {
   // complete this function
}
```

<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

```
 public static int indexOfLargest(int[] ls) {
    if (ls.length == 0) {
      return -1;
    }
    int idx = 0;
    int max = ls[0];

    for (int i = 1; i < ls.length; i++) {
      if (ls[i] > max) {
        max = ls[i];
        idx = i;
      }
    }
    return idx;
  } 
```

</details> 

 

#### 2.2.2 indexOfMode
Write a function to return the first index of the item that appears the most in a given list. For this problem you can assume that there is just one mode in a list. To keep things easier, you can also assume that there are only positive values in our list.

```
// Input:  An array of integers
// Returns: The first index of the item in the list that appears the most frequently,
//    -1 if the list is empty

int indexOfMode(int[] ls) {
   // complete this function
}
```

<details><summary><b style="color:DodgerBlue;">Hint 1</b></summary>

```
First we need to keep track of how many times each number appeared in the list. The only data structure we can use so far in this class is an array. 
How might we use an array to keep track of each item in the list? (answer is in Hint 2)
```

</details> 

<details><summary><b style="color:DodgerBlue;">Hint 2</b></summary>

```
Each index in the array can indicate how many times a number appeared in the list. But, how long should the list be? (answer is in Hint 3)
```

</details> 


<details><summary><b style="color:DodgerBlue;">Hint 3</b></summary>

```
The length of the array should be the range of possible values in our list. How can we compute this range? (Answer is in Hint 4). 
```

</details> 


<details><summary><b style="color:DodgerBlue;">Hint 4</b></summary>

```
We can compute the range by finding the the largest value in our list. Let's go ahead and make helper functions to find the largest values in a list. Now we can make a new array that keeps track of how many times each number appeared.

Next, we can go ahead and update the values in the array that keeps track of how many times a number appears. In turn, if the value at index i is 10, that means that i appeared 10 times in our original list. 

Next, we can find the index of our array that has the largest value. That index will be the mode.

However, the problem does not ask us to just find the mode, it asks us to find the first index of the mode. THerefore, we now need to iterate through the original list until we find the first occurence of the mode. 
```

</details> 


<details><summary><b style="color:DodgerBlue;">Solution</b></summary>

```
  public static int maxValue(int[] ls) {
    int max = ls[0];

    for (int i = 1; i < ls.length; i++) {
      if (ls[i] > max) {
        max = ls[i];
      }
    }
    return max;
    
  }

  public static int firstIndex(int n, int[] ls) {
    for (int i = 0; i < ls.length; i++) {
      if (ls[i] == n) {
        return i;
      }
    }
    return -1;
  }

  public static int indexOfMode(int[] ls) {
    int max = maxValue(ls);
    int[] counts = new int[max+1];

    for (int i = 0; i < ls.length; i++) {
      counts[ls[i]] += 1;
    } 
    int mode = indexOfLargest(counts);

    return firstIndex(mode, ls);
  }
```

</details> 


#### 2.2.3 modeChar in String

Now, imagine we asked you to find the most common character in a String. 

Below, write out an algorithm to solve this.

<br><br><br>

## Wrap up

In today's lab we covered searching and reading code. This should help prepare you for midterm 2.

### Signing out
Before leaving, make sure your TA/instructor have signed you out of the lab. If you finish the lab early, you are free to go.
