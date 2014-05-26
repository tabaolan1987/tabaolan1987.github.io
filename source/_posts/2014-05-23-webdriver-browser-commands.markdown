---
layout: post
title: "Webdriver : Browser Commands"
date: 2014-05-23 15:56:48 +0700
comments: true
categories: Webdriver
---

##Selenium WebDriver Browser Commands

The very first thing you like to do with Selenium is to opening and closing a new browser. Below are the numbers of commands you can apply on the Selenium opened browser.

###1)Get Command

Purpose: This command is use to open a new web page in the current browser. 

Command: driver.get(URL);

Parameters: url – The URL to load. It is best to use a fully qualified URL.

``` 
driver.get("wwww.google.com");
```

###2)Get Title Command

Purpose: This command is use to get the title of the current page.

``` 
driver.getTitle();
```

###3)Get Current URL Command

Purpose: This command is use to get the URL of the page currently loaded in the browser.

``` 
driver.getCurrentUrl();
```

###4)Get Page Source Command

Purpose: This command is use to get the source of the last loaded page.

``` 
driver.getPageSource();
```

###5)Close Command

Purpose: This command is use to close the current window of the browser, if it’s the last window it will close the browser.

```
driver.close();
```

###6)Quit Command

Purpose: This command is use to quit the browser and all the opened windows in the browser.

```
driver.quit();
```

###7)Refresh Command

Purpose: There are some commands is use to refresh the current browser.

```
driver.navigate().refresh();
driver.get(driver.getCurrentUrl());
driver.navigate().to(driver.getCurrentUrl());
driver.findElement(By.name("s")).sendKeys("\uE035");
```

##Simple Practice Exercise

1) Launch a new Firefox browser.

2) Open daringfireball.net

3) Get Page Title name and Title length

4) Print Page Title and Title length on the Eclipse Console.

5) Get Page URL and URL length

6) Print URL and URL length on the Eclipse Console.

7) Refresh current page

8) Get Page Source (HTML Source code) and Page Source length

9) Print Page Source and length on Eclipse Console.

10) Close the Browser.

###Solution

####1) Create class 'PracticeBrowserCommands' and copy code below paste to your class and Run this class.

```
package automationFramework;
import java.util.concurrent.TimeUnit;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
 
public class PracticeBrowserCommands {
    private static WebDriver driver = null;
 
    public static void main(String[] args) throws InterruptedException {
 
         // Create a new instance of the Firefox driver
        driver = new FirefoxDriver();
 
        //Put a Implicit wait, this means that any search for elements on the page could take the time the implicit wait is set for before throwing exception
        driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
 
        //Launch the markdown syntax
        driver.get("http://daringfireball.net/");
 
        // Storing Title name in String variable
        String sTitle = driver.getTitle();
        // Storing Title length in Int variable
        int iTitleLength = driver.getTitle().length();
        // Printing Title name on Console
        System.out.println(sTitle);
        // Printing Title length on console
        System.out.println(iTitleLength);
 
        // Storing URL in String variable
        sTitle = driver.getCurrentUrl();
        // Storing URL length in Int variable
        iTitleLength = driver.getCurrentUrl().length();
        // Printing URL on Console
        System.out.println(sTitle);
        // Printing URL length on console
        System.out.println(iTitleLength);
 
        // Refreshing current page
        driver.get(driver.getCurrentUrl());  
 
        // Storing Page Source in String variable
        String sPageSource = driver.getPageSource();
        // Storing Page Source length in Int variable
        int iPageSourceLength = driver.getPageSource().length();
        // Printing Page Source on console
        System.out.println(sPageSource);
        // Printing Page SOurce length on console
        System.out.println(iPageSourceLength);
 
        //Closing browser
        driver.close();
    }
}
```