---
layout: post
title: "Webdriver : Browser Navigation Commands"
date: 2014-05-26 08:53:47 +0700
comments: true
categories: Webdriver
---

##WebDriver Browser Navigation Commands

The navigate interface exposes the ability to move backwards and forwards in your browser’s history but navigate().to() and get() do exactly the same thing. One’s just a lot easier to type than the other.
<!--more-->
###To Command

Purpose : This command is use to navigate on specific page or URL in between the  test Command : driver.navigate().to(URL); Parameters : url – The URL to load. It is best to use a fully qualified URL.

```
driver.navigate().to("http://www.gooogle.com");
```

###Forward Command

Purpose : This command is use to go on to next page like browser’s forward button.

```
driver.navigate().forward();
```

###Back Command

Purpose : This command is use to go back to previous page like browser’s back button.

```
driver.navigate().back();
```

###Practice Exercise

1) Launch new Browser 

2) Open Selenium docs website 

3) Click on About link ( On top navigation) 

4) Come back to Home page (Use ‘Back’ command) 

5) Again go back to About page (This time use ‘Forward’ command) 

6) Again come back to Home page (This time use ‘To’ command) 

7) Refresh the Browser (Use ‘Refresh’ command) 

8) Close the Browser

####Solution

```
package automationFramework;

import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;

public class PracticeNavigationCommands {
	private static WebDriver driver = null;
	public static void main(String[] args) {

		// Create a new instance of the Firefox driver
		driver = new FirefoxDriver();

		// Open Selenium website
		driver.get("http://docs.seleniumhq.org/");

		// Put an Implicit wait on driver
        driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);

		// Click on About link
        driver.findElement(By.Xpath("//a[contains(@href, '/about/')]")).click();

		// Go back to Home Page
		driver.navigate().back();

		// Go forward to About page
        driver.navigate().forward();

		// Go back to Home page
        driver.navigate().to("http://docs.seleniumhq.org/");

		// Refresh browser
		driver.navigate().refresh();

		// Close browser
		driver.close();
	}
}

```