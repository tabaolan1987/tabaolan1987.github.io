---
layout: post
title: "XPath : Selenium Locators"
date: 2014-05-26 10:48:22 +0700
comments: true
categories: XPath
---

##Locators in Selenium

Selenium uses what is called locators to find and match the elements of the webpage that it needs to interact with. Locators are the lifeblood of the tests. Using the right locator ensures the tests are faster, more reliable or has lower maintenance over releases. If you’re fortunate enough to be working with unique IDs and Classes, then you’re usually all set. But there will be times when choosing a right locator will become a nightmare. It can be a real challenge to verify that you have the right locators to accomplish what you want.

This tutorial explains different locators, how, when and ideal Strategies to use these locators.

###Different types of Locators

There are 8 explicit locators: id, name, identifier, dom, xpath, link, css and ui that Selenium’s commands support. I will explain just a few most important locators to avoid over dosage and any confusion.

####ID Locator

Ids are the most preferred way to locate elements on a page, as each id is supposed to be unique which makes ids a very faster and reliable way to locate elements.

With this strategy, the first element with the id attribute value matching the location will be returned. If no element has a matching id attribute, a NoSuchElementException will be raised.

HTML CODE :

```
<form name="loginForm">Login 
 Username: <input id="username" type="text" name="login" />
 Password: <input id="password" type="password" name="password" />
 <input type="submit" name="signin" value="SignIn" /></form>
``` 

You can easily choose the element with the help of ID locator from the above example:

id = “username”

id = “password”

Use the same in your Selenium test script as well:

```
WebElement elementUsername = driver.findElement(By.id("username"));

WebElement elementPassword = driver.findElement(By.id("password"));

```

Even though this is a great locator, obviously it is not realistic for all objects on a page to have ids. In some cases developers make it having non-unique ids on a page or auto-generate the ids, in both cases it should be avoided.

####Name Locator

This is also an efficient way to locate an element  with name attribute, after Ids give it your second preference but likewise Ids, name attributes don’t have to be unique in a page.

With this strategy, the first element with the name attribute value matching the location will be returned. If no element has a matching name attribute, a  NoSuchElementException will be raised.

Example: Let’s take the above example:

You can easily choose the element with the help of Name locator from the above example:

name = “login”

name = “password”

Use the same in your Selenium test script as well:

```
WebElement elementUsername = driver.findElement(By.name("login"));
 
WebElement elementPassword = driver.findElement(By.name("password"));
```

####Identifier Locator

This selects the element with the specified @id attribute. If no match is found, then it tries to select the first element whose @name attribute is id.

Example: Valid locator for above example is:
identifier = “password”

First it will try to find the locator with id = “password” if it exists, otherwise it would target name = “password”.

####Link Locator

With this you can find elements of “a” tags(Link) with the link names. Use this when you know link text used within an anchor tag.

Example: If an element is given like this:

```
<a href="link.html">Name of the Link</a>
```

To click this hyperlink using the anchor tag’s text, you can use the link locator:
link=”Name of the Link”

Use the same in your Selenium test script as well:

```
WebElement element=driver.findElement(By.linkText("Name of the Link"));
```

####DOM Locator

The DOM strategy works by locating elements that matches the JavaScript expression referring to an element in the DOM of the page. DOM stands for Document Object Model. DOM is convention for representing objects in HTML documents.

Example: To select the username from the above example you can use the following ways: 

document.forms[0].elements[0]

document.forms['loginForm'].elements['username']

document.forms['loginForm'].username

document.getElementById(‘username’)

####XPath Locator

While DOM is the recognized standard for navigation through an HTML element tree, XPath is the standard navigation tool for XML; and an HTML document is also an XML document (xHTML). XPath is used everywhere where there is XML.

Example: To select the username from the above example you can use the following ways:

xpath=//*[@id='username']

xpath=//input[@id='username']

xpath=//form[@name='loginForm']/input[1]

xpath=//*[@name='loginForm']/input[1]
