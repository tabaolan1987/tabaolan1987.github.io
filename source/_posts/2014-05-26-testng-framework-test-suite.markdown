---
layout: post
title: "TestNG Framework : Test Suite"
date: 2014-05-26 11:28:33 +0700
comments: true
categories: TestNG-Framework
---

##TestNG Test Suite

In any project, you will end up to a place where you need to execute so many test cases on a run. Running a set of test cases together is call executing a Test Suite. Those test cases can be dependent to each other or may have to be executed in a certain order. TestNg gives us the capability to manage our test execution.

In TestNG framework, we need to create testng.xml file to create and handle multiple test classes. This is the xml file where you will configure your test run, set test dependency, include or exclude any test, method, class or package and set priority etc.
<!--more-->
###How to do it…

####Step 1 : Create a TestNG XML

1) Right click on Project folder, go to New and select ‘File‘ as shown in below image.

{% img /images/TestNG-Suite1.png%}

2) In New file wizard, add file name = ‘testng.xml‘ as shown in below given image and click on Finish button.

{% img /images/TestNG-Suite2.png%}

3) It will add testng.xml file under your project folder.

####Step 2 : Write xml code ?

Now add below given code in your testng.xml file.see the image below

{% img /images/TestNG-Suite3.png%}

Hope you have understood the xml code, as it is quite simple hierarchy:

Very first tag is the Suite tag<suite>, under that it is the Test tag<test> and then the Class tag<classes>. You can give any name to the suite and the test but you need to provide the correct name to the <classes> tag which is a combination of your Package name and Test Case name.

####Step 3 : Execute a testng.xml

Now it’s time to run the xml. Run the test by right click on the testng.xml file and select Run As > TestNG Suite.

{% img /images/TestNG-Suite4.png%}

It will take few seconds to start the testng execution engine and soon you will notice that your test will run and complete. Once the execution is complete, you can view test execution result under the TestNg console.

{% img /images/TestNG-Suite5.png%}

This is the one simple example of creating and running testng.xml file in eclipse.

###Building a Test Suite

Now when you have learned how to build the xml, now it’s time to learn how to build a Test Suite using testng.xml. It is again not a complex task, all you need to do is to add your test cases to your xml file in <classes> tag.

{% img /images/TestNG-Suite6.png%}

The above test will execute only those tests, which are mentioned in the testng.xml. The rest of the test cases under ‘automationFramework’ package will remain untouched.




