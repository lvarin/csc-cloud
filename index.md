---
title: CSC Cloud Course
author: CSC Training
---

CSC training course for efficient use of CSC's cloud, which mainly
include computing resourses such as virtual machines and containers
as well as object storage resources in a scalable, automated, and
on-demand fasion.

TO whom: The target audience for this course includes researchers and IT professionals who aim to build and manage their research and education infrastructure and IT solutions in the cloud.

# Course pre-requirements

To succeed in this course, you should be familiar with the following:

- Basic operating systems and networking concepts
- The [Linux command line](https://github.com/csc-training/linux-1/tree/ThomasZ), web servers, and text editors


# Lectures

Lectures as HTML slides. Use cursor keys or click left/right side of
the slide to change it. You can print the slides to PDF with Chrome,
just tweak the print settings a bit.

* Virtual Machines

{% for slide in site.lectures %}
  - [{{ slide.title }}]({{ slide.url | relative_url }})
{% endfor %}

* Containers

{% for slide in site.lectures-containers %}
  - [{{ slide.title }}]({{ slide.url | relative_url }})
{% endfor %}

# Exercises

Practical exercises supplement and build upon the introductory theory slides on topics related to the course. 

* Virtual Machines

{% for exercise in site.exercises %}
  - [{{ exercise.title }}]({{ exercise.url | relative_url }})
{% endfor %}

* Containers

{% for exercise in site.exercises-containers %}
  - [{{ exercise.title }}]({{ exercise.url | relative_url }})
{% endfor %}

# Extras

{% for extra in site.extras %}
- [{{ extra.title }}]({{ extra.url | relative_url }})
{% endfor %}
