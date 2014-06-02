---
layout: post
title: "Selenium Automation Framework P8 : Read Data From Excel File"
date: 2014-06-02 12:05:43 +0700
comments: true
categories: Selenium-Framework
---

##Reading data from the Excel

###Required knowledge : [Page Object Model](/blog/2014/05/26/selenium-automation-framework-page-object-model/), [Modular Driven Framework](/blog/2014/05/27/selenium-automation-framework-modular-driven-framework/)

In some way , the client want us read data from excel file then past it to the automation test.In this tutorial , I will write step by step to read data from excel file then past it to the test.

This is the scenario  : Login to facebook by get username and password from excel file.

###How to do 
<!--more-->
1)Create new file excel 'test.xlsx' like this  and paste to the folder 'Driver' or you can create new folder.

{% img /images/excel-3.png%}

2) Open your 'pom.xml' to make sure that we added apache POI jar file(this jar file will allow us to open ,get data from excel) in the dependency tag.

{% img /images/excel-1.png%}

3) Open your project go to package 'com.selenium.util' and create new class 'ExcelUtil'.

{% img /images/excel-2.png%}

4) Open 'ExcelUtil.java' and paste the code below to it : 

```
package com.selenium.util;

import java.io.File;
import java.io.FileInputStream;

import org.apache.poi.xssf.usermodel.XSSFCell;
import org.apache.poi.xssf.usermodel.XSSFSheet;
import org.apache.poi.xssf.usermodel.XSSFWorkbook;

public class ExcelUtil {
	private static XSSFSheet ExcelWSheet;
	private static XSSFWorkbook ExcelWBook;
	private static XSSFCell Cell;
	
	
	//this method is to get the path of the file 'test.xlsx' in folder driver
	public static String PathExcelInProject(){
		String path = DriverUtil.getKey(DriverUtil.PROP_PROJECT_BASE_DIR) + File.separator + DriverUtil.FOLDER_DRIVER 
				+ File.separator + "";
		try {
			File Excel = new File(path);
			if(Excel.exists()){
				return Excel.getAbsolutePath();
			}
		} catch (Exception e) {
			e.printStackTrace();
			return null;
		}
		return null;	
	}
	
	// This method is to set the File path and to open the Excel file, Pass
	// Excel Path and Sheetname as Arguments to this method
	public static void setExcelFile(String Path, String SheetName)
			throws Exception {
		try {
			// Open the Excel file
			FileInputStream ExcelFile = new FileInputStream(Path);
			// Access the required test data sheet
			ExcelWBook = new XSSFWorkbook(ExcelFile);
			ExcelWSheet = ExcelWBook.getSheet(SheetName);
		} catch (Exception e) {
			throw (e);
		}
	}

	// This method is to read the test data from the Excel cell, in this we are
	// passing parameters as Row num and Col num
	public static String getCellData(int RowNum, int ColNum) throws Exception {
		try {
			Cell = ExcelWSheet.getRow(RowNum).getCell(ColNum);
			String CellData = Cell.getStringCellValue();
			return CellData;
		} catch (Exception e) {
			return "";
		}
	}
}

```

5) Create a new testNG class and with name 'loginFacebookByExcelData' and paste the code below :

```
package com.selenium.test;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.testng.annotations.Test;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.AfterTest;

import com.selenium.pageObject.LoginPage;
import com.selenium.userAction.SignIn;
import com.selenium.util.ExcelUtil;


public class loginFacebookByExcelData {
	
	private WebDriver driver;
	
	private static String username;
	
	private static String password;
	
  @Test
  public void loginByExcel() {
	  //Call loading page of login page facebook , take a look in post [Page Object Model] of my blog
	 LoginPage.loadPage(driver);
	 //Call action SignIn , take a look in post [Modular Driven Framework] of my blogs
	 SignIn.Execute(driver, username, password);
  }
  
  @BeforeTest
  public void beforeTest() throws Exception {
	  
	  driver = new FirefoxDriver();
	  
	  //set file excel is my excel file in folder Driver , you can set the other path to your excel file
	  ExcelUtil.setExcelFile(ExcelUtil.PathExcelInProject(), "test");
	  //get the data from file excel
	  username = ExcelUtil.getCellData(2, 1);
	  password = ExcelUtil.getCellData(2, 2);
	  
  }

  @AfterTest
  public void afterTest() {
	  driver.quit();
  }

}

```

6) Right click into class and chose 'Run as' -> 'TestNg Test'

{% img /images/excel-5.png%}





