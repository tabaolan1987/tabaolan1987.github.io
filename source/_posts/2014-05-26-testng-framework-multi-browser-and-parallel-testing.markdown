---
layout: post
title: "TestNG Framework : Multi Browser and Parallel Testing"
date: 2014-05-26 12:15:47 +0700
comments: true
categories: TestNG-Framework
---

##Multi Browser, Cross Browser & Parallel Testing using TestNG

When the time comes to turn your site from mock-up to something fully functional, you’ll want to make sure that it works great for everyone visiting your site whether they’re using Internet Explorer, Firefox, or any other browser. Testing your website with multiple combinations of browsers is known as Cross Browser testing.

Your site will look different in different browsers. That’s because browsers understand some code slightly differently. Your designer should be testing to make sure that your site works well in all modern browsers. But as a tester we need to make sure that functionality should at least tested on Internet Explorer, Firefox, Safari & Google Chrome browser.
<!--more-->
###Multi Browser Testing using Selenium TestNG

In every project it is required to perform multi-browser testing to make sure that the functionality is working as expected with every browser to give equal user experience to all of the wide range of audience. It takes a considerable time to test everything on every browser and when we have used automation to reduce the testing efforts then why don’t we perform the multi-browser testing using automation. TestNG gives us functionality to perform same test on different browsers in a simple and easy way.

####How to do it…

1)Create your Script to test a LogIn application using TestNG class.

2) Pass ‘Browser Type’ as parameters using TestNG annotations to the before method of the TestNG class. This method will launch only the browser, which will be provided as parameter.

```
package automationFramework;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.openqa.selenium.ie.InternetExplorerDriver;
import org.testng.annotations.AfterClass;
import org.testng.annotations.BeforeClass;
import org.testng.annotations.Parameters;
import org.testng.annotations.Test;

public class MultiBrowser {
	public WebDriver driver;
  
  @Parameters("browser")
  @BeforeClass
  // Passing Browser parameter from TestNG xml
  public void beforeTest(String browser) {
  // If the browser is Firefox, then do this
  if(browser.equalsIgnoreCase("firefox")) {
	  driver = new FirefoxDriver();
  // If browser is IE, then do this	  
  }else if (browser.equalsIgnoreCase("ie")) { 
	  // Here I am setting up the path for my IEDriver
	  System.setProperty("webdriver.ie.driver", "D:\OnlineStore\drivers\IEDriverServer.exe");
	  driver = new InternetExplorerDriver();
  } 
  // Doesn't the browser type, lauch the Website
   driver.get("https://www.facebook.com");
  }
  
  // Once Before method is completed, Test method will start
  @Test public void login() throws InterruptedException {
      driver.findElement(By.id("email")).sendKeys("your username");
      driver.findElement(By.id("pass")).sendKeys("your password");
      driver.findElement(By.id("loginbutton")).click();
      driver.quit();
	}  

  @AfterClass public void afterTest() {
		driver.quit();
	}
}

```

3) Create a TestNG XML for running your test. Configure the TestNG XML for passing parameters i.e. to tell which browser should be used for Running the Test.

```
<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE suite SYSTEM "http://testng.org/testng-1.0.dtd">

<suite name="Suite" parallel="none">
 <test name="FirefoxTest">
 <parameter name="browser" value="firefox" />
 <classes>
 <class name="automationFramework.MultiBrowser" />
 </classes>
 </test>

 <test name="IETest">
 <parameter name="browser" value="ie" />
 <classes>
 <class name="automationFramework.MultiBrowser" />
 </classes>
 </test>
</suite>

```

 Note: You can set any number of Browsers here and just for the example purpose I have set up only two main browsers.

4) Now it’s time to run the xml. Run the test by right click on the testng.xml file and select Run As > TestNG Suite.

{% img /images/TestNG-MultiBrowser-1.png%}

Note: TestNg will execute the test one by one. You may like to perform parallel tests, next topic will cover that.

###Parallel Tests using TestNG

Using the feature provided by TestNG for Parallel Executions. just take the above example for Sign In application with two different browsers. This time all we want is to execute test in both browsers simultaneously.

Now just set the ‘parallel‘ attribute to ‘tests‘ in the above used xml and give a run again. This time you will notice that your both browsers will open almost simultaneously and your test will run in parallel.

```
<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE suite SYSTEM "http://testng.org/testng-1.0.dtd">

<suite name="Suite" parallel="tests">
 <test name="FirefoxTest">
 <parameter name="browser" value="firefox" />
 <classes>
 <class name="automationFramework.MultiBrowser" />
 </classes>
 </test>

 <test name="IETest">
 <parameter name="browser" value="ie" />
 <classes>
 <class name="automationFramework.MultiBrowser" />
 </classes>
 </test>
</suite>

```

Note: You may see some intermittent issues using parallel testing. I will not recommend you this rather run one by one only.
