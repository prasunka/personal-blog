---
layout: post
title: "GSoC'20 progress : Phase I"
description: "Wrapping up the first phase of Google Summer of Code"
tags: [gsoc, kde]
---

## GSoC 2020 with KDE

Greetings Reader,

Much to my delight, the first phase of my project for GSoC has completed successully.
All the goals according to my proposal timeline for the first month have been met and
I'm pleased to say that I have passed my first evaluation.

{% include image.html path="passed.png" path-detail="passed.png" alt=":)" %}
*The official email from Google*

Hoping for similar results for the next two evaluations :)

So, what happened in Week 4? Here is a quick overview.

### Week 4

In my project proposal timeline, I have kept this week (which is the last week before
the first evaluation) with lesser work than the rest. I was wary of the fact that some
unforseeable problems may creep up during the project and to account for that I had kept
some time reserved. Fortunately, no such problem showed up and my work proceeded as planned.

So, the major tasks this week were to rewrite and enable the **benchmark** tool and ensure that it
works as a CTest and to make some changes to the **ktoblzcheck** command-line tool to allow the
support of user-supplied bankdata which had become incompatible due to my previous work.

The command line tool was not much work. It just needed to take the argument from the user,
do some error-checking and call the appropriate constructor. Although to make the checking part easier,
I included a method in the public API to help in future.

{% highlight c++ %}

// Returns true if dbname exists and is a valid SQLite file
bool AccountNumberCheck::validSQLite(const std::string &filename){
    char buffer[100];
    std::ifstream db(filename, ios::in | ios::binary);
    if(db){
        db.seekg(0,db.end);
        long length = db.tellg();
        if(length < 100) {
            db.close();
            return false;
        }

        db.seekg(0,db.beg);
        db.read(buffer,100);

        if(starts_with(buffer,"SQLite format 3")) return true;
    }
    return false;
}
{% endhighlight%}

This is a mere translation of a similar function in **update-database.py**.

The **benchmark** tool required an almost rewrite. The existing code dealt solely with
text file reading, thus had to be replaced.
The current benchmarking uses the two functions that were in the existing tool.

The first function, check_bankData_lookup, generates given number of **blz** and checks them
using the **AccountNumberCheck::findBank** method.

The second function, check_testkontos, takes a file as a parameter and for **blz** in
each row in this file, it generates a random **kto** and checks the two using **AccountNumberCheck::check**
method.

After pushing these changes, my mentor Ralf suggested to add a \-\-file argument to this tool so as
to use this tool with any specified bankdata file.
Thus, to handle command-line arguments, I made some further changes using the code from an existing tool
in the project.

You can see my commits here : <a href="https://sourceforge.net/u/prasun/ktoblzcheck-gsoc2020/commit_browser" title="Commit Browser" rel="noreferrer noopener" target="_blank">Commit Browser</a>

As outlined in the previous post, all the objectives of this phase are completed.

* A script that generates the SQLite DB using blz datafile downloaded from the  <a href="https://www.bundesbank.de/de/aufgaben/unbarer-zahlungsverkehr/serviceangebot/bankleitzahlen/download-bankleitzahlen-602592" title="Deutsche Bundesbank" rel="noreferrer noopener" target="_blank">Deutsche Bundesbank</a> :heavy_check_mark:
* Modifications in the CMake build system to call this script at build time. :heavy_check_mark:
* Replacing the part of code that uses the text datafile with the code that reads from this database. :heavy_check_mark:
* Updating tests, documentations and benchmark to work with the new database. :heavy_check_mark:
* Modifying the command-line tool to enable support for user-supplied database. :heavy_check_mark:

So, this marks the end of the first phase of the project.
Truly, a remarkable experience.

Learnt so much, still much remains unknown.
Hoping to discover more new stuff.

See you in the next post.

:wave:<br/>
Prasun.