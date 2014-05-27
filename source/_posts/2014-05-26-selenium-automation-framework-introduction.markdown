---
layout: post
title: "Selenium Automation Framework : Introduction"
date: 2014-05-26 14:07:59 +0700
comments: true
categories: Selenium-Framework
---

##Selenium Automation Framework

###Introduction

Mission critical software undergoes rigorous functional tests, especially supported by automated testing frameworks. Automating these frameworks and maintaining quality software releases are critical to business performance. Enterprises often face the dilemma of balancing costs and managing resources to ensure that automation frameworks cover all the business scenarios and the applications delivered are error – free.
By implementing the appropriate automated testing framework, enterprises can significantly increase the speed and accuracy of the testing process, provide a higher return on investment (ROI) from software projects and systematically minimize risk.

###Why Framework

A framework defines the organization’s way of doing things – a ‘Single Standard’. Following this standard would result in the project team achieving:

####Script-less representation of Automated tests

The testing framework should offer point-and-click interface for accessing and interacting with the application components under test—as opposed to presenting line after line of scripting. Testers should be able to visualize each step of the business scenario, view and edit test cases intuitively. This will shorten the learning curve for testers and help QA teams meet deadlines.

####Data Driven tests

A key benefit of automating functional testing is the ability to test large volumes of data on the system quickly. But you must be able to manipulate the data sets, perform calculations, and quickly create hundreds of test iterations and permutations with minimal effort. Test Automation Frameworks must have capability to integrate with spreadsheets and provide powerful calculation features.

####Concise Reporting

The ability to run high volume of tests is of little benefit if the results of the tests are not easy to understand. The framework must automatically generate reports of the test run and show the results in an easy-to-read format. The reports should provide specifics about where application failures occurred and what test data was used. Reports must present application screen shots for every step to highlight any discrepancies and provide detailed explanations of each checkpoint pass and failure. Reports must also be easily shared across the entire QA and development teams.

####Standard Scripting and Team Consistency

Scripting standard should be maintained across the framework library creation, which includes business components, system communications, data check points, loggers, reporters etc. Project team should follow the defined scripting standards. Published standards across the project team pre-empt the effort involved in duplicate coding, which prevent individuals from following their own coding standards.

####Encapsulation from Complexities

Test engineers are encapsulated from the complexities and critical aspects of the code. Engineers are exposed only to the implemented libraries and tests are executed by just invoking the libraries.

####Implement and Maximize Re-Usability

Establish the developed libraries across the organization/project team/product team, i.e. publish the library and provide access rights. Utilities/components shared across the team. Usage of available libraries. Minimized effort for repeated regression cycle.

###Class Diagram

{% img /images/diagram.png%}

What does this look like in code? How would we best accomplish this task? Well, that depends on what you are doing. For example, maybe you need to test 5 different types of projects, or maybe you need to test same page differently each time. Either way, as a coding standard, you should always design classes with a specific purpose. Anything that is shared should go into a base class for common functionality.



