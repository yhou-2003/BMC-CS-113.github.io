---
title: Computer Science I - CS113 - Bryn Mawr College
layout: default
img: <!-- turk-engraving-detail -->
img_link: <!-- http://en.wikipedia.org/wiki/The_Turk -->
caption: <!--An engraving of the Mechanical Turk, the 18th century chess-playing automaton -->
active_tab: main_page 
---


This is an introduction to the discipline of computer science, suitable for those students with a mature quantitative ability. This fast-paced course covers the basics of computer programming, with an emphasis on program design, problem decomposition, and object-oriented programming in Java. Graduates of this course will be able to write small computer programs independently; examples include data processing for a data-based science course, small games, or estimating likelihood of probabilistic events, etc.. No computer programming experience is necessary or expected. Students are required to register for a weekly lab.

<!-- Display an alert about upcoming homework assignments -->
{% capture now %}{{'now' | date: '%s'}}{% endcapture %}
{% for page in site.pages %}
{% if page.release_date and page.due_date %}
{% capture release_date %}{{page.release_date | date: '%s'}}{% endcapture %}
{% capture due_date %}{{page.due_date | date: '%s'}}{% endcapture %}
{% if release_date < now and due_date >= now %}
<div class="alert alert-info">
<a href="{{page.url}}">{{ page.title }}</a> has been released.  
{% if page.deliverables %}
The assignment has multiple deliverables.
{% for deliverable in page.deliverables %}
The {{deliverable.description}} is due before {{ deliverable.due_date | date: "%I:%M%p" }} on {{ deliverable.due_date | date: "%A, %B %-d, %Y" }}.  
{% endfor %}
{% else %}
It is due before {{ page.due_date | date: "%I:%M%p" }} on {{ page.due_date | date: "%A, %B %-d, %Y" }}.
{% endif %}
</div>
{% endif %}
{% endif %}
{% endfor %}
<!-- End alert for upcoming homework assignments -->


<!--
<div class="alert alert-info" markdown="1">
Check out the [excellent final projects](http://crowdsourcing-class.org/final-projects-2016.html) from last year's class.
</div>
-->


Course number
: CMSC B113 - students from all majors are welcome!

Instructor
: [Adam Poliak](http://azpoliak.github.io)

Teaching Assistants
: [Course Staff](staff.html) 

Website 
: [https://cs.brynmawr.edu/cs113/](https://cs.brynmawr.edu/cs113/)

Discussion Forum
: [Piazza](https://piazza.com/brynmawr/spring2023/cs113)

Time and place
: Spring 2023, TTH 12:55-2:15pm, Location: Park 338
: Lab T: 2:25-3:45pm

Office Hours
: <a href="{{ site.url }}{{ site.baseurl }}/office-hours.html">Times</a>

Prerequisites
: None - no prior programming background is required

Course Readings
: Each lecture has an accompanying chapter/section of the [textbook](https://cs.brynmawr.edu/cs113/textbook)
: Some lectures will have accompanying optional reading related to the lecture's topic

Grading
* Homeworks: 29%
* Labs: 7%
* Midterms: 25%
* Final: 34% 
* Participation: 5%


Late day policy
: As a general rule, no late homework will be accepted.
<br>
See the <a href="{{ site.url }}{{ site.baseurl }}/policies.html">Policies</a> for more details.

<!--#### Acknowledgments-->
