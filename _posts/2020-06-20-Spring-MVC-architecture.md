---
title: Spring MVC architecture
author: Mohamed Elhamra
date: 2020-06-21 14:00:00 +0800
categories: [Blogging, spring]
tags: [spring MVC]
---

# Introduction 

--------------------------------------

Hello everyone, in this article I will discuss the Spring web MVC, the components of this framework, their roles, the architecture as well as the request execution flow in Spring MVC application.
So please enjoy reading!

# Spring MVC components

The **Spring Web MVC** framework provides Model-View-Controller (MVC) architecture and a lot of ready components that can be used to develop Web applications.
In this section, we will focus mainly on the components:

## 1-Front controller

The front controller is responsible to perform pre-processing and post-processing of incoming requests.<br />
For example: <br />
* **pre-processing request:** capturing form data incoming from the client.
* **post-processing request:** returning data to client.<br />

In Spring Web  MVC based application we will use the `DispatcherServlet` as a front controller which is a pre-defined servlet provided by the Spring MVC module. <br />

>💡Java Servlet are programs that act as a middle layer between a request coming from a Web browser or HTTP client, and applications on the HTTP server.

## 2.Handler mapper

The handler mapper is a pre-defined class available in Spring MVC which is responsible to identify the request handler (controller) and return details to the `DispatcherServlet`.

## 3.Controller
A controller is a class  which is responsible to handle the request, there are some pre-defined controllers available in the Spring MVC like below: <br />
* `org.springframework.web.servlet.mvc.SimpleFormController`
* `org.springframework.web.servlet.mvc.AbstractFormController`
* `org.springframework.web.servlet.mvc.multiaction.MultiActionController` etc...<br />

Also, we can define our costume controllers using the `@Controller` annotation.

## 4.Model and View

Once the request processing is completed the controller will return the `org.springframework.web.servlet.ModelAndView` object to the `DispatcherServlet`.<br />

The **model** holds data retrieved from the data source. <br />
The **view** represents a logical view name.

## 5.View resolvers

In Spring MVC we have multiple view resolver classes that implement the interface `org.springframework.web.servlet.ViewResolver` :<br />
* `org.springframework.web.servlet.view.InternalResourceViewResolver`
* `org.springframework.web.servlet.view.UrlBasedViewResolver` etc...<br />

These view resolvers are responsible to identify view files (location and extension).

## 6.View component

Responsible to render model data on view files.<br />

>💡 All the above-mentioned components (i.e. HandlerMapping, Controller, and ViewResolver) are parts of WebApplicationContext, which is an extension of the ApplicationContext with some extra features necessary for web applications.


# Request execution flow

<img src="/assets/img/sample/request-execution-flow.png" alt="drawing" width="350" height="350"/>

The Spring Web MVC framework is designed around the `DispatcherServlet`.

🔍 What happens behind the scene when an HTTP request is sent to the server: <br />

1. Incoming Http request will be received by the Dispatcher servlet, which will send request URL to the HandlerMapper.<br />

2. `HandlerMapper` will identify the appropriate request handler (controller) which is responsible to handle the request. After the `HandlerMapper` will send handler request details to `DispatcherServlet`. <br />

3. `DispatcherServlet` will call the respective Controller class method.<br />

4. Controller method will process the request and will send `ModelAndView` object to `DispatcherServlet`:
   * Model &#8594; Data
   * View  &#8594; Logical file name

5. `DispatcherServlet` will send the view name to the `ViewResolver`. <br />

6. `ViewResolver` will identify the view location & extension and sends data to `DispatcherServlet`.<br />

7. `DispatcherServlet` will give the model and view details to the view component.<br />

8. View component will render the appropriate view which holds the data model.<br />

9. `DispatcherServlet` will send back the response to the browser.<br />

# Summary 

That was all for this blog, I tried to clarify all the components of the **Spring Web MVC** and their roles as well as the request execution flow, I hope you enjoy it.<br />
Don't hesitate to share this blog whit your friends!!! 😄 😄 
  
  
  



















