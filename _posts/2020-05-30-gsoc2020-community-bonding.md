---
layout: post
title: "GSoC 2020 with KDE"
description: "Wrapping up the Community Bonding period"
tags: [gsoc, kde]
---

## GSoC 2020 with KDE

The day was the 4th of May. As the hours were passing, some anxiousness
was settling in. I was waiting for the announcement of the list of accepted
projects for Google Summer of Code 2020. It had been one month and four days
of waiting since proposal submission and it was time to face the results.

As the moment arrived, it brought with itself the good news. My project was
accepted by the KDE community and I was given a chance to work with one of
the largest active free software communities :)

{% include image.html path="kde-logo.png" path-detail="kde-logo.png" alt="KDE" %}


### About the Project

KtoBLZCheck is a library to check bank account numbers and bank codes
(BLZ) of German Banks and other international banks. Currently, KtoBLZCheck
uses multiple bankdata files in text format which are
valid at different dates. The data which is regularly retrieved from ​Deutsche
Bundesbank is valid for three months. This leads to a lot of duplication of data.<br>
The idea is to integrate the support for query and generation of SQLite
databases into KtoBLZCheck to replace the text files used currently. This will
avoid duplicate data and enable the support for multiple countries improving
the scope of this library.<br/>
Another task is to create an API for querying these databases, so as to integrate
these databases into other applications.<br/>
The database would also need to be updated on demand so that the applications can
be sure about the results. An API for checking and downloading these updates
would also be implemented. <br/>

> **Mentors** : Ralf Habacker, Thomas Baumgart, Ingo Klöcker

### Community Bonding period

This month was spent on ironing out the details of the project. With the help of
my mentors, I became aware of the possible challenges and started to search for the
possible solutions to figure out a plan for the first phase of the project.

This was also the time to meet my fellow students who were participating in this
program. It was a remarkable experience, interacting with them and talking about
our GSoC projects. I met a lot of talented people here and we hope to be in touch
even after the program ends.

### What's Next?

Currently, this is the Community Bonding period of Google Summer of Code.
This will last till June 1. After this, coding will officially begin.
I am in regular contact with my mentors and I have finalised the details
of the initial work. On the suggestions of my mentors, I have added another
subtask of creating an API for fetching datafiles from the web.

I plan to start my work as soon as the coding period begins and will be updating
my progress on this project during this period through this blog and my KDE GSoC
status report page.

I thank the KDE community for selecting my proposal as a project for Google Summer of Code.
I am super excited to work on this project and learn about software development from my mentors
and the community. This is the first time I will be working so close with an open-source
organisation. <br/>
I look forward to working and learning a lot in the next three months.

### About me

I am Prasun Kumar, a student of Indian Institute of Information Technology,
Guwahati (Assam, India). I am in my 2nd year (4th) semester of Bachelor in
Technology in Computer Science and Engineering.

* My KDE status report page: [Status Report](https://community.kde.org/GSoC/2020/StatusReports/PrasunKumar)
* My GSoC Proposal : [Proposal](https://docs.google.com/document/d/1pMM0cUlPNpzWzlfEZ7XKcHTwJC73EYiYbLoQJRT7Jpc/)