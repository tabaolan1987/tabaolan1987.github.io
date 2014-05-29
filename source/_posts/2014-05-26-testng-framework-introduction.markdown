---
layout: post
title: "TestNG Framework : Introduction"
date: 2014-05-26 11:00:14 +0700
comments: true
categories: TestNG-Framework
---

##TestNG Introduction

TestNG is a testing framework inspired from JUnit and NUnit but introducing some new functionality that make it more powerful and easier to use.
<!--more-->
TestNG is an open source automated testing framework; where NG of TestNG means Next Generation. TestNG is similar to JUnit but it is much more powerful than JUnit but still it’s inspired by JUnit. It is designed to be better than JUnit, especially when testing integrated classes. Pay special thanks to Cedric Beust who is the creator of TestNG.

TestNG eliminates most of the limitations of the older framework and gives the developer the ability to write more flexible and powerful tests with help of easy annotations, grouping, sequencing & parameterizing.

###Benefits of TestNG

There are number of benefits of TestNG but from Selenium perspective, major advantages of TestNG are :

1) It gives the ability to produce HTML Reports of execution

2) Annotations made testers life easy

3) Test cases can be Grouped & Prioritized more easily

4) Parallel testing is possible

5) Generates Logs

6) Data Parameteriz ation is possible

###Test Case Writing

Writing a test in TestNG is quite simple and basically involves following steps:

Step 1 – Write the business logic of the test

Step 2 – Insert TestNG annotations in the code

Step 3 - Add the information about your test (e.g. the class names, methods names, groups names etc…) in a testng.xml file

Step 4 - Run TestNG

###Annotations in TestNG

@BeforeSuite: The annotated method will be run before all tests in this suite have run.

@AfterSuite: The annotated method will be run after all tests in this suite have run.

@BeforeTest: The annotated method will be run before any test method belonging to the classes inside the tag is run.

@AfterTest: The annotated method will be run after all the test methods belonging to the classes inside the tag have run.

@BeforeGroups: The list of groups that this configuration method will run before. This method is guaranteed to run shortly before the first test method that belongs to any of these groups is invoked.

@AfterGroups: The list of groups that this configuration method will run after. This method is guaranteed to run shortly after the last test method that belongs to any of these groups is invoked.

@BeforeClass: The annotated method will be run before the first test method in the current class is invoked.

@AfterClass: The annotated method will be run after all the test methods in the current class have been run.

@BeforeMethod: The annotated method will be run before each test method.

@AfterMethod: The annotated method will be run after each test method.

@Test: The annotated method is a part of a test case.

Benefits of using annotations

1) TestNG identifies the methods it is interested in by looking up annotations. Hence method names are not restricted to any pattern or format.

2) We can pass additional parameters to annotations.

3) Annotations are strongly typed, so the compiler will flag any mistakes right away.

4) Test classes no longer need to extend anything (such as Test Case, for JUnit 3).
 
