---
layout: post
title: "Selenium Automation Framework P6 : Create Test Script"
date: 2014-05-29 14:48:11 +0700
comments: true
categories: Selenium-Framework
---

##Create Test Script using TestNG

###Required knowledge : [Page Object Model](/blog/2014/05/26/selenium-automation-framework-page-object-model/), [Modular Driven Framework](/blog/2014/05/27/selenium-automation-framework-modular-driven-framework/) , [TestNG Framework](/blog/categories/testng-framework/) 

TestNG is a testing framework inspired from JUnit and NUnit but introducing some new functionalities that make it more powerful and easier to use. In simple words TestNG is a tool that help us to organize the tests and help us to produce the test reports. TestNG framework can be used for automation testing with Selenium (web application automation testing tool).

TestNG Advantages

- Multiple built in Annotations which are easier to use and understand

- Test method can be dependent to other method

- Test cases can be Grouped and can be execute separately by groups

- Parallel testing is possible

- TestNG has built in HTML report and XML report generation facility. It has also built in  logging facility

<!--more-->
####How to do it...

1) Right Click in 'src/test/java' -> New -> Package -> name it as 'com.selenium.test'

{% img /images/testng-1.png%}

{% img /images/testng-2.png%}

2) Right Click in package 'com.selenium.test' -> TestNG -> Create TestNG Class.

{% img /images/testng-3.png%}

3) Name your class as 'autoTestFacebook' and tick on 'BeforeTest' and 'AfterTest' option.

{% img /images/testng-4.png%}

4) Double click in 'autoTestFacebook' to open it. Copy and paste the code below to this.

```
package com.selenium.test;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.testng.annotations.Test;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.AfterTest;

import com.selenium.pageObject.LoginPage;
import com.selenium.userAction.PostStatus;
import com.selenium.userAction.SignIn;

public class autoTestFacebook {
	
	/**
	 * Create WebDriver as static variable
	 */
	private static WebDriver driver;
	
  
  /**
 * Setup some variable to run your script test
 */
@BeforeTest
  public void beforeTest() {
	  driver = new FirefoxDriver();
  }
  
  /**
 * your test script call action class here
 */
@Test
  public void f() {
	  LoginPage.loadPage(driver);
	  SignIn.Execute(driver, "gaumun", "63hamlong");
	  PostStatus.Execute(driver, "this is my status posted by my automation test");
  }
  
  
  /**
 * after run your script test , use this code to close your browser
 */
@AfterTest
  public void afterTest() {
	  driver.quit();
  }
}
```

5) Right click on your class -> Run As -> TestNG Test.

{% img /images/testng-5.png%}

6) Wait for TestNG running and check the result of test in folder 'test-output'

{% img /images/testng-6.png%}

###After this tutorial you are already have a project base on Selenium Framework. Take a look what you have done , you will see maintain this project is not hard. Your test script is very easy to know base on actually action of user.


