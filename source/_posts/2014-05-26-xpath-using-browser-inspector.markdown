---
layout: post
title: "XPath : Using Browser Inspector"
date: 2014-05-26 10:24:15 +0700
comments: true
categories: XPath
---

##Finding Elements using Browser Inspector

Now days, it is very easy to find elements on the page. All the modern browsers have the web inspector, the built-in tool for to easily examine the structure of webpages.

I used to use Google Chrome’s inspector because Chrome was my default browser; Safari uses the same inspector and IE uses IE Inspector. Firefox has its own built in Inspector and it has an optional extension called Firebug, which has a little more functionality that is sometimes worth switching over for. The steps to use it are largely the same.

###1) Activating the Web Inspector

You can activate the web inspector in any of the above browsers by right-clicking on any element in the page, such as a photo. A pop-up menu should appear with the option to Inspect Element.  Or you can use the short cut key for Inspector which is F-12.

F-12 will pop-up a panel, usually in the bottom-half of your browser, showing the HTML source. The red circle is pointing to the Element Inspector in Firefox.

{% img /images/Finding-Elements-1.png%}

###2) Selecting Elements

Once you click the Inspector Icon from the bottom panel your element inspector is active and as you move your mouse around the page, the element under your mouse is highlighted with a dotted border and an annotation displays its HTML tag. At the same time, its HTML definition is displayed, in context, in the Inspector’s left-hand pane.

In the screenshot below, I have chosen to inspect the "Email or Phone” textbox on the [Facebook](https://www.facebook.com/). The inspector (in the bottom panel of the browser) highlights where in the HTML that the “Email or Phone” button appears.

{% img /images/FIND-ELEMENTS-2.png%}

With the help of above html code you can simply write the below code in your test script:

```
driver.findElement(By.id("email")).sendKeys("your username or email login to facebook");
```



