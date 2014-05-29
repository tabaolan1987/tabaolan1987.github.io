---
layout: post
title: "Webdriver : Checkbox and Radio Button Operations"
date: 2014-05-26 10:10:11 +0700
comments: true
categories: Webdriver
---

##CheckBox & Radio Button Operations

Operations on Checkboxes and Radio Buttons are easy to perform and most of the times the simple ID attributes work fine for both of these. But selection and d-selection is not the only thing we want with checkboxes and radio buttons. We might like to check that if the checkbox is already checked or if the radio button is selected by default or anything. Checkboxes and Radio button deals exactly the same way and you can perform below mentioned operations on either of them.
<!--more-->
###Different Selection Method

####By ID

If ID is given for the radio button/checkbox and you just want to click the radio button/checkbox Irrespective of its value, then the command will be like this:

```
WebElement radioBtn = driver.findElement(By.id("toolsqa"));
radioBtn.click();
```

####With ‘IsSelected’

If your choice is based on the pre-selection of the Radio button/Checkbox and you just need to select the deselected radio button/checkbox. Assume there are two radio buttons/checkboxes, one is selected by default and you want to select the other one for your test. With IsSelected statement, you can get to know that the radio button or the check box is selected or not.

```
 // Store all the elements of same category in the list of WebLements	
 List  oRadioButton = driver.findElements(By.name("toolsqa"));

 // Create a boolean variable which will hold the value (True/False)
 boolean bValue = false;

 // This statement will return True, in case of first Radio button is selected
 bValue = oRadioButton.get(0).isSelected();

 // This will check that if the bValue is True means if the first radio button is selected
 if(bValue = true){

	// This will select Second radio button, if the first radio button is selected by default
	oRadioButton.get(1).click();

 }else{

	// If the first radio button is not selected by default, the first will be selected
	oRadioButton.get(0).click();
 }

```

Note: Name is always same for the same group of radio buttons/checkboxes but their Values are different. So if you find the checkbox/radio button element with the name attribute then it means that it may contain more than one element, hence we need to use findElements method and store it the list of WebElements.

###With ‘Value’

You can even select Radio buttons/Checkboxes with their Values.

```
// Find the checkbox or radio button element by Name
 List oCheckBox = driver.findElements(By.name("example"));

 // This will tell you the number of checkboxes are present
 int iSize = oCheckBox.size();

 // Start the loop from first checkbox to last checkboxe
 for(int i=0; i < iSize ; i++ ){

	 // Store the checkbox name to the string variable, using 'Value' attribute
	 String sValue = oCheckBox.get(i).getAttribute("value");

	 // Select the checkbox it the value of the checkbox is same what you are looking for
	 if (sValue.equalsIgnoreCase("your value")){
		 oCheckBox.get(i).click();

		 // This will take the execution out of for loop
		 break;
		 }
	}
```

###By ‘CssSelector’

A simple way of selecting a check-box or radio button is by using its value:

```
WebElement oCheckBox = driver.findElement(By.cssSelector("input[value='example']"));
oCheckBox.click();
``` 
