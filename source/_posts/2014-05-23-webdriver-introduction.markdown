---
layout: post
title: "Webdriver : Introduction"
date: 2014-05-23 15:26:35 +0700
comments: true
categories: Webdriver
---
##Selenium Introduction

###About Selenium

Selenium is a software testing framework for the web that facilitates the automation of browsers. The Selenium project produces various tools for automation testing such as Selenium IDE, Selenium Remote Control (RC), Selenium Grid and Selenium 2.0 & WebDriver. Learning all the tools will give you many different options for approaching different automation problems. The entire suits of tools result in a rich set of testing functions specially geared to the needs of testing of web application of all types.

-- Selenium là 1 phần mềm dành cho việc tự động hóa test cái website. Selenium cung cấp cho chúng ta rất nhiều công cụ để tạo automation test như Selenium IDE (1 plugin dành cho Firefox, tự động ghi lại quá trình người sử dụng trên trang web), Selenium Remote Control (RC) , Selenium Grid và Selenium 2.0 và WebDriver. Nếu hiểu rõ tất cả các sản phẩm mà Selenium cung cấp bạn có thể hoàn thành việc tạo 1 project chạy automation test rất hữu ích.

###Why Selenium

- Selenium is an open source tool with Corporate backing. (Đây là phần mềm miễn phí)
- The tests can then be run against most modern web browsers.(Có thể chạy trên nhiều trình duyệt)
- Selenium deploys on Windows, Linux, and Macintosh platforms.(Thích ứng với các hệ điều hành OS, WINDOW, LINUX)
- It allows recording, editing, and debugging tests.(Nó cho phép bạn ghi lại , sửa chữa và chạy từng bước test)
- Recorded tests can be exported in most language e.g. html, Java, .net, perl, ruby etc. (Ghi lại các quá trình test có thể chuyển đổi sang các File Java, HTML , .net ,perl ,ruby...)
- Selenium has the support of some of the largest browser vendors who have taken (or are taking) steps to make Selenium a native part of their browser.(Selenium được sự giúp đỡ của rất nhiều các chuyên gia về trình duyệt)

###Selenium WebDriver

The primary new feature in Selenium 2.0 is the integration of the WebDriver API. WebDriver is designed to provide a simpler, more concise programming interface in addition to addressing some limitations in the Selenium-RC API. It enables you to use a programming language to write test scripts in different programming languages like html, Java, .net , perl, ruby and which enables you to use conditional operations, looping and other programming concepts which makes you test script robust. Selenium-WebDriver was developed to better support dynamic web pages where elements of a page may change without the page itself being reloaded. WebDriver’s goal is to supply a well-designed object-oriented API that provides improved support for modern advanced web-app testing problems.

-- WebDriver là 1 ứng dụng mới của Selenium phiên bản 2.0 , nó được thiết kế đơn giản hơn , ngắn gọn cho việc lập trình và giải quyết được một số vấn đề hạn chế của Selenium RC- API. Nó cho phép bạn viết code bằng rất nhiều ngôn ngữ như html , java, .net , perl, ruby .Nó cho phép bạn dùng những điều kiện , vòng lặp , và một số trường hợp khác để bạn tạo ra code dễ dàng.Selenium Webdriver được phát triển để hỗ trợ nhiều trình duyệt nơi mà các đối tượng trong page có thể thay đổi khi mà reload.