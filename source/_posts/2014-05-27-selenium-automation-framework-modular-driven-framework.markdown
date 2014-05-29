---
layout: post
title: "Selenium Automation Framework : Modular Driven Framework"
date: 2014-05-27 10:11:21 +0700
comments: true
categories: Selenium-Framework
---

##Modular Driven Framework

###Required knowledge : [Page Object Model](/blog/2014/05/26/selenium-automation-framework-page-object-model/)

In most of the web application we have few set of actions which are always executed in the series of actions. Rather than writing those actions again and again in our test, we can club those actions in to a method and then calling that method in our test script. Modularity avoids duplicacy of code. In future if there is any change in the series of action, all you have to do is to make changes in your main modular method script. No test case will be impacted with the change.

<!--more-->

###How to do it..

Look for repeated functionality in your application for example the 'login' functionality. We can simple wrap this functionality in a method and we can give it a sensible name.

1) Create a 'New Package' file and name it as 'userAction', by right click on the Project and select New > Package. We will be creating different packages for Page Objects, Utilities, Test Data, Test Cases and Modular actions. It is always recommended to use this structure, as it is easy to understand, easy to use and easy to maintain.

{% img /images/pom-1.png%}

{% img /images/user-action-1.png%}

{% img /images/user-action-2.png%}

2) Create 'New Class' and name it as SignIn by right click on package 'userAction' and select New > Class. It will add new class 'SignIn' under package 'userAction'.

{% img /images/user-action-3.png%}

{% img /images/user-action-4.png%}

3) Now create a Public Static Void Method and name it as Execute  and club the following steps in to it:

Load Page login Facebook

Enter Username

Enter Password

Click on the Submit button

```
package com.selenium.userAction;

import org.openqa.selenium.WebDriver;

import com.selenium.pageObject.LoginPage;

public class SignIn {

	/**
	 * @param driver
	 * @param username
	 * @param password
	 * execute login to facebook
	 */
	public static void Execute(WebDriver driver , String username, String password) {
		LoginPage.loadPage(driver);
		LoginPage.txtbx_UserName(driver).sendKeys(username);
		LoginPage.txtbx_Password(driver).sendKeys(password);
		LoginPage.btn_LogIn(driver).click();
	}

}

```

4) Create 'New Class' and name it as PostStatus by right click on package 'userAction' and select New > Class. It will add new class 'PostStatus' under package 'userAction'.

{% img /images/user-action-3.png%}

{% img /images/user-action-5.png%}

5) Now create a Public Static Void Method and name it as Execute  and club the following steps in to it:

Enter Status

Click on button Post.


```
package com.selenium.userAction;

import org.openqa.selenium.WebDriver;

import com.selenium.pageObject.HomePage;

public class PostStatus {
	
	/**
	 * @param driver
	 * @param status
	 * execute post status in facebook
	 */
	public static void Execute(WebDriver driver, String status){
		HomePage.txt_status(driver).sendKeys(status);
		HomePage.butt_post(driver).click();
	}
	
}

```

###We are complete to create the actions next we will follow to create the first test with TestNG