---
layout: post
title: "Selenium Automation Framework : Page Object Model"
date: 2014-05-26 16:03:08 +0700
comments: true
categories: Selenium-Framework
---

##Page Object Model | POM

Creating Selenium test cases can result in an unmaintainable project. One of the reasons is that too many duplicated code is used. Duplicated code could be caused by duplicated functionality and this will result in duplicated usage of locators. The disadvantage of duplicated code is that the project is less maintainable. If some locator will change, you have to walk through the whole test code to adjust locators where necessary. By using the page object model we can make non-brittle test code and reduce or eliminate duplicate test code. Beside of that it improves the readability and allows us to create interactive documentation. Last but not least, we can create tests with less keystroke. An implementation of the page object model can be achieved by separating the abstraction of the test object and the test scripts.

Note : We will try to create Login Page and Homepage follow website [Facebook](https://facebook.com)

###How to do it

1. Create a ‘New Package’ file and name it as ‘pageObjects’, by right click on the Project and select New > Package. We will be creating different packages for Page Objects, Utilities, Test Data, Test Cases and Modular actions. It is always recommended to use this structure, as it is easy to understand, easy to use and easy to maintain.

{% img /images/pom-1.png%}

{% img /images/pom-2.png%}

{% img /images/pom-3.png%}

2. Create a ‘New Class’ file and refer the name to the actual page from the test object, by right click on the above created Package and select New > Class. In our case it is Login Page.

{% img /images/pom-4.png%}

{% img /images/pom-5.png%}

4. Open URL : Https://facebook.com . Wait for page loading then we will use firebug to find the location elements of form login Facebook.

{% img /images/pom-6.png%}

3.Now create a Static Method for each Element (Object) in the Login Page. Each method will have an Argument (driver) and a Return value (element).

```
package com.selenium.pageObject;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;

import com.gargoylesoftware.htmlunit.ElementNotFoundException;

public class LoginPage {
	
	 /**
	 * WebElement element 
	 */
	private static WebElement element = null;
	
	/**
	 * @param driver
	 * @return let driver load the login page of facebook
	 * @throws InterruptedException
	 */
	public static WebDriver loadPage(WebDriver driver) {
		driver.get("https://facebook.com");
		return driver;
	}
	 
	
	/**
	 * @param driver
	 * 
	 * @return the textbox username of login form facebook
	 */
	public static WebElement txtbx_UserName(WebDriver driver) throws ElementNotFoundException{
		element = driver.findElement(By.id("email"));
		return element;
	}
	
	/**
	 * @param driver
	 * @return the textbox passwork of login form facebook
	 */
	public static WebElement txtbx_Password(WebDriver driver) throws ElementNotFoundException{
		element = driver.findElement(By.id("password"));
		return element;
	}
	
	/**
	 * @param driver
	 * @return the button login of login form facebook
	 */
	public static WebElement btn_LogIn(WebDriver driver) throws ElementNotFoundException{
		element = driver.findElement(By.id("loginbutton"));
		return element;
	}
}
```

6. Create a ‘New Class’ file and refer the name to the actual page from the test object, by right click on the above created Package and select New > Class. In our case it is Home Page.

{% img /images/pom-1.png%}

{% img /images/pom-7.png%}

7. Open URL : Https://facebook.com -> login in - use xpath to find element location (textarena to post status and button for post).

{% img /images/pom-8.png%}

8.Now create a Static Method for each Element (Object) in the Home Page. Each method will have an Argument (driver) and a Return value (element).

```
package com.selenium.pageObject;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;

public class HomePage {

	/**
	 * WebElement
	 */
	private static WebElement element;
	
	/**
	 * @param driver
	 * @return textbox update status element
	 */
	public static WebElement txt_status(WebDriver driver) {
		element = driver.findElement(By.xpath("//div[@id='pagelet_composer']/div/div/div/form[1]/div[1]/div[2]/div/div/div[2]/div/div/textarea"));
		return element;
	}
	
	/**
	 * @param driver
	 * @return button to post status
	 */
	public static WebElement butt_post(WebDriver driver){
		element = driver.findElement(By.xpath("//div[@id='pagelet_composer']/div/div/div/form[1]/div[1]/div[4]/div/ul/li[2]/button"));
		return element;
	}
}
```

### We are finish to create a Login Page , Home Page follow Page Object Model . Now you will need to create an Action in Java base on User Define, please [click here]()
