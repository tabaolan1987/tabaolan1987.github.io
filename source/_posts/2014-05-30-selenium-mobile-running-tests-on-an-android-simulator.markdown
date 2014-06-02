---
layout: post
title: "Selenium Mobile : Running tests on an Android simulator"
date: 2014-05-30 14:46:17 +0700
comments: true
categories: Selenium-mobile
---

##Introduction

The android driver allows us to execute our tests against an Android browser. This can be a simulator or a real device. This recipe will walk us through the steps we have to do to run our tests in a simulator.
<!--more-->
Before we can register our simulator we have to download the android SDK (Software Development Kit) from the following location: [SDK](http://developer.android.com/sdk/)

##Solution

We can divide this section into three parts: setup the emulator, install the WebDriver APK and finally run the test.

###Setup the emulator

1) Navigate to the tools directory and create an Android Virtual Device. -n: specifies the name of the AVD -t: specifies the platform target -c: specifies the SD card storage space.

```

$cd ~/android_sdk/tools/ 
$./android create avd -n my_android -t 12 -c 100M

```

2) We can list the targets with the following command to check if the creation succeeded:

```

./android list targets

```

3)Finally we can start the emulator with the following command:

```
$./emulator -avd my_android &
```

###Install the WebDriver APK

1) We need to retrieve the serial id with the following command: 

```
$cd /android_sdk/platform-tools/
adb devices
```

2) Download the Android server from [Selenium website](http://code.google.com/p/selenium/downloads/list) and save it in the platform-tools directory. To install the application enter:

```
$./adb -s <serialId> -e install -r android-server.apk
```

3) Start the Android WebDriver application,by running this command:

```
$./adb -s <serialId> shell am start -a android.intent.action.MAIN -n org.openqa.selenium.android.app/.MainActivity
```

4) Now we need to setup the port forwarding in order to forward traffic from the host machine to the emulator. Enter the following in the terminal :

```
$./adb -s <serialId> forward tcp:8080 tcp:8080
```

###Run the test

You will need to take a look in [TestNG Framework](/blog/categories/testng-framework/)

Now we have our environment setup we can run our tests. Create new TestNG and paste the code below : 

```
package com.selenium.test;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.android.AndroidDriver;
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
	  driver =  new AndroidDriver();
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