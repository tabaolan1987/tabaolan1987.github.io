---
layout: post
title: "Selenium Mobile : Run test scripts in real IPhone"
date: 2014-05-30 15:22:09 +0700
comments: true
categories: Selenium-mobile
---

##Introduction

We want to execute our testscripts on a iphone device. The iphone driver allows us to execute the WebDriver tests on a real iphone device.
<!--more-->
###Configuration

We need to install Xcode which is available for the Mac operating systems. We also need a provisoning profile for running the script on a real device.

1) We need to create a provisioning profile, so go to this [website](http://developer.apple.com/programs/ios/) and create a profile.

2) We need to download Xcode from the following location: [this](http://developer.apple.com/iphone)

3) The iPhone WebDriver application is not available from the App Store, therefore we need to check-out the code and build it manually. We can do the check-out by entering the following terminal command:

```
svn checkout http://selenium.googlecode.com/svn/trunk/
```

###Solution

1) Open the project selenium-read-only/iphone/iWebDriver.xcodeproj in Xcode.

2) Double-click on the project and set the build configuration to the latest version of the iPhone Simulator, by using the drop-down box in the top left corner.

3) Configure and install the iPhone provisioning profile.

4) Open Info.plist and edit the Bundle Identifier to com.NAME.$ {PRODUCT_NAME:identifier} where NAME is the name you registered your provisioning profile to be an authority on.

5) Make sure your device is connected to your computer. Your device must also be routable from your computer. The easiest way to do this is to configure a wifi network and connect your device to it.

6) Click on Run (play button). After compiling, the iphone simulator should appear and the iWebDriver app will be installed in it.

7) Now we can use the IPhoneDriver in our tests. You will need to take a look in [TestNG Framework](/blog/categories/testng-framework/). Create new TestNG class and paste the code below :

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

8) Run your script.