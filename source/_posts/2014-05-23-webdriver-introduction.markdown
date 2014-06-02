---
layout: post
title: "Webdriver : Introduction"
date: 2014-05-23 15:26:35 +0700
comments: true
categories: Webdriver
---
##Selenium Introduction

###About Selenium

Selenium is a software testing framework for the web that facilitates the automation of browsers. The Selenium project produces various tools for automation testing such as Selenium IDE, Selenium Remote Control (RC), Selenium Grid and Selenium 2.0 & WebDriver. Learning all the tools will give you many different options for approaching different automation problems. The entire suits of tools result in a rich set of testing functions specially geared to the needs of testing of web application of all types.

<!--more-->

###Why Selenium

- Selenium is an open source tool with Corporate backing.
- The tests can then be run against most modern web browsers.
- Selenium deploys on Windows, Linux, and Macintosh platforms.
- It allows recording, editing, and debugging tests.
- Recorded tests can be exported in most language e.g. html, Java, .net, perl, ruby etc.
- Selenium has the support of some of the largest browser vendors who have taken (or are taking) steps to make Selenium a native part of their browser.

###Selenium WebDriver

The primary new feature in Selenium 2.0 is the integration of the WebDriver API. WebDriver is designed to provide a simpler, more concise programming interface in addition to addressing some limitations in the Selenium-RC API. It enables you to use a programming language to write test scripts in different programming languages like html, Java, .net , perl, ruby and which enables you to use conditional operations, looping and other programming concepts which makes you test script robust. Selenium-WebDriver was developed to better support dynamic web pages where elements of a page may change without the page itself being reloaded. WebDriver’s goal is to supply a well-designed object-oriented API that provides improved support for modern advanced web-app testing problems.

###WebDriver Vs Selenium RC

1) Architecture

####WebDriver's architecture is simpler than Selenium RC's.

It controls the browser from the OS level

All you need are your programming language's IDE (which contains your Selenium commands) and a browser.

{% img /images/compare-1.jpg%}

####Selenium RC's architecture is way more complicated.

You first need to launch a separate application called Selenium Remote Control (RC) Server before you can start testing

The Selenium RC Server acts as a "middleman" between your Selenium commands and your browser

When you begin testing, Selenium RC Server "injects" a Javascript program called Selenium Core into the browser.

Once injected, Selenium Core will start receiving instructions relayed by the RC Server from your test program.

When the instructions are received, Selenium Core will execute them as Javascript commands.

The browser will obey the instructions of Selenium Core, and will relay its response to the RC Server.

The RC Server will receive the response of the browser and then display the results to you.

RC Server will fetch the next instruction from your test script to repeat the whole cycle.

{% img /images/compare-2.jpg%}

2) Speed

WebDriver is faster than Selenium RC since it  speaks directly to the browser uses the browser's own engine to control it.

Selenium RC is slower  sinceit uses a Javascript program called Selenium Core.This Selenium Core is the one that directly controls the browser, not you.

3) Real-life Interaction

WebDriver interacts with page elements in a more realistic way. For example, if you have a disabled text box on a page you were testing, WebDriver really cannot enter any value in it just as how a real person cannot.

Selenium Core, just like other Javascript codes, can access disabled elements .In the past, Selenium testers complain that Selenium Core was able to enter values to a disabled text box in their tests.Differences in API.

