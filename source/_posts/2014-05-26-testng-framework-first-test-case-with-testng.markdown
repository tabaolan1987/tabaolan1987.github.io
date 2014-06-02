---
layout: post
title: "TestNG Framework P3 : First Test case with TestNG"
date: 2014-05-26 11:09:19 +0700
comments: true
categories: TestNG-Framework
---

##First Test case with TestNG

Steps to follow:

1) Press Ctrl+N , select “TestNG Class” under TestNG category and click Next.

Or

Right click on Test Case folder, go to TestNG and select “TestNG Class“. 
<!--more-->
{% img /images/TestNG-FTC-1.png%}

2) If your project is set up and you have selected the Test Case folder before creating TestNG class then the source folder and the package name will be prepopullated on the form. Set class name as ‘TestNG‘.
Under Annotations, check “@BeforeMethod”, “@AfterMethod” and click Finish. That’s it.

{% img /images/TestNG-FTC-2.png%}

3) Now it will display the newly created TestNg class under the Test Case package(folder). TestNG class will look like the image below with displaying three empty methods. One method f() by default and before & after method, as selected during the creation of the class.

{% img /images/TestNG-FTC-3.png%}

4) Project explorer will look like this with TestNG class.

{% img /images/TestNG-FTC-3.png%}

Now it is the time to write the first TestNG test case.

5) Let’s take an example of First Test Case and divide the test case in to three parts .

@BeforeMethod : Launch Firefox and direct it to the Base URL

@Test : Enter Username & Password to Login, Print console message

@AfterMethod : Close Firefox browser

```
package automationFramework;

import java.util.concurrent.TimeUnit;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.testng.annotations.Test;
import org.testng.annotations.BeforeMethod;
import org.testng.annotations.AfterMethod;

public class TestNG {
	public WebDriver driver;

  @Test
  public void main() {
	// Find the element that's ID attribute is 'account'(My Account)
      driver.findElement(By.id("account")).click();
      // Find the element that's ID attribute is 'log' (Username)
      // Enter Username on the element found by above desc.
      driver.findElement(By.id("email")).sendKeys("yourusername");
      // Find the element that's ID attribute is 'pwd' (Password)
      // Enter Password on the element found by the above desc.
      driver.findElement(By.id("pass")).sendKeys("yourpassword");
      // Now submit the form. WebDriver will find the form for us from the element
      driver.findElement(By.id("loginbutton")).click();
      // Print a Log In message to the screen
      System.out.println(" Login Successfully");
  }
  @BeforeMethod
  public void beforeMethod() {
	  // Create a new instance of the Firefox driver
      driver = new FirefoxDriver();
      //Put a Implicit wait, this means that any search for elements on the page could take the time the implicit wait is set for before throwing exception
      driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
      //Launch the Online Store Website
      driver.get("https://www.facebook.com/");
  }

  @AfterMethod
  public void afterMethod() {
	  // Close the driver
      driver.quit();
  }

}

```

6) Run the test by right click on the test case script and select Run As > TestNG Test.

{% img /images/TestNG-FTC-5.png%}

####Results of running the Testng Test Case

7) Give it few minutes to complete the execution, once it is finished the results will look like this in the TestNg Result window.

{% img /images/TestNG-FTC-6.png%}

It displayed ‘passed : 1′. This means test is successful and  Passed.

There are 3 sub tabs. “All Tests”, “Failed Tests” and “Summary”. Just click “All Tests” to see what is there.

{% img /images/TestNG-FTC-7.png%}

As you see, there is information of which test cases are executed and their duration. Take look to other tabs. Better than Junit right?

8) TestNG also produce HTML reports. To access those reports go to the Project directory and open test-output folder.

{% img /images/TestNG-FTC-8.png%}

9) TestNG also produce ‘index.html‘ report and it resides in the same test-output folder. This reports gives the link to all the different component of the TestNG reports like Groups & Reporter Output. On clicking these will display detailed descriptions of execution. In the advance chapter of TestNG we will go though each of the TestNG topics.

{% img /images/TestNG-FTC-10.png%}

{% img /images/TestNG-FTC-11.png%}





