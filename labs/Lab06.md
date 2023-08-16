---
layout: default
title: Exceptions & Files
type: Lab
number: 06
active_tab: lab
release_date: 2023-03-14

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

_credit: Dianna Xu_

## Objectives:

The main goals for this lab are for you to get more comfortable working with files and understanding Exceptions, In this lab we are going to implement some terminal programs that work with text files! 

### Paired Programming rules

This lab is a **paired programming assignment.** What exactly does that mean? You will be working in pairs on the CS lab computers. Each pair will be working on one computer. One person will be the **driver** and the other person will be the **navigator**. Here is the rule: the **driver** controlls the lab computer, but the **driver** can only type what the **navigator** tells them to type. For this to work well, each pair should be constantly talking among themselves. After each problem, you will switch roles, the navigator will become the driver and the driver will become the navigator.

> **NEW Partners**
> You **must** work with a **new partner ** this week. This should be someone you havent worked with yet in a lab this semster. You will be working together for the next 3 weeks. 

### Finishing the lab

Before leaving the lab, make sure you fill out the attendance sheet and go through your answers with a TA or instructor.

## 1. Errors

As you've seen so far this semester, when writing code, you will invariably have syntax errors and the code will not compile until all syntax errors are corrected. 
You've also noticed that once you have a complete program free of syntax errors, programs rarely run
correctly the first time. 

Even after we fix all logical errors, sometimes when running the program it might crash! For example,You might an off-by-one-errors that causes an `ArrayIndexOutofBounds` error.

### 1.1 Writing Code That Crashes!

**Question 1.1:** Create the following program:

```
public class Crash1 {
	
		public static void main(String[] args) {
		
			int[] a = { 10, 20, 30, 40, 50 };
			for (int i = 0; i < a.length; i++) {
				System.out.println(a[i]);
			}
			System.out.println("Done printing the array!");
		}
}
```

Run the program. This is the correct version. 
Below, write out the output of the program:

<details><summary><b style="color:DodgerBlue;">Answer</b></summary>

```
10
20
30
40
50
Done printing the array!
```

</details> 



<br><br><br><br><br><br>

### 1.2 Breaking it!

Now, let’s break it. Ready?

Change the termination condition in the for-loop to the following:
`i <= a.length`

**Question 1.2:**Can you tell what’s going to happen? Why? (Make sure to write out your answer below)

<br><br><br><br>

Run the program and then write the output below:
<br><br><br><br><br>

<details><summary><b style="color:DodgerBlue;">Answer</b></summary>

```
10
20
30
40
50
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 5
at Crash1.main(Crash1.java:8)
```

</details>


You got a runtime error in your program. After printing out the last element in the array, it got the error.
Why? Did you guess correctly?


Let’s try and parse the error message. Runtime errors are typically called ***exceptions*** in Java. If you read
the first line, it is telling you that there was an exception in the thread “main”. What is a *thread*? This is a
technical term. In computing, each set of instructions running on the computer is called a *thread*. At any
point there could be several threads of computation running. So, this exception occurred in the “main”
thread (that is your `main()` method).

Further, it is also telling you that the error, or exception, that occurred is a known type of error. It is
called `java.lang.ArrayIndexOutOfBoundsException.` Just by looking at the name, you should be
able to guess that this is an object of some kind. It belongs to the `java.lang` class and its name is:

`ArrayIndexOutOfBoundsException`

And, that is exactly the error we introduced when we changed the termination test. We let the loop run
beyond the bounds of the array, to an index 5, which in an array of five elements does not exist. Right?

In fact, the index number that caused the exception is also shown (:5), as is the line at which the
exception occurred:

`Crash1.main(Crash1.java:8)`

That is, at line 8 of Crash1.java (your source code) was where you tried to access an array element that
doesn’t exist. This is line 8:

`System.out.println(a[i]);`

Since `i=5` and `a[5]` does not exist, you get the `ArrayIndexOutOfBoundsException`.
Java includes an elaborate set of classes that define various exceptions. Moreover, when these
exceptions occur (technically, when an exception is raised/thrown) it also gives you an option to write
your programs so that you include code to handle (or catch) some exceptions. This is called ***exception
handling***. In many instances, as you will soon see, you are required to provide code for handling
anticipated exceptions. We will learn how to handle exceptions next.

### 1.3 Exceptions & Runtime Errors

Java has a class called `Exception` and several dozen types of exceptions that can arise are defined as
subclasses of the Exception class. Some of the errors occur during input/output (for example a misplaced input file) and others during the course of executing
your logic (for example an out of bounds array access, or trying to access an object before instantiation,
etc.). Sometimes, it is possible to recover from an error and to do this Java provides a way for you to
detect and specify corrective measures. 

Java provides a `try-catch` statement block to detect and handle exceptions. Its basic syntax is shown
below:

```
try {
 	some code during whose execution errors may occur
} catch (<some exception> <variable>) {
 	some corrective action you could perform
}
```

Essentially, you enclose the code that may (or is likely to) result in an error in a `try-catch` statement
block as shown. If, in the course of executing the surrounded code an exception occurs, the code
included in the `catch`-block is executed. The following exercise illustrates this.

Create a new program with the code shown below.

```
import java.util.Scanner;

public class Crash2 {
 	public static void main(String[] args) {
		Scanner in = new Scanner(System.in);
			while (true) {
				System.out.print("Enter a number: ");
				String line = in.nextLine();
				int data = Integer.parseInt(line);
				System.out.println("Square root of " + data + " is " + Math.sqrt(data));
			}
 	} // main()
} // end of class
```

The code shown above repeatedly prompts the user for a number and then computes and outputs the
square root of that number. The number is actually input as a string, as you have learned earlier. You
use the Java function:

`Integer.parseInt(<string>)`

to extract a number from the input string. There is also a `Double.parseDouble()` if you want to
accept floating-point input.

The while-loop ensures that the program does this forever. Run the program and enter some numbers
to try it out. Enter only positive integer values at first. Then, after a few successful tries, enter something
that’s not a number. 

**Question 1.3** What happens? What error is thrown?
<br><br><br>

<details><summary><b style="color:DodgerBlue;">Answer</b></summary>
The program crashes with the following error:

```
Exception in thread "main" java.lang.NumberFormatException: null
at java.lang.Integer.parseInt(Integer.java: 454)
at java.lang.Integer.parseInt(Integer.java 527)
at InputErrorDemo.main(Crash2.java:10)
```
</details>


Can you guess why that happens?

Notice, the error is occurring at line 10 of your program. That is the line where you are trying to convert
the string to an integer. The exception flagged, `java.lang.NumberFormatException`, is
indicating that there was a problem in the number format: it wasn’t a number that you entered.
To handle this, we need Java’s exception handling.

### 1.4 The `try-catch` Statement

**TODO:** Read and understand the code below to see how a `try-catch` block is structured, and used.
Modify your program to work this way and experiment with it.

```
import java.util.Scanner;
public class Crash2 {
	public static void main(String[] args) {
		while(true) {
 			Scanner in = new Scanner(System.in);
 			try {
 				System.out.print("Enter a number: ");
 				String line = in.nextLine();
 				double data = Double.parseDouble(line);
 				System.out.println("The square root of " + data + " is " + Math.sqrt(data));
 			}
 			catch(NumberFormatException e) {
 				System.out.println("That's not a number!");
 			}
 		} // end while
 	} // end main
} // end class
```

Run the above program several times. Enter integer values, floating point values, as well as other
garbage. Notice how your program is now robust enough to do the right thing when a number is input,
and recovers in situations when nothing or some non-numeric input is provided. It does not crash!

Now that we have covered Exceptions and how to catch them, we can begin working with files.

<b style="color:Red;">DO NOT GO ON IN THIS LAB WITHOUT SHOWING AN INSTRUCTOR YOUR ANSWERS SO FAR. OTHERWISE YOU WILL NOT GET FULL POINTS FOR THIS LAB!</b>

<b style="color:Red;">MAKE SURE YOU WROTE OUT ALL OF YOUR ANSWERS TO ALL OF THE QUESTIONS ABOVE.</b>

## 2. Download a file
For the remaining of this lab, you are going to compute statistics about a book. Go to Project Gutenberg online and choose a book to download. Then run `wget` to download the book as a txt file and save the book in a text file called `book.txt`.

For example, if you are downloading Les Misérables, you would run `wget https://www.gutenberg.org/files/135/135-0.txt > book.txt`

Make sure to do this before moving on.
If you are stuck or unsure how to find a txt file of a book on Project Gutenberg, ask the lab instructor.

## 3. cat

`cat` is a terminal program that will print out the contents of the file. 

**Question: 3.1** What is the official description of `cat`. You can use the `--help` or `man` commands

**SOLUTION:** Concatenate FILE(s) to standard output

<br><br><br><br><br>

### Stub

Lets begin by creating a file called `Cat.java`. 
Since the program will not be so large, we can work
completely in the main method.

`cat` works by a user passing in a command line argument that is the name of a file.

**Question: 3.2** Modify your main method so that it prints out the command line argument. If the user does not provide a command line argument, then make sure to print out a message to the user and have the program terminate. 

<b style="color:Red;">DO NOT GO ON IN THIS LAB WITHOUT SHOWING AN INSTRUCTOR YOUR ANSWERS SO FAR. OTHERWISE YOU WILL NOT GET FULL POINTS FOR THIS LAB!</b>

<b style="color:Red;">MAKE SURE YOU WROTE OUT ALL OF YOUR ANSWERS TO ALL OF THE QUESTIONS ABOVE.</b>


### Algorithm

Before implementing the program, its important to come up with your algorithm. Below are some steps for a simple high-level algorithm for how `cat` works. 

**Question: 3.3: Re-order the steps below so that they are correct**


2. Repeat previous steps
3. Print out a line of the file
4. Open the file
2. Read a line in the file

### Implementation

Now that we have our algorithm, we can begin to implement it.

#### 3.1 Opening the file

**TODO:** In your main method in `Cat.java`,
create a new `Scanner` object. Instead of having your Scanner object read in from `System.in`, it should read data from the file that the user specified. 

*Hint:* You can use the code from today's class where we created a new `File` object and passed that into `new Scanner(...)`.  

<details><summary><b style="color:DodgerBlue;">Answer</b></summary>


```
import java.util.Scanner;
import java.io.File;

public class Cat {

	public static void main(String[] args) {
		File input = new File(args[0]);
		Scanner sc = new Scanner(input);
	}
}
```

</details> 

**Question 3.4:** What happens when you run the code now? What error do you see? What do you think it means?

<br><br><br>

<details><summary><b style="color:DodgerBlue;">Answer</b></summary>
unreported exception FileNotFoundException; must be caught or declared to be thrown. 

</details>


Lets fix this by simply adding `throws FileNotFoundException` to the main method.
So the main method should look like:

`public static void main(String[] args) throws FileNotFoundException`.

#### 3.2 Reading and printing a line
Before we worry about the loop, lets first figure out what we want to do in each iteration of the loop.

Based on the algorithm above, we want to to read in a line from the file and then print out that same line.

**TODO:** In your main method, now read in a line from the file (using your scanner object) and then print out the line.

#### 3.3 Looping through the file

Since we want to print out the entire file, we will now need to loop through each line of the file. 

**Question 3.5:** Which type of loop do you think we will want to use here? A `for` loop or a `while` loop? Why?

<br><br><br>

<details><summary><b style="color:DodgerBlue;">Answer</b></summary>
While loop since we dont know how long the file will be.
</details>

**Question 3.6:** When do we want to stop our loop?
<br><br><br>
<details><summary><b style="color:DodgerBlue;">Answer</b></summary>
When we reached the end of the file, i.e. when there are no more lines.
</details>

**Question 3.7:** What Scanner method will do that for us? Feel free to look at the list of Scanner methods here: https://docs.oracle.com/javase/7/docs/api/java/util/Scanner.html#method_summary

<br><br><br>
<details><summary><b style="color:DodgerBlue;">Answer</b></summary>
hasNextLine()
</details>


**TODO:** Now that we have the stop condition, add the loop to your `main()`. Make sure to put the code from the previous section (i.e. the code that reads in a line and then prints it out) inside your loop.

#### 3.4 Testing your implementation

Now its time to test your implementation. 

**TODO**: First create a simple text file called `simple.txt`. Write two lines in the file.
Then run `java Cat simple.txt` and confirm that the program prints out the contents of the text file.


**TODO:** Now run `java Cat book.txt` to see the contents of the book that you downloaded.


**TODO:** Now, run `java Cat nonExistantFile.txt`. 

**Question 3.8:** What happens when the program tries opening this file called `nonExistantFile.txt`?

<br><br><br>
<details><summary><b style="color:DodgerBlue;">Answer</b></summary>
We get a runtime error. Specfically that the file is not found.
</details> 

#### 3.5 Adding `try-catch` block

We'd rather not have our programs crash when the user puts in faulty input. 

**TODO:** Put your code in your main method in a `try` block. Then below create a `catch` block where you print out a message to the user and terminate the program.

The catch statement should look like: `catch (FileNotFoundException e)` 

**TODO:** Now, run `java Cat nonExistantFile.txt` and the program should not crash.

This concludes `Cat.java`. Now we have a working java implementation of the basic functionality of the `cat` program.

We have also included a correct implementation here as well: <details><summary><b style="color:DodgerBlue;">Cat.java</b></summary>

```
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class Cat {
	
	public static void main(String[] args) {

		try {
 			// Create a new Scanner for the input file
			Scanner sc = new Scanner(new File(inFileName));
			while (sc.hasNextLine()) { // test if there is a line to read
				// read the next line
				String line = sc.nextLine();
				// output it to Console
				System.out.println(line);
				}
			// Close the input stream
			input.close();
		} // end try
		catch (FileNotFoundException e) {
			System.out.println("Error in opening the file:" + inFileName);
			return;
		} // end catch
 	} // end main
}
```

</details> 

<b style="color:Red;">DO NOT GO ON IN THIS LAB WITHOUT SHOWING AN INSTRUCTOR YOUR ANSWERS SO FAR. OTHERWISE YOU WILL NOT GET FULL POINTS FOR THIS LAB!</b>

<b style="color:Red;">MAKE SURE YOU WROTE OUT ALL OF YOUR ANSWERS TO ALL OF THE QUESTIONS ABOVE.</b>

## 4. wc

`wc` is another command line program that is useful when working with text documents. 

**Question 4.1:**  What does `wc` do?

<br><br><br>
<details><summary><b style="color:DodgerBlue;">Answer</b></summary>
It pints out the number of words, line, and characters.
</details>

In this part of the lab we will implement `wc` in java.

**TODO:** Copy `Cat.java` to a new file called `WC.java`. You can run `cp Cat.java WC.jva` to do this.

Now, modify WC.java so that instead of printing out the contents of a file, it prints out three pieces of information:

1. the number of words in the file
2. the number of lines in the file
3. the number of characters in the file

Defining a word is actually more complicated that we might think. For example, how many words is `don't`. There's good reason to say its just 1 word, and good reason to say its just 2 words. For the sake of this assignment, we will define a word as a run of characters between an empty space. For example, `"hello` would be considered 1 word.

### 4.1 Algorithm

Before begining to code your solution, write out three  algorithms:

1. algorithm for counting the number of words
2. algorithm for counting the number of lines
3. algorithm for counting the number of characters.

Then try to combine those 3 seperate algorithms into one algorithm.

<br><br><br>

### 4.2 Implementation

Now you can begin to modify `WC.java` to implement your algorithm.


## Wrap up

In todays lab we covered exceptions and working with files. 


### Signing out
Before leaving, make sure your TA/instructor have signed you out of the lab. If you finish the lab early, you are free to go.
