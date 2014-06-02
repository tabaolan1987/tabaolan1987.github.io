---
layout: post
title: "Webdriver : Action Class"
date: 2014-05-30 14:01:08 +0700
comments: true
categories: Webdriver
---

##Introduction

The Advanced User Interactions API is a new, more comprehensive API for describing actions a user can perform on a web page. This includes actions such as drag and drop or clicking multiple elements while holding down the Control key.
<!--more-->
###Mouse Hover action

There will be situations where it is required to click on the item of the drop down menu that will show up when you mouse over this menu.take a look in the example :

```
// find the menu that have the dropdown showing when we mouse over it.	
WebElement element = driver.findElement(By.linkText("Category"));
//Create instance of action class
Actions action = new Actions(driver);
//move mouse over the menu.
action.moveToElement(element).build().perform();
//find the link you want and click it.
driver.findElement(By.linkText("News")).click();
```

or you can code like this way : 

```
WebElement element = driver.findElement(By.linkText("Category"));
        Actions action = new Actions(driver);
action.moveToElement(element).moveToElement(driver.findElement(By.linkText("News"))).click().build().perform();

```

With some of the browser it happens that once mouse hover action is performed, the menu list disappear with in the fractions of seconds before Selenium identify the next submenu item and perform click action on it. In that case it is better to use perform()' action on the main menu to hold the menu list till the time Selenium identify the sub menu item and click on it.

```
WebElement element = driver.findElement(By.linkText("Category"));
Actions action = new Actions(driver);
action.moveToElement(element).perform();
WebElement subElement = driver.findElement(By.linkText("News"));
action.moveToElement(subElement);
action.click();
action.perform();
```

###Drag And Drop

In case you need drag and drop an element to another position , the action class provide us the way like below code :

```

WebElement From = driver.findElement(By.xpath("yourlocationElement));
WebElement To = driver.findElement(By.xpath("yourlocationElement"));
Actions builder = new Actions(driver);
Action dragAndDrop = builder.clickAndHold(From)
.moveToElement(To)
.release(To)
.build();
dragAndDrop.perform();

``` 


