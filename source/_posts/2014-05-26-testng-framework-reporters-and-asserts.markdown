---
layout: post
title: "TestNG Framework :Reporters and Asserts "
date: 2014-05-26 11:55:48 +0700
comments: true
categories: TestNG-Framework
---

##TestNG Reporters & Asserts

###TestNG Reporters

TestNG is a Framework and so far we have already seen the many different powerful features of TestNG. It almost gives you all the important things you are required to complete the Framework.

###TestNG Reporter Logs

TestNG also gives us the logging facility for the test. For example during the running of test case user wants some information to be logged in the console. Information could be any detail depends upon the purpose. Keeping this in mind that we are using Selenium for testing, we need the information which helps the User to understand the test steps or any failure during the test case execution. With the help of TestNG Logs it is possible to enable logging during the Selenium test case execution.

In selenium there are two types of logging. High level logging and Low level logging. In low level logging you try to produce logs for the every step you take or every action you make in your automation script. In high  level logging you just try to capture main events of your test.

Everybody has their own style of logging and I have mine too. I am also a big fan of Log4j logging and that’s why I do not mix log4j logging with testng logging but on the same side I make to use of both of its. I perform low level logging with log4j and high level logging with testng reporter logs.

####How to do it…

1) Write a test case for Sign In application and implement Log4j logging on every step.

2) Insert Reporter logs on the main events of the test.

```
package automationFramework;

import java.util.concurrent.TimeUnit;

import org.apache.log4j.Logger;
import org.apache.log4j.xml.DOMConfigurator;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.testng.Reporter;
import org.testng.annotations.Test;

import utility.Log;

public class ReporterLogs {
	private static WebDriver driver;
	private static Logger Log = Logger.getLogger(Log.class.getName());
    @Test
	public static void test() {
		DOMConfigurator.configure("log4j.xml");
        driver = new FirefoxDriver();
        Log.info("New driver instantiated");
        driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
        Log.info("Implicit wait applied on the driver for 10 seconds");
        driver.get("https://www.facebook.com/");
        Log.info("Web application launched");
        // Our first step is complete, so we produce a main event log here for our reports.
        Reporter.log("Application Lauched successfully | ");
   
        driver.findElement(By.id("email")).sendKeys("yourusername");
        Log.info("Username entered in the Username and email text box");
        driver.findElement(By.id("pass")).sendKeys("yourpassword");
        Log.info("Password entered in the Password text box");
        driver.findElement(By.id("loginbutton")).click();
        Log.info("Click action performed on Submit button");
        // Here we are done with our Second main event
        Reporter.log("Sign In Successful | " );
        driver.quit();
        Log.info("Browser closed");
        // This is the third main event
        Reporter.log("User is Logged out and Application is closed | ");
	}

}
```

3) Run the test by right click on the test case script and select Run As > TestNG Test.

Your Log4j logging output will look like this:

{% img /images/TestNG-Reporter-1.png%}

But your Reporters log will look like this:

{% img /images/TestNG-Reporter-2.png%}

Log4j logging will help you to report a bug or steps taken during the test, on the other hand reporters log will help you to share the test status with leadership. As leadership is just interested in the test results, not the test steps.

I also use reporter’s logs on the verification during the test. For example

```
if(Text1.equals(Text2)){
		Reporter.log("Verification Passed forText");
	}else{
		Reporter.log("Verification Failed for Text");
	}
```

###TestNG Asserts

TestNG also gives us the power to take decisions in the middle of the test run with the help of Asserts. With this we can put various checkpoints in the test. Asserts are the most popular and frequently used methods while creating Selenium Scripts. In selenium there will be many situations in the test where you just like to check the presence of an element. All you need to do is to put an assert statement on to it to verify its existence.

####Different Asserts Statements

1) Assert.assertTrue() & Assert.assertFalse() 

```
package automationFramework;

import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.testng.Assert;
import org.testng.annotations.Test;

public class Asserts {
	private static WebDriver driver;
  @Test
  public void f() {
	  driver = new FirefoxDriver();
      driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
      driver.get("https://www.facebook.com/");
      
      // Here driver will try to find out My username textbox on the application
      WebElement text_username = driver.findElement(By.id("email"));
      
      //Test will only continue, if the below statement is true
      //This is to check whether the textbox is displayed or not
      Assert.assertTrue(text_username.isDisplayed());
      
      //My username text will be type only if the above condition is true
      myAccount.sendKeys("your_username");
  }
}
```

Note: Assert true statement fails the test and stop the execution of the test, if the actual output is false.  Assert.assertFalse() works opposite of Assert.assertTrue(). It means that if you want your test to continue only if when some certain element is not present on the page. You will use Assert false, so it will fail the test in case of the element present on the page.

2) Assert.assertEquals()

```
@Test
  public void test() {
	  String sValue = "Ta bao Lan";
	  System.out.println(" What is your full name");
	  Assert.assertEquals("Ta Bao Lan", sValue);
	  System.out.println(sValue);
  }
```

It also works the same way like assert true and assert fail. It will also stop the execution, if the value is not equal and carry on the execution, if the value is equal.
