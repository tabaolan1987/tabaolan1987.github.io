---
layout: post
title: "TestNG Framework : Annotations , Groups and OnDepends"
date: 2014-05-26 11:35:51 +0700
comments: true
categories: TestNG-Framework
---

##TestNG Annotations, Groups & OnDepends

###TestNG Annotations

In the TestNG Introduction chapter we have came across different annotations used in TestNG Framework but so far we have used just three(Before, After & Test). All though these are the most frequently used annotations but who know how far you will go with your framework and may like to use other useful TestNG annotations.

Before that I would like you to give a small idea on Annotations hierarchy or Annotations levels in TestNG.

```
<suite>
 	   <test>
			 <classes>
				 	<method>
				    	  <test>
				    </method>
			 </classes>
	   </test>
</suite>
```

It says that @Test is the smallest annotation here. @Method will be executed first, before and after the execution of @Test. The same way @Class will be executed first, before and after the execution of @Method and so on.

Now with the below example it will be clear to you easily.

```
package automationFramework;
 
import org.testng.annotations.AfterClass;
import org.testng.annotations.AfterMethod;
import org.testng.annotations.AfterSuite;
import org.testng.annotations.AfterTest;
import org.testng.annotations.BeforeClass;
import org.testng.annotations.BeforeMethod;
import org.testng.annotations.BeforeSuite;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.Test;
public class Sequencing {
 
        @Test
        public void testCase1() {
            System.out.println("This is the Test Case 1");
        }
 
        @Test
        public void testCase2() {
            System.out.println("This is the Test Case 2");
        }
 
        @BeforeMethod
        public void beforeMethod() {
            System.out.println("This will execute before every Method");
        }
 
        @AfterMethod
        public void afterMethod() {
            System.out.println("This will execute after every Method");
        }
 
        @BeforeClass
        public void beforeClass() {
            System.out.println("This will execute before the Class");
        }
 
        @AfterClass
        public void afterClass() {
            System.out.println("This will execute after the Class");
        }
 
        @BeforeTest
        public void beforeTest() {
            System.out.println("This will execute before the Test");
        }
 
        @AfterTest
        public void afterTest() {
            System.out.println("This will execute after the Test");
        }
 
        @BeforeSuite
        public void beforeSuite() {
            System.out.println("This will execute before the Test Suite");
        }
 
        @AfterSuite
        public void afterSuite() {
            System.out.println("This will execute after the Test Suite");
        }
 
    }

```

Output of the above code will be like this:

{% img /images/TestNG-Annotations-1.png%}

It is clearly visible that the @Suite annotation is the very first and the very lastly executed. Then @Test followed by @Class. Now if you notice, the @Method has executed twice. As @Test is a method in the class, hence @Method will always executed for each @Test method.

###Test Case Grouping

‘Groups‘ is one more annotation of TestNG which can be used in the execution of multiple tests. Let’s say you have hundred tests of class vehicle and in it ten method of car, ten method of scooter and so on. You probably like to run all the scooter tests together in a batch. And you want all to be in a single test suite. With the help of grouping you can easily overcome this situation.

####How to do it…

1) Create two methods for Car, two methods for Scooter and one method in conjunction with Car & Sedan Car.

2) Group them separately with using  (groups = { ” Group Name” })

```
package automationFramework;

import org.testng.annotations.Test;

public class Grouping {
  @Test (groups = { "Car" })
  public void Car1() {
	  System.out.println("Batch Car - Test car 1");
  }
  @Test (groups = { "Car" })
  public void Car2() {
	  System.out.println("Batch Car - Test car 2");
  }
  @Test (groups = { "Scooter" })
  public void Scooter1() {
	  System.out.println("Batch Scooter - Test scooter 1");
  }
  @Test (groups = { "Scooter" })
  public void Scooter2() {
	  System.out.println("Batch Scooter - Test scooter 2");
  }
  @Test (groups = { "Car", "Sedan Car" })
  public void Sedan1() {
	  System.out.println("Batch Sedan Car - Test sedan 1");
  }
}

```

3) Create a testng xml like this:

```
<suite name="Suite">
    <test name="Practice Grouping">
        <groups>
	    <run>
		<include name="Car" />
	    </run>
	</groups>
	<classes>
	    <class name="automationFramework.Grouping" />
	</classes>
    </test>
</suite>

```

4) Run the test by right click on the testng.xml file and select Run As > TestNG Suite. Output will be like this in TestNg console:

{% img /images/TestNG-Grouping-1.png%}

 Note: We have just call the group ‘Car’ from the xml and it also executed the test for Sedan Car, as we have mentioned the ‘Car’ as well while declaring the group of Sedan Car.

Clubbing of groups is also possible, take a look at the below xml:

```

<suite name="Suite">
   <test name="Practice Grouping">
      <groups>
         <define name="All">
	   		 <include name="Car"/>
	   		 <include name="Scooter"/>
		 </define>
	 	<run>
	   		 <include name="All"/>
		</run>
   	 </groups>
	 <classes>
	      <class name="automationFramework.Grouping" />
	</classes>
   </test>
</suite>

```

You can see that we have created a new Group with the name ‘All’ and include other groups in it. Then simply called the newly created group for execution. The output will be like this:

{% img /images/TestNG-Grouping-2.png%}

###Dependent Test

Sometimes, you may need to invoke methods in a Test case in a particular order or you want to share some data and state between methods. This kind of dependency is supported by TestNG as it supports the declaration of explicit dependencies between test methods.

TestNG allows you to specify dependencies either with:

Using attributes dependsOnMethods in @Test annotations OR

Using attributes dependsOnGroups in @Test annotations.

Take a look over the below example:

```
package automationFramework;

import org.testng.annotations.Test;

public class Dependent {
  @Test (dependsOnMethods = { "OpenBrowser" })
  public void SignIn() {
	  System.out.println("This will execute second (SignIn)");
  }
  @Test
  public void OpenBrowser() {
	  System.out.println("This will execute first (Open Browser)");
  }
  @Test (dependsOnMethods = { "SignIn" })
  public void LogOut() {
	  System.out.println("This will execute third (Log Out)");
  }
  
```

The output will be like this:

{% img /images/TestNG-Dependent1.png%}





