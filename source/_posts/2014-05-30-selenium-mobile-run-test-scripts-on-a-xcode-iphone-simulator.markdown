---
layout: post
title: "Selenium Mobile : Run test scripts on a Xcode iPhone simulator"
date: 2014-05-30 15:07:42 +0700
comments: true
categories: Selenium-mobile
---

##Introduction

We want to run our test in a iPhone simulator. The iphone simulator comes with Xcode which is available for the Mac operating systems. This recipe will show us how we can run our WebDriver tests in a iphone simulator.
<!--more-->
We need to download Xcode from the following location: [here](http://developer.apple.com/iphone)

The iPhone WebDriver application is not available from the App Store, therefore we need to check-out the code and build it manually. We can do the check-out by entering the following terminal command

```

svn checkout http://selenium.googlecode.com/svn/trunk/

```

##Solution

1) Open the project selenium-read-only/iphone/iWebDriver.xcodeproj in Xcode.

2) Double-click on the project and set the build configuration to the latest version of the iPhone Simulator, by using the drop-down box in the top left corner.

3) Click on Run (play button). After compiling, the iphone simulator should appear and the iWebDriver app will be installed in it.


4) Now we can use the IPhoneDriver in our tests. You will need to take a look in [TestNG Framework](/blog/categories/testng-framework/). Create new TestNG class and paste the code below :

```
package com.selenium.test;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.iphone.IPhoneDriver;
import org.testng.annotations.Test;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.AfterTest;

import com.selenium.pageObject.LoginPage;
import com.selenium.userAction.PostStatus;
import com.selenium.userAction.SignIn;

public class autoTestLoadingFacebook {
	
	/**
	 * Create WebDriver as static variable
	 */
	private static WebDriver driver;
	
  
  /**
 * Setup some variable to run your script test
 */
@BeforeTest
  public void beforeTest() {
	  driver =  new IPhoneDriver();
  }
  
  /**
 * your test script
 */
@Test
  public void f() {
	driver.get("https://facebook.com");
	//create more test script here
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

5) Run your test.