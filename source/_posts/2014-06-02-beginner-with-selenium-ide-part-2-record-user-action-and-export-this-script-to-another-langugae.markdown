---
layout: post
title: "Beginner with Selenium Ide Part 2: Record User Action and Export this Script to another langugae"
date: 2014-06-02 15:03:46 +0700
comments: true
categories: NewBie
---

##Introduction

In this tutorial  , we will let you know how to record the user action in browser via Selenium IDE and How to export this to another language like java , ...!

###Record User Action
<!--more-->

1) Open Firefox Browser and click in the icon of Selenium IDE.

{% img /images/ide-3.png %}

2) The GUI of Selenium Ide will show , click in the red circle button of the top to record user action.

{% img /images/ide-5.png %}

3) Go back to the firefox driver and type to the url "https://facebook.com"

4) Login to facebook as normal.

5) Back to Selenium IDE GUI , you will see it recorded your action.

{% img /images/ide-6.png %}

6) Click in the button play to let Selenium IDE run again each action that you made before.

{% img /images/ide-7.png %}

7) Now if you can save this test case as html file and re-run it by Open Selenium IDE and Open File -> choose the path you save this file.

###Export this test script to another language script.

The most useful option is "Export" because it allows you to turn your Selenium IDE test cases into file formats that can run on Selenium Remote Control and WebDriver

Selenium IDE , test cases can be exported only to the following formats:

.cs (C# source code)

.java (Java source code)

.py (Python source code)

.rb (Ruby source code)

You just need click in menu File -> Export Test Case As.

{% img /images/ide-9.png %}

Note : You need to know that some function when you export from Selenium IDE to another language will be fail. I suggest you need to re-check the export File by running it again.






