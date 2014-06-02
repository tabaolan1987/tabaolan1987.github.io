---
layout: post
title: "Webdriver XPath : FireBug and FirePath"
date: 2014-05-26 10:37:18 +0700
comments: true
categories: Webdriver
---

##FireBug and FirePath

###What is XPath

XPath is a language that describes a way to locate and process items in Extensible Markup Language (XML) documents by using an addressing syntax based on a path through the document’s logical structure or hierarchy. XPath in used in Selenium  to uniquely identify an element on a Webpage as element locator just like the way we use PostCode and House address in real world to locate Home Address.
<!--more-->
###What is Firebug

Firebug integrates with Firefox to put a wealth of web development tools at your fingertips while you browse. You can edit, debug, and monitor CSS, HTML, and JavaScript live in any web page. The whole content of this page is taken from the [firebug](https://getfirebug.com/html).

###Why it is Useful to Selenium Automation Tester

1) View source live : Firefox has a “View Source” window, but it doesn’t show you what the HTML source really looks like once it has been transformed by JavaScript. Firebug’s HTML tab shows you what the HTML looks like right now.

2) See changes highlighted: In any JavaScript-driven website, HTML elements are constantly being created, removed, and modified. Wouldn’t it be nice if you could see exactly what, when, and where these changes take place? Firebug highlights changes to the HTML in yellow immediately when they occur. If you want to spy even closer, you have the option to also scroll every change into view, so you won’t miss a thing.

3) Find elements with the mouse: Something in your page doesn’t quite look right and you want to know why. There’s no faster way to get answers than to click the “Inspect” button on Firebug’s toolbar and then prepare for immediate gratification. As you move around the page, whatever is beneath your mouse will be instantly revealed within Firebug, showing you the HTML and CSS behind it.

4) Copy the source: Right-click on any element, and you’ll have several options for copying aspects of that element to the clipboard, including its HTML fragment, the value of its “innerHTML” property, or an XPath expression that identifies the element uniquely.

###How to Download FireBug

FireBug is a plugin which comes with Firefox browser, hence it is easily be downloadable from Firefox itself.

1) Go to Tools > Web Developer > Get More Tools.

{% img /images/Firebug-1.png%}

2) It will open a Webpage and display all the plugins available for Firefox browser. As we need Firebug, just click on Add to Firefox button for Firebug.

{% img /images/Firebug-2.png%}

3) Hit on Install Now button to proceed.

{% img /images/Firebug-3.png%}

4) Once the Installation is finished, press ‘F-12′ to open Firebug tool. It will display like this.

{% img /images/FIND-ELEMENTS-2.png%}

###How to Use it

Most of the times it is used to Inspect Elements on a Webpage and to get the XPath of the Elements from a Webpage.

1) Inspect Elements: Please visit Finding Elements using Browser Inspector for details explanation on How to find Elements using Browser Inspector.

2) Copy XPath: Copying XPath is really very handy. Once you are done with selecting an Element using Inspector, all you need to do is to Right click on the HTML code of the selected element and select Copy XPath.

{% img /images/Firebug-6.png%}

3) Now you can paste the copied XPath on your test script by pressing ‘Ctrl + V‘. It will display like this:

```
/html/body/div/header/div/a/img
```

###What is FirePath

It is an extension to FireBug that adds a development tool to edit, inspect and generate XPath expressions and CSS3 Selectors.

###Why it is Useful to Selenium Automation Tester

1) You can type self-written XPath and check if it is correct by highlighting the results directly on the Webpage.

2) Generate an XPath expression or a CSS selector for an element by right clicking on it and selecting “Inspect in FirePath” in the context menu.

3) Like Firebug it also gives you the Xpath of the selected Element.

###How to Download Firepath

Firepath is an extension to Firebug, so you would only be able to install it after installing FireBug.

1) Go to Tools > Web Developer > Get More Tools.

{% img /images/Firebug-1.png%}

2) It will open a Webpage and will display all the plugins available for Firefox browser. As I said before that it is an extension to Firebug, you need to click on the Extensions link and the type Firepath on the Search field. As we need FirePath, just click on Add to Firefox button for FirePath.

{% img /images/FirePath-1.png%}

3) Hit on Install Now button to proceed.

{% img /images/FirePath-2.png%}

4) Once it is installed, it will ask to Restart the browser. Click on Restart Now button.

{% img /images/FirePath-3.png%}

4) Once it is opened, press ‘F-12′ to open Firebug tool. It will display the FirePath on the same console.

###How to Use FirePath

1) Inspect Elements: Please visit Finding Elements using Browser Inspector for details explanation on How to find Elements using Browser Inspector. But unlike FireBug, it displays the XPath of the selected element on the console.

{% img /images/FirePath-6.png%}

2) Copy XPath: Copying XPath is really very handy. Once you are done with selecting an Element using Inspector, all you need to do is to Copy the XPath of the selected element and paste it to your Test script by pressing ‘Ctrl + V‘. It will display like this:

```
//*[@id='masthead']/div/a/img
```

###Difference between FireBug and FirePath

The only difference from Automation tester point of view is FireBug returns Absolute XPath and FirePath returns Relative XPath.








