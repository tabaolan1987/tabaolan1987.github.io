---
layout: post
title: "Selenium Automation Framework : Create New Project"
date: 2014-05-26 15:01:18 +0700
comments: true
categories: Selenium-Framework
---

##Create new Project

Maven project is very helpful for us to manage the version of each library we used and easy to build , easy to configuration with Continuous Integration.

Now we will create a project Maven name "Selenium-Automation-Framework". 

####Step 1 : Open eclipse -> Choose File menu -> Choose New -> Choose Other..

{% img /images/c-maven-1.png%}

####Step 2 : Find Maven -> Choose Maven Project -> Click 'Next' button

{% img /images/c-maven-2.png%}

####Step 3 : Tick on  "Create a simple project" , "Use default workspace"

{% img /images/c-maven-3.png%}

####Step 4 : Enter value for "Group ID" and  "Artifact ID" . Then click "Finish".

{% img /images/c-maven-4.png%}

####Step 5 : The new Project "Selenium-Automation-Framework" will show in the left menu of Eclipse. 

{% img /images/c-maven-5.png%}

##Configuration Project

First you need to configuration the pom.xml file to add library required by Selenium.

####Step 1 : Open project -> Double click to file "pom.xml"

{% img /images/c-maven-6.png%}

####Stemp 2 : Copy this code and paste into your pom.xml file

```
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>Selenium-Automation-Framework</groupId>
  <artifactId>Selenium-Framework</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  	<dependencies>
		<dependency>
			<groupId>org.seleniumhq.selenium</groupId>
			<artifactId>selenium-java</artifactId>
			<version>2.41.0</version>
		</dependency>
		<dependency>
			<groupId>org.seleniumhq.selenium</groupId>
			<artifactId>selenium-server</artifactId>
			<version>2.41.0</version>
		</dependency>
		<dependency>
			<groupId>org.seleniumhq.selenium</groupId>
			<artifactId>selenium-firefox-driver</artifactId>
			<version>2.41.0</version>
		</dependency>
		<dependency>
			<groupId>org.seleniumhq.selenium</groupId>
			<artifactId>selenium-chrome-driver</artifactId>
			<version>2.41.0</version>
		</dependency>
		<dependency>
			<groupId>org.seleniumhq.selenium</groupId>
			<artifactId>selenium-remote-driver</artifactId>
			<version>2.41.0</version>
		</dependency>
		<dependency>
			<groupId>org.seleniumhq.selenium</groupId>
			<artifactId>selenium-ie-driver</artifactId>
			<version>2.41.0</version>
		</dependency>
		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<version>4.11</version>
		</dependency>
		 <dependency>
            <groupId>org.apache.poi</groupId>
            <artifactId>poi</artifactId>
            <version>3.10-FINAL</version>
        </dependency>
        <dependency>
            <groupId>org.testng</groupId>
            <artifactId>testng</artifactId>
            <version>6.8.8</version>
        </dependency>
	</dependencies>
</project>

```

By adding this code , we are telling to maven that we will use jar files that we define in the tag <dependency>.

####Step 3 : Right click into project and choose Maven -> Update project.

{% img /images/c-maven-7.png%}

####Step 4 : Click "Ok" button to let Maven download jar files.

{% img /images/c-maven-8.png%}

####Step 5 : Open the "Maven dependencies" to see jar file are available in your project.

{% img /images/c-maven-9.png%}

###Note : you will need to have an internet in your laptop to allow the download of maven.

Now the setup and configuration is done , you are able to start writing Selenium Automation Framework.







