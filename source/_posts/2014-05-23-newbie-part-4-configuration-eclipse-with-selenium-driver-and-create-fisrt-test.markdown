---
layout: post
title: "Newbie Part 4 : Configuration Eclipse with Selenium driver and Create Fisrt Test"
date: 2014-05-23 15:13:27 +0700
comments: true
categories: NewBie
---
##Creat a simple test case selenium in Eclipse

To configure Eclipse with Selenium webdriver, we need to launch the Eclipse IDE, create a Workspace, create a Project, create a Package, create a Class and add External libraries to the project.

###1) Select WorkSpace on Eclipse start up.

a) Double click on ‘eclipse.exe’ to start eclipse. First time when you start eclipse, it will ask you to select your workspace where your work will be stored as shown in below image.

{% img /images/Start-Eclipse-1.png %}

b) Create a “working directory” for all of your projects. Think of it like “My Documents” in the Windows operating system. It’s a folder which contains a lot of your documents, but there’s nothing to prevent you from creating another folder called “My Other Documents” (for instance) to house other documents.

Typically you only need one workspace, and you can think of it as your “My Documents” for Java code. If you wanted to, you could have more than one, but chances are you won’t have a use for more. I like to choose my own workplace location and will place all my ToolsQA tutorial projects under it.

You can change it later on from ‘Switch Workspace‘ under ‘File‘ menu of eclipse. After selecting workspace folder, Eclipse will be open.

{% img /images/Start-Eclipse-21.png%}

{% img /images/Start-Eclipse-3.png%}

c) You may see the window like this, this is the Welcome window for Eclipse. You may close this window.

{% img /images/Start-Eclipse-4.png%}

###2) Create a new Project

Projects: A collection of related code. Generally speaking, each project encompasses one independent program. Each programming assignment you do will typically require its own project.

Once you’ve established your workspace, you’ll want to create a project and begin writing code. In Eclipse, projects are the next-smallest functional unit after workspaces, but where you might have only one workspace, you will usually have several projects inside one workspace.

a) Create new Java Project from File > New > Project .

{% img /images/Setup-Project-1.png%}

b) Select Java Project and click Next.

{% img /images/Setup-Project-2.png%}

c) Give your Project name ‘OnlineStore‘ as shown in below given figures. Click on Finish button.

{% img /images/Setup-Project-3.png%}

d) You may or may not see this message but if in case you get any, check Remember my decision and  click on Yes.

{% img /images/Setup-Project-4.png%}

###3) Create a new Package

a) Right click on Project name ‘OnlineStore‘ and select New > Package.

{% img /images/Creating-Package-1.png%}

b) Give your Package name ‘automationFramework‘ and click on Finish button.

{% img /images/Creating-Package-2.png%}

###4) Create a new Class

Now that you have a project set up, you’re going to want start writing some new classes.

a) Right click on Package ‘automationFramework‘ and select New > Class.

{% img /images/Creating-Class-1.png%}

b)  Give your Class name ‘FirstTestCase‘, check the option ‘public static void main‘ and click on Finish button. This will bring up totally a sweet class creation window.

Note: In case of not creating class for Main test case, please do not click ‘public static void main’. We need to select it only in case of writing test cases which we are going to execute and from where we call other classes. For functional classes, POM classes or any other classes we dont need this to be checked.

{% img /images/Creating-Class-2.png%}

c) Now your Eclipse window will looks like bellow.

{% img /images/Creating-Class-3.png%}

###5) Add External Jars to Java build path

Now you need to add selenium webdriver’s jar files in to Java build path.

a) Right click on Project ‘OnlineStore‘ > Select Properties > Java build path. Then navigate to Libraries tab and click Add External JARs.

{% img /images/Selenium-Jar-1.png%}

b) Add Selenium Java jar, you may add the source file too.

{% img /images/Selenium-Jar-2.png%}

c) Add all the jars from the libs folder as well.

{% img /images/Selenium-Jar-3.png%}

d) Click OK.

-- Ấn nút Ok.

{% img /images/Selenium-Jar-4.png%}

That’s all about configuration of WebDriver with eclipse. Now you are ready to write your test script in eclipse and run it in WebDriver.

{% img /images/Selenium-Jar-5.png%}

###6) Write your First Test Case

a) Copy & paste the below code to your First Test Case class and give it a run.

```
package automationFramework;
import java.util.concurrent.TimeUnit;
 
import org.openqa.selenium.*;
import org.openqa.selenium.firefox.FirefoxDriver;
 
public class FirstTestCase {
    private static WebDriver driver = null;
 
    public static void main(String[] args) {
        // Create a new instance of the Firefox driver
        driver = new FirefoxDriver();
 
        //Put a Implicit wait, this means that any search for elements on the page could take the time the implicit wait is set for before throwing exception
        driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
 
        //Launch the facebook
        driver.get("https://www.facebook.com/");
 
        
        // Find the element that's ID attribute is 'email' (Username)
        // Enter email on the element found by above desc.
		driver.findElement(By.id("email")).sendKeys('enter your username login to facebook')
 
        // Find the element that's ID attribute is 'pass' (Password)
        // Enter Password on the element found by the above desc.
         driver.findElement(By.id("pass")).sendKeys("enter your password login to facebook"); 
 
        // Now submit the form. WebDriver will find the form for us from the element 
        driver.findElement(By.Xpath("//form[@id='login_form']/table/tbody/tr[2]/td[3]/label/input")).click();
 
        // Print a Log In message to the screen
        System.out.println(" Login Successfully, now it is the time to Log Off buddy.");
 
        // Close the driver
        driver.quit();
            }
    }
```

2) Now, to start the test just select Run > Run As > Java Application Or Right Click on Eclipse code and Click Run As  > Java Application

3) After a few Seconds a Mozilla browser will open  and you will see that with the help of your script, Selenium will Launch the Online Store, perform Sign in, display the Message, perform Log out and then Close the browser.

Once the execution is finished, you will see the message in Console section of the Eclipse IDE.

Now you will need to know about WebDriver in Selenium. I just create some basic knowledge about Webdriver please click [here](/blog/categories/webdriver/)