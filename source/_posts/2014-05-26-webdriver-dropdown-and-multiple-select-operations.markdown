---
layout: post
title: "Webdriver : Dropdown and Multiple Select Operations"
date: 2014-05-26 10:15:16 +0700
comments: true
categories: Webdriver
---

##DropDown & Multiple Select Operations

Just like Checkboxes & Radio buttons, Dropdown and Multiple Select also works together and almost the same way. To perform any action, the first task is to identify the element group. I am saying it a group, as dropdown/multiple select is not a single element. They always have a single name but and they contains one or more than one elements in them. I should rather say more than one option in dropdown and multiple select. The only difference between these two is deselecting statement & multiple selections are not allowed on dropdowns. Let’s look at the different operations:

###Selecting Dropdown/Multiple Select Box

It is just an ordinary operation like selecting any other type of element on a webpage. You can choose it by ID, Name, Css & Xpath etc. But to perform any action on this element it is required to import ‘import org.openqa.selenium.support.ui.Select' package and to use it we need to create a new select object of class select.

```
Select oSelection = new Select(driver.findElement(By.id(id)));
```

Note: Select class only works for elements with <select> tags

###Selecting an option using ‘selectByVisibleText’

It is very easy to choose or select an option given under any dropdowns and multiple selection boxes with selectByVisibleText method.

```
Select oSelection = new Select(driver.findElement(By.id(id)));
oSelection.selectByVisibleText(text);

```

###Selecting an option using ‘selectByIndex’

It is almost the same as selectByVisibleText but the only difference here is that we provide the index number of the option here rather the option text.

```
Select oSelection = new Select(driver.findElement(By.id(id)));

oSelection.selectByIndex(index);
```

###Selecting an option using ‘selectByValue’

It is again the same what we have discussed earlier, the only difference in this is that we need to provide the value of the option rather the option text.

```
Select oSelection = new Select(driver.findElement(By.id(id)));
oSelection.selectByValue(value);

```

Note: The value of an option and the text of the option may not be always same and there can be a possibility that the value is not assigned to Select webelement. If the value is given in the Select tag then only you can use the selectByValue method.

###Getting the Size of Select item

Sometimes you may like to count the element in the dropdown and multiple select box, so that you can use the loop on Select element.

```
Select oSelection = new Select(driver.findElement(By.id(id)));
List<WebElement> oSize = oSelection.getOptions();
int iListSize = oSize.size();

```

###Printing the Options

Once you get the size of the Select element then it is easy to print the Text of the options.

```
Select oSelection = new Select(driver.findElement(By.id(id)));
	List oSize = oSelection.getOptions();
	int iListSize = oSize.size();
	for(int i =0; i>iListSize ; i++){
		String sValue = oSelection.getOptions().get(i).getText();
		System.out.println(sValue);
		}
```

All of the above methods work on both Dropdown and Multiple select box.

###Deselect methods

This only works on Multiple selection boxes. If in case you want to deselect any selected option and that can be done with either deselectAll(), deselectByIndex, deselectByValue and deselectByVisibletext.

```
Select oSelection = new Select(driver.findElement(By.id(id)));
	oSelection.deselectAll();
	oSelection.deselectByIndex(index);
	oSelection.deselectByValue(value);
	oSelection.deselectByVisibleText(text);

```

###Multiple selection method

This one also just works on Multiple selection boxes and not on regular List boxes or dropdowns. There is no additional logic behind selecting multiple options of Select element. All you need to do is to fire select commands on multiple elements one by one that’s it.

```
Select oSelection = new Select(driver.findElement(By.id(id)));
	oSelection.selectByIndex(index)
	oSelection.selectByIndex(index)
	// Or
	oSelection.selectByVisibleText(text)
	oSelection.selectByVisibleText(text)
	// Or
	oSelection.selectByValue(value)
	oSelection.selectByValue(value)
```

