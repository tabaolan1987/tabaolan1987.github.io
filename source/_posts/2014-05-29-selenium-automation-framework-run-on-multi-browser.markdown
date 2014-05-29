---
layout: post
title: "Selenium Automation Framework : Run on Multi Browser"
date: 2014-05-29 15:16:59 +0700
comments: true
categories: Selenium-Framework
---

##Multi Browser Test

###Required knowledge : [Test Script](/blog/2014/05/29/selenium-automation-framework-create-test-script/), [Page Object Model](/blog/2014/05/26/selenium-automation-framework-page-object-model/), [Modular Driven Framework](/blog/2014/05/27/selenium-automation-framework-modular-driven-framework/) , [TestNG Framework](/blog/categories/testng-framework/) 

In many case of testing , we need enable our script running on cross browser to make sure that the front-end of website is stable with multi browser.In this tutorial , you will know step by step to run script in 3 browser basic is 'Chrome' , 'IE' and 'FireFox' with this action :

Login Facebook

Post Status

####How to do it....
<!--more-->

1) Download driver for IE: [ 32 bit Windows](http://selenium-release.storage.googleapis.com/2.42/IEDriverServer_Win32_2.42.0.zip) , [ 64 bit Windows](http://selenium-release.storage.googleapis.com/2.42/IEDriverServer_x64_2.42.0.zip)

2) Download driver for [Chrome](http://chromedriver.storage.googleapis.com/index.html?path=2.9/)

3) Right click into project -> New -> folder -> name it as 'Driver'

{% img /images/mulb-1.png%}

4) Unzip and Copy 2 driver Chrome and IE to folder 'Driver'.

{% img /images/mulb-1.png%}

5) Double click on 'pom.xml' paste the configuration below the tag <dependencies> to enable maven get the Directory of project.

```
<reporting>
		<plugins>
			<!-- <plugin> -->
			<!-- <groupId>org.codehaus.sonar-plugins</groupId> -->
			<!-- <artifactId>maven-report</artifactId> -->
			<!-- <version>0.1</version> -->
			<!-- </plugin> -->
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-surefire-report-plugin</artifactId>
				<version>2.14.1</version>
				<configuration>
					<!-- <showSuccess>false</showSuccess> -->
				</configuration>
			</plugin>
		</plugins>
	</reporting>
<build>
		<extensions>
			<!-- start - for deploying using webdav -->
			<extension>
				<groupId>org.apache.maven.wagon</groupId>
				<artifactId>wagon-webdav</artifactId>
				<version>1.0-beta-2</version>
			</extension>
			<!-- end - for deploying using webdav -->
		</extensions>
		<plugins>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-resources-plugin</artifactId>
				<executions>
					<execution>
						<id>init-res</id>
						<!-- use the copy resources instead of resources, which adds it to 
							the eclipse buildpath -->
						<phase>initialize</phase>
						<goals>
							<goal>copy-resources</goal>
						</goals>
						<configuration>
							<outputDirectory>${project.basedir}/src/main/resources</outputDirectory>
							<resources>
								<resource>
									<directory>${project.basedir}/src/template/resources</directory>
									<targetPath>${project.basedir}/src/main/resources</targetPath>
									<filtering>true</filtering>
								</resource>
							</resources>
						</configuration>
					</execution>
				</executions>
			</plugin>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-surefire-plugin</artifactId>
				<version>2.7.1</version>
				<configuration>
					<argLine>-Xmx1024m -Xms1024m</argLine>
					<suiteXmlFiles>
						<suiteXmlFile>Test.xml</suiteXmlFile>
					</suiteXmlFiles>
				</configuration>
			</plugin>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.1</version>
				<configuration>
					<source>1.5</source>
					<target>1.5</target>
				</configuration>
			</plugin>
			<plugin>
				<groupId>org.codehaus.mojo</groupId>
				<artifactId>sonar-maven-plugin</artifactId>
				<version>2.1</version>
			</plugin>
		</plugins>
	</build>
```

6) After that your 'pom.xml' file will look like this :

```
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>Selenium-Automation-Framework</groupId>
	<artifactId>Selenium-Framework</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<dependencies>
		<dependency>
			<groupId>org.seleniumhq.selenium</groupId>
			<artifactId>selenium-java</artifactId>
			<version>2.41.0</version>
		</dependency>
		<dependency>
			<groupId>org.seleniumhq.selenium</groupId>
			<artifactId>selenium-server</artifactId>
			<version>2.41.0</version>
		</dependency>
		<dependency>
			<groupId>org.seleniumhq.selenium</groupId>
			<artifactId>selenium-firefox-driver</artifactId>
			<version>2.41.0</version>
		</dependency>
		<dependency>
			<groupId>org.seleniumhq.selenium</groupId>
			<artifactId>selenium-chrome-driver</artifactId>
			<version>2.41.0</version>
		</dependency>
		<dependency>
			<groupId>org.seleniumhq.selenium</groupId>
			<artifactId>selenium-remote-driver</artifactId>
			<version>2.41.0</version>
		</dependency>
		<dependency>
			<groupId>org.seleniumhq.selenium</groupId>
			<artifactId>selenium-ie-driver</artifactId>
			<version>2.41.0</version>
		</dependency>
		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<version>4.11</version>
		</dependency>
		<dependency>
			<groupId>org.apache.poi</groupId>
			<artifactId>poi</artifactId>
			<version>3.10-FINAL</version>
		</dependency>
		<dependency>
			<groupId>org.testng</groupId>
			<artifactId>testng</artifactId>
			<version>6.8.8</version>
		</dependency>
	</dependencies>
	<reporting>
		<plugins>
			<!-- <plugin> -->
			<!-- <groupId>org.codehaus.sonar-plugins</groupId> -->
			<!-- <artifactId>maven-report</artifactId> -->
			<!-- <version>0.1</version> -->
			<!-- </plugin> -->
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-surefire-report-plugin</artifactId>
				<version>2.14.1</version>
				<configuration>
					<!-- <showSuccess>false</showSuccess> -->
				</configuration>
			</plugin>
		</plugins>
	</reporting>
	<build>
		<extensions>
			<!-- start - for deploying using webdav -->
			<extension>
				<groupId>org.apache.maven.wagon</groupId>
				<artifactId>wagon-webdav</artifactId>
				<version>1.0-beta-2</version>
			</extension>
			<!-- end - for deploying using webdav -->
		</extensions>
		<plugins>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-resources-plugin</artifactId>
				<executions>
					<execution>
						<id>init-res</id>
						<!-- use the copy resources instead of resources, which adds it to 
							the eclipse buildpath -->
						<phase>initialize</phase>
						<goals>
							<goal>copy-resources</goal>
						</goals>
						<configuration>
							<outputDirectory>${project.basedir}/src/main/resources</outputDirectory>
							<resources>
								<resource>
									<directory>${project.basedir}/src/template/resources</directory>
									<targetPath>${project.basedir}/src/main/resources</targetPath>
									<filtering>true</filtering>
								</resource>
							</resources>
						</configuration>
					</execution>
				</executions>
			</plugin>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-surefire-plugin</artifactId>
				<version>2.7.1</version>
				<configuration>
					<argLine>-Xmx1024m -Xms1024m</argLine>
					<suiteXmlFiles>
						<suiteXmlFile>Test.xml</suiteXmlFile>
					</suiteXmlFiles>
				</configuration>
			</plugin>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.1</version>
				<configuration>
					<source>1.5</source>
					<target>1.5</target>
				</configuration>
			</plugin>
			<plugin>
				<groupId>org.codehaus.mojo</groupId>
				<artifactId>sonar-maven-plugin</artifactId>
				<version>2.1</version>
			</plugin>
		</plugins>
	</build>
</project>
```

7) Right click in folder 'src' -> New -> Folder -> name it as 'template'

{% img /images/mulb-3.png%}

8) Right click in folder 'template' -> New -> Folder -> name it as 'resources'

{% img /images/mulb-4.png%}

9) Right click in folder 'resources' -> New -> File -> name it as 'system.properties'

{% img /images/mulb-5.png%}

10) Open file 'system.properties' and copy the code below and paste to this file:

```
project.basedir=${project.basedir}
project.build.directory=${project.build.directory}
```

11) Right click in your project -> Run as -> Maven generate-resources. 

{% img /images/mulb-6.png%}

12) Right click in 'src/main/java' -> New -> Package -> name it as 'com.selenium.util'

{% img /images/mulb-7.png%}

13) Right click in package 'com.selenium.util' -> New -> Class -> name it as 'DriverUtil'

{% img /images/mulb-8.png%}

14) Double click on 'DriverUtil.java' and paste the below code to it.

```
package com.selenium.util;

import java.io.File;
import java.io.IOException;
import java.util.Properties;

public class DriverUtil {
	public static final String PROP_PROJECT_BASE_DIR = "project.basedir";
	public static final String FOLDER_DRIVER = "Driver";
	public static final String DEFAULT_PROPERTIES = "system.properties";
	private static Properties prod;
	
	/**
	 * @return the path of ie driver file.
	 */
	public static String getIeDriver(){
		String path = getKey(PROP_PROJECT_BASE_DIR) + File.separator + FOLDER_DRIVER 
				+ File.separator + "IEDriverServer.exe";
		try {
			File driverIe = new File(path);
			if(driverIe.exists()){
				return driverIe.getAbsolutePath();
			}
		} catch (Exception e) {
			e.printStackTrace();
			return null;
		}
		return null;	
	}
	
	/**
	 * @return the path of chrome driver file
	 */
	public static String getChromeDriver(){
		String path = getKey(PROP_PROJECT_BASE_DIR) + File.separator + FOLDER_DRIVER 
				+ File.separator + "chromedriver.exe";
		try {
			File driverChrome = new File(path);
			if(driverChrome.exists()){
				return driverChrome.getAbsolutePath();
			}
		} catch (Exception e) {
			e.printStackTrace();
			return null;
		}
		return null;	
	}
	
	/**
	 * @return load the file system.properties
	 */
	public static Properties getProperties() {
		if (prod == null) {
			prod = new Properties();
			try {
				prod.load(DriverUtil.class.getClassLoader().getResourceAsStream(DEFAULT_PROPERTIES));
			} catch (IOException e) {				
				//
			}
		}
		return prod;
	}
	
	/**
	 * @param key
	 * @return get value of key
	 */
	public static String getKey(String key) {
		Object obj = getProperties().get(key);
		String value = "";
		if (obj != null) 
			value = obj.toString();
		return value;
	}
}
```

15) Double click on 'autoTestFacebook.java' and paste the code below to it.

```
package com.selenium.test;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.openqa.selenium.ie.InternetExplorerDriver;
import org.testng.annotations.Parameters;
import org.testng.annotations.Test;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.AfterTest;

import com.selenium.pageObject.LoginPage;
import com.selenium.userAction.PostStatus;
import com.selenium.userAction.SignIn;
import com.selenium.util.DriverUtil;

public class autoTestFacebook {
	
	/**
	 * Create WebDriver as static variable
	 */
	private static WebDriver driver;
	private static String username_login;
	private static String password_login;
	private static String status_facebook;
  
  /**
 * Setup some variable to run your script test, load from the file TestNg.xml
 * Your parameters in annotation Parameters will match with define in TestNG.xml 
 */
@Parameters({"browser","status","username","password"})	
@BeforeTest
  public void beforeTest(String browser, String status, String username, String password) {
	 if(browser.equalsIgnoreCase("firefox")) {
	      driver = new FirefoxDriver();
	  }else if (browser.equalsIgnoreCase("ie")) { 
	      // Here I am setting up the path for my IEDriver
	      System.setProperty("webdriver.ie.driver", DriverUtil.getIeDriver());
	      driver = new InternetExplorerDriver();
	  }else if (browser.equalsIgnoreCase("chrome")){
		  System.setProperty("webdriver.chrome.driver", DriverUtil.getChromeDriver());
		  driver = new ChromeDriver();
	  } 
	 username_login = username;
	 status_facebook = status;
	 password_login = password;
  }
  
  /**
 * your test script call action class here
 */
@Test
  public void f() {
	  LoginPage.loadPage(driver);
	  SignIn.Execute(driver, username_login, password_login);
	  PostStatus.Execute(driver, status_facebook);
  }
  
  
  /**
 * after run your script test , use this code to close your browser
 */
@AfterTest
  public void afterTest() {
	  driver.quit();
  } 
}
```

16) Right Click in Project -> New -> File -> name it as 'TestNg.xml'

{% img /images/mulb-9.png%}

17) Copy code below and paste to 'TestNg.xml'.Remember to change the username and password in tag parameter.

```
<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE suite SYSTEM "http://testng.org/testng-1.0.dtd">

<suite name="Suite" parallel="none">

 <test name="FirefoxTest">
	 <parameter name="browser" value="firefox" />
	 <parameter name="status" value="firefox" />
	 <parameter name="username" value="yourusername" />
	 <parameter name="password" value="yourpassword" />
	 <classes>
	 <class name="com.selenium.test.autoTestFacebook" />
	 </classes>
 </test>

 <test name="IETest">
 <parameter name="username" value="yourusername" />
 <parameter name="password" value="yourpassword" />
 <parameter name="browser" value="ie" />
 <parameter name="status" value="ie" />
 <classes>
 <class name="com.selenium.test.autoTestFacebook" />
 </classes>
 </test>
 
<test name="ChromeTest">
  <parameter name="username" value="yourusername" />
 <parameter name="password" value="yourpassword" />
 <parameter name="browser" value="chrome" />
  <parameter name="status" value="chrome" />
 <classes>
 <class name="com.selenium.test.autoTestFacebook" />
 </classes>
 </test>
</suite>
```

17) Right click in file 'TestNG.xml' -> Run as -> TestNG Suite and wait for the process running.

{% img /images/mulb-10.png%}

18) Open folder 'Test-Output' -> Open folder 'Suite' - > You will see 3 file html -> open to see the report of each browser.

{% img /images/mulb-11.png%}


###Note : In this tutorial we have many knowledge so I recommend you to read the comment of code to know what it do. 