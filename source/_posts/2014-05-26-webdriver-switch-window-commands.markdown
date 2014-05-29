---
layout: post
title: "Webdriver : Switch Window Commands"
date: 2014-05-26 09:02:20 +0700
comments: true
categories: Webdriver
---

##WebDriver Switch Window Commands

Some web applications have many frames or multiple windows. Selenium WebDriver assigns an alphanumeric id to each window as soon as the WebDriver object is instantiated. This unique alphanumeric id is called window handle. Selenium uses this unique id to switch control among several windows. In simple terms, each unique window has a unique ID, so that Selenium can differentiate when it is switching controls from one window to the other.
<!--more-->
###GetWindowHandle Command

Purpose: To get the window handle of the current window.

```
String  handle= driver.getWindowHandle();//Return a string of alphanumeric window handle
```

###GetWindowHandles Command

Purpose: To get the window handle of all the current windows.

```
Set<String> handle= driver.getWindowHandles();//Return a set of window handle
```

###SwitchTo Window Command

Purpose: WebDriver supports moving between named windows using the “switchTo” method.

```
driver.switchTo().window("windowName");

```

Alternatively, you can pass a “window handle” to the “switchTo().window()” method. Knowing this, it’s possible to iterate over every open window like so:

```
for (String handle : driver.getWindowHandles()) {
    driver.switchTo().window(handle);
}

```

Switching between windows with Iterators:

```

driver.findElement(By.id(“id of the link which opens new window”)).click();
 //wait till two windows are not opened
 waitForNumberofWindowsToEqual(2);//this method is for wait

 Set handles = driver.getWindowHandles();
 firstWinHandle = driver.getWindowHandle(); handles.remove(firstWinHandle);
 String winHandle=handles.iterator().next();
 if (winHandle!=firstWinHandle){
 //To retrieve the handle of second window, extracting the handle which does not match to first window handle
 secondWinHandle=winHandle; //Storing handle of second window handle

//Switch control to new window
 driver.switchTo().window(secondWinHandle);

```

###SwitchTo Frame Command

Purpose: WebDriver supports moving between named frames using the “switchTo” method.

```
driver.switchTo().frame("frameName");
```

###SwitchTo PopUp Command

Purpose: WebDriver supports moving between named PopUps using the “switchTo” method. After you’ve triggered an action that opens a popup, you can access the alert and it will return the currently open alert object. With this object you can now accept, dismiss, read its contents or even type into a prompt. This interface works equally well on alerts, confirms, and prompts.

```
Alert alert = driver.switchTo().alert();
```

###Practice Exercise 1

1) Launch new Browser

2) Open URL "http://docs.seleniumhq.org/download/"

3) Get Window name (Use GetWindowHandle command)

```
package practiceTestCases;
import java.util.Set;
import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;

public class PracticeSwitchWindow {

		public static WebDriver driver;
		public static void main(String[] args) {

			// Create a new instance of the Firefox driver
	        driver = new FirefoxDriver();

	        // Put an Implicit wait, this means that any search for elements on the page could take the time the implicit wait is set for before throwing exception
	        driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);

	        // Launch the URL
	        driver.get("http://docs.seleniumhq.org/download/");

	        // Store and Print the name of the First window on the console
	        String handle= driver.getWindowHandle();
	        System.out.println(handle);

	        // Close Original window
	        driver.quit();

	}

}
```