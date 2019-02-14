---
layout: post
title: Remote Code execution with EL Injection Vulnerabilities
---

 **Introduction**
An expression language makes it possible to easily access application data. For example, the JSP expression language allows a page author to access a bean using simple syntax such as ${name} for a simple variable [1].

EL Injection occurs when user input is embedded in an unsafe manner. EL Injection are very serious and lead to complete compromise of the application's data and functionality and often obtain Remote Code Execution (RCE), turning every vulnerable application into a potential pivot point. Also EL Injection can be used to bypass input filters and any HttpOnly protection for application pages vulnerable to cross-site scripting (XSS) [2].


**The core problem**
To demonstrate the vulnerability. We have two test cases.

In first test case we created simple demo application running in windows environment which is vulnerable to EL injection. Whereas, in second test case we exploit a real world application running in Linux environment which is vulnerable to EL injection.

The main difference between the two test cases are

First test case help us to understand Expression language. We can see an error messages and stack trace which help us to develop our payload.

However, in second test case we demonstrate some tricks how an attacker can still develop a working payload and get remote code execution in black box if he cannot see any error message or stack trace.


 **First vulnerable Application**

Suppose the following lines of Code are found in an application.

![_config.yml]({{ site.baseurl }}/images/RCE-EL/2.PNG)
 1.  index.xhtml gets “name” parameter from the request and sends it to bingo():
 
 
![_config.yml]({{ site.baseurl }}/images/RCE-EL/3.PNG)
 2. Bing() evaluates argument dynamically and echo the value of “name” request parameter to the browser
 
 
 
 ![_config.yml]({{ site.baseurl }}/images/RCE-EL/1.PNG)
 3. Example, the get request with parameter "name=" is sent and its value is echo in page.





PDF version of white paper can be downloaded from:
[ExpressionLanguageInjection.pdf](https://www.exploit-db.com/docs/46303)
