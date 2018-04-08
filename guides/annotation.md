---
title: DataAtWork BRAT Annotation Manual
---

This document provides an introduction to the BRAT tool deployed by DataAtWork for skill tagging.

Although the installation of BRAT is mostly standard, there are some changes so
even if you know how to use BRAT this guide is worth reading.

## Selecting a Document

You should have been sent a link to a particular collection.
Unlike standard BRAT installations, *annotating is not collaborative* here.
What this means is that you have a directory of your own, just for your annotations. 

The link you were sent should look something like:
*http://label.dataatwork.org/#/.thcrockett/unit_4/*

The *.thcrockett* (but with your username) is a directory for job postings
that are just for you to annotate.

The *unit_4* is a directory containing a subset of job postings that has
been allocated for you to work on. If you finish annotating these job postings
and want to request more, you may do so.

After clicking the link, you will likely see a tutorial tab, which upon closing you will
see the *collection browser*. Because you have been sent a link to a personal collection,
it should look something like this:

![Annotation Guide Collection Browser](/img/annotation-guide/collection-browser.png)

The numbers starting at 0 are job posting documents for you to annotate.
Double-click on any document (or click and then click 'OK') to open the document.


## Logging In

A common source of confusion at this point is making sure you are logged in. BRAT will
show you the document whether or not you are logged in, but you won't be able to make any
annotations unless you are logged in. If you hover your cursor on the top bar, a menu will
drop down. It will have either a 'Login' or 'Logout' link on the right. If it says 'Login',
login with the username and password you were given so you can start to tag documents.


## Tagging a Document

### The Mechanics of Tagging

BRAT lets the user tag words or phrases in a document by highlighting them. So click on the
beginning of a word or phrase, and drag it to the end of that word or phrase to tag it.
A window will pop up, prompting for an entity type. Our job posting collection has only one
entity type, 'Skill', so it comes preselected. Simply press 'Enter', click the 'OK' button
in the popup window, or type the keyboard shortcut 's' to confirm this phrase as a skill.
You can later double-click on this word or phrase to delete the skill tag if needed.
Your tags are automatically saved.

### What Should Be Tagged?
At this point, you know how to mark a word or phrase as a skill. But how do you decide what is a skill?

Let's start with a simple definition: a skill is the expertise or talent needed to do, or useful for doing, a job.

A lot of different categories fall under this umbrella, from cognitive skills to physical skills to pieces of technology.  We want to tag any examples of these, without distinctions between the different categories.

Making the distinction between what should be tagged and what shouldn’t may seem tricky, especially at first. Here are some guidelines to hopefully make this easier:

- *Short generalized verbs or verb phrases like ‘Lead’ or ‘Motivate and lead’ can still be skills.* It’s more that we want to avoid things that are overly specific to the job/company. It’s true that the canonical phrasing of ‘Lead’ as a skill would probably be the noun form ‘Leadership’, but different employers will phrase this in different ways, and it’s useful to extract generalizable skills even in verb form.
- *Tools and technology count.* If some type of device, software, or other jargon used on the job is mentioned, definitely tag it. These types of competencies are fast-changing, and extracting them from job postings is of great importance.
- *Don’t be afraid to tag the same thing multiple times.* Although it may seem duplicative, we are training a machine learning model and it’s important for it to learn the rules to extract skills correctly. So if ‘product design’ is mentioned a few different times in the job posting, that’s helpful.
- *It’s okay if there are multiple skills in a phrase that can’t be separated because of how they are phrased.* For instance, ‘design and production of x’ is a pattern that shows up a lot. Ideally, maybe you would want to tag ‘design of x’ and ‘production of x’, but that requires rewording a sentence. We would rather tag ‘design and production of x’ as a skill. It’s better to have slightly too much information than too little, and in later data processing stages it may be possible to separate ‘design and production of x’ into two distinct skills.

To help illustrate our definition let's look at an example.

Below you’ll see two screenshots, of two different sections of the same job posting.
![Annotation Guide Example Section 1](/img/annotation-guide/example-1.png)
![Annotation Guide Example Section 2](/img/annotation-guide/example-2.png)

What has been tagged in this example? A mix of:

- Soft skills (lead, mentor, demonstrated leadership skills)
- Academic knowledge (Molecular Biology, basic statistics)
- Tool/technology jargon (BSL-2+ level human pathogens)
- General technical skills (data analysis)
- General work skills (product design)

When you are done tagging skills in this job posting document, you can move onto the
next document in one of a couple ways:

- The left/right arrow buttons on the top left corner of the screen
- The 'Collection' link on the top menu towards the left side. This will bring you back
to the collection browser screen you came from, which allows you to pick any job posting you'd like.


## Requesting More Job Postings

You'll note that there is a small list of job postings in your collection. If you have tagged
all of these job postings and you wish to tag more, let us know! We are working on a solution
within BRAT to make this more automated, but for now you can:

- Send an email to thcrockett AT uchicago DOT edu
- Send a Slack message (register for [our Slack](http://slack.dataatwork.org/) if you haven't already) to @thcrockett
