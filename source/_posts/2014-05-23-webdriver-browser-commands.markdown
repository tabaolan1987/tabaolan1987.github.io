---
layout: post
title: "Webdriver : Browser Commands"
date: 2014-05-23 15:56:48 +0700
comments: true
categories: Webdriver
---

##Selenium WebDriver Browser Commands

The very first thing you like to do with Selenium is to opening and closing a new browser. Below are the numbers of commands you can apply on the Selenium opened browser.

-- Điều đầu tiên bạn muốn làm với Selenium là mở và đóng 1 trình duyệt. Dưới đây là những lệnh hữu ích mà bạn có thể dùng.

###1)Get Command

Purpose: This command is use to open a new web page in the current browser. 

(Dùng để mở ra 1 trang web trên 1 trình duyệt)

Command: driver.get(URL);

Parameters: url – The URL to load. It is best to use a fully qualified URL.

(Dữ liệu truyền vào là 1 URL. Tốt nhất là truyền vào 1 URL đầy đủ cả Http)

``` 
driver.get("wwww.google.com");
```

###2)Get Title Command

Purpose: This command is use to get the title of the current page.
(Lấy ra tiêu đề của trang hiện tại)

``` 
driver.getTitle();
```

###3)Get Current URL Command

Purpose: This command is use to get the URL of the page currently loaded in the browser.

(Lệnh này dùng để lấy ra URL của 1 trang đã được tải xong trên trình duyệt)

``` 
driver.getCurrentUrl();
```

###4)Get Page Source Command

Purpose: This command is use to get the source of the last loaded page.

(Lệnh này dùng để lấy các code html của trang đã được tải về trên trình duyệt)

``` 
driver.getPageSource();
```

###5)Close Command

Purpose: This command is use to close the current window of the browser, if it’s the last window it will close the browser.

(Lệnh này dùng dể đóng trang web hiện tại đang mở trên trình duyệt nếu nó là trang web cuối cùng thì trình duyệt sẽ tự động đóng)

```
driver.close();
```

###6)Quit Command

Purpose: This command is use to quit the browser and all the opened windows in the browser.

(Lệnh này dùng để đóng trình duyêt)

```
driver.quit();
```

###7)Refresh Command

Purpose: There are some commands is use to refresh the current browser.

(Những lệnh sau đây dùng để tải lại trang web hiện tại trên trình duyệt)

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
