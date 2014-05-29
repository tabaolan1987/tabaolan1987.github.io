---
layout: post
title: "TestNG Framework : Parameters and Data Provider"
date: 2014-05-26 12:05:31 +0700
comments: true
categories: TestNG-Framework
---

##TestNG Parameters & Data Provider

###TestNG Parameters

Everybody knows the importance of Parameterization in testing and in automation testing. It allows us to automatically run a test case multiple times with different input and validation values. As Selenium Webdriver is more an automated testing framework than a ready-to-use tool, you will have to put in some effort to support data driven testing in your automated tests. I usually prefer to use Microsoft Excel as the format for storing my parameters but so many of my followers have requested to write an article on TestNG Data Provider.

TestNG again gives us another interesting feature called TestNG Parameters. TestNG lets you pass parameters directly to your test methods with your testng.xml.
<!--more-->
####How to do it…

Let me take a very simple example of LogIn application, where the username and password is required to clear the authentication.

1) Create a test on my demo OnlineStore application to perform LogIn which takes the two string argument as username & password.

2) Provide Username & Password as parameter using TestNG Annotation.

```
package automationFramework;

import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.testng.annotations.Test;

import org.testng.annotations.Parameters;

public class TestngParameters {
	private static WebDriver driver;
  @Test 
  @Parameters({ "sUsername", "sPassword" })
  public void test(String sUsername, String sPassword) {
	  driver = new FirefoxDriver();
      driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
      driver.get("https://www.facebook.com");
      driver.findElement(By.id("email")).sendKeys(sUsername);
      driver.findElement(By.id("pass")).sendKeys(sPassword);
      driver.findElement(By.id("loginbutton")).click();
      driver.quit();
  }
}

```

3) The parameter would be passed values from testng.xml which we will see in the next step.

```
<suite name="Suite">
    <test name="ToolsQA">
	<parameter name="sUsername" value="yourusername"/>
	<parameter name="sPassword" value="yourpassword"/>
		<classes>
		    <class name="automationFramework.TestngParameters" />
		</classes>
    </test>
</suite>

```

Now, run the testng.xml, which will run the parameterTest method. TestNG will try to find a parameter named sUsername & sPassword.

###TestNG DataProviders

When you need to pass complex parameters or parameters that need to be created from Java (complex objects, objects read from a property file or a database, etc…), in such cases parameters can be passed using Dataproviders. A Data Provider is a method annotated with @DataProvider. A Data Provider returns an array of objects.

Let us check out the same Sign In examples using Dataproviders.

####How to do it…

1)  Define the method credentials() which is defined as a Dataprovider using the annotation. This method returns array of object array.

2) Add a method test() to your DataProviderTest class. This method takes two strings as input parameters.

3) Add the annotation @Test(dataProvider = “Authentication”) to this method. The attribute dataProvider is mapped to “Authentication”.

Test will look like this:

```
package automationFramework;

import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.testng.annotations.DataProvider;
import org.testng.annotations.Test;

public class DataProviderTest {
	private static WebDriver driver;
	
  @DataProvider(name = "Authentication")
  public static Object[][] credentials() {
        return new Object[][] { { "yourusername", "yourpassword" }, { "yourusername_another", "yourpassword_another" }};
  }
  
  // Here we are calling the Data Provider object with its Name
  @Test(dataProvider = "Authentication")
  public void test(String sUsername, String sPassword) {
	   driver = new FirefoxDriver();
      driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
      driver.get("https://www.facebook.com");
      driver.findElement(By.id("email")).sendKeys(sUsername);
      driver.findElement(By.id("pass")).sendKeys(sPassword);
      driver.findElement(By.id("loginbutton")).click();
      driver.quit();
  }
}
```

Run the test by right click on the test case script and select Run As > TestNG Test. Give it few minutes to complete the execution, once it is finished the results will look like this in the TestNg Result window.

Note: As the test data is provided two times, the above test executed two times completely.
