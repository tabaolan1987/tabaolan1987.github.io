---
layout: post
title: "Selenium Automation Framework P2 : Install Maven to Eclipse"
date: 2014-05-26 14:14:07 +0700
comments: true
categories: Selenium-Framework
---

##Maven plugin for Eclipse

You can install Maven plugin for Eclipse via update site, simply copy the above update site link address and paste it into Eclipse’s “Update” or “Install New Software” manager as explained below.

<!--more-->

###Step 1 : 

Installing m2eclipse is fairly simple. Start Eclipse then go to: Help -> Install New Software

Copy this link http://download.eclipse.org/technology/m2e/releases for the latest Stable Release into Eclipse and hit Enter.

{% img /images/maven-plugin-eclipse-1.jpeg%}

When the site loads, select the features to install, or click the Select All button. For our requirement select “Maven Integration for Eclipse” as shown above.

Checking [x] Contact all update sites during install to find required software might take sometime and this is optional.

###Step 2 : 

Click Next to view Installation Details.

Click Next to agree the license terms, and click Finish.

###Step 3 :

If you get any warning message when installing, click OK to continue.

{% img /images/maven-plugin-eclipse-2.jpg%}

This will take few minutes to install the Maven plugin and once done restart the Eclipse.

{% img /images/maven-3.jpg%}

