---
layout: post
title: "Webdriver : Element Commands"
date: 2014-05-23 16:29:53 +0700
comments: true
categories: Webdriver
---

##Selenium WebDriver WebElement Commands

The next thing you like to do is to interact with a web page. You need to locate an element first on the web page before interacting with it and locating elements can be done on the WebDriver instance itself or on a WebElement. Webdriver gives us “Find Element” and “Find Elements” method to locate elements on the web page.

###Find Element & Find Elements Method

The difference between “Find Element” and “Find Elements” method is the first returns a WebElement object otherwise it throws an exception and the latter returns a list of WebElements, it can return an empty list if no DOM elements match the query. The “Find” methods take a locator or query object called “By”. “By” strategies are listed below.

####By ID

With this strategy, the first element with the id attribute value matching the location will be returned. If no element has a matching id attribute, a NoSuchElementException will be raised. This is the most efficient and preferred way to locate an element, as most of the times IDs are unique. But in some cases UI developers make it having non-unique ids on a page or auto-generating the id, in both cases it should be avoided.

Example: If an element is given like this:

```

<!-- html code
<input id="Username"></input>
--!>
//java code to find the input with id is "Username"
WebElement element = driver.findElement(By.id("Username"));

```

####By Name

This is also an efficient way to locate an element but again the problem is same as with ID that UI developer make it having non-unique names on a page or auto-generating the names. With this strategy, the first element with the name attribute value matching the location will be returned. If no element has a matching name attribute, a NoSuchElementException will be raised.

Example: If an element is given like this:

```
<!-- html code
<input name="Username"></input>
--!>
//java code to find the input with name is "Username"
WebElement element = driver.findElement(By.name("Username"));

```

####By Class Name

With this you can find elements based on the value of the “class” attribute. If an element has many classes then this will match against each of them. A class can contain many elements.

Example: If an element is given like this:

```
<!-- html code
<input class="Username"></input>
--!>
//java code to find the input with className is "Username"
WebElement element = driver.findElement(By.className("Username"));

```

####By Tag Name

With this you can find elements by their tag names.

Example: If an element is given like this:

```
//html code
<a href="link.html">Name of the Link</a>

// java code to find
WebElement element=driver.findElement(By.linkText("Name of the Link"));

```

By Partial Link Text

With this you can find elements of “a” tags(Link) with the partial link names. Use this when you know link text used within an anchor tag.

Example: If an element is given like this

```
//html code
<a href="link.html">Name of the Link</a>
// java code to find
WebElement element=driver.findElement(By.linkText("Name of"));
```

or

```
WebElement element=driver.findElement(By.linkText("the Link"));
```

###Practice Exercise 1

1) Launch new Browser

2) Open URL https://www.facebook.com

3) Type Name & password 

4) Click on SignIn button

####Solution

```
package automationFramework;

import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;

public class PracticeWebElementCommands {
	public static WebDriver driver;
	public static void main(String[] args) {
		 // Create a new instance of the Firefox driver
        driver = new FirefoxDriver();

        // Put an Implicit wait, this means that any search for elements on the page could take the time the implicit wait is set for before throwing exception
        driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);

        // Launch the ToolsQA Website
        driver.get("https://www.facebook.com");

        // Type email      
        driver.findElement(By.id("emaill")).sendKeys("youremail"); 

        //Type passwork
        driver.findElement(By.name("pass")).sendKeys("yourpassword");

        // Click on SignIn
        driver.findElement(By.Xpath("//form[@id='login_form']/table/tbody/tr[2]/td[3]/label/input")).click();
		}
	}
```