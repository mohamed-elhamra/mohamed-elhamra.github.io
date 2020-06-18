---
title: Spring MVC architecture
author: Mohamed Elhamra
date: 2020-06-20 16:00:00 +0800
categories: [Blogging, spring]
tags: [spring MVC]
---

# Introduction 

--------------------------------------

Hello everyone, in this article I will discuss the Spring web MVC, the components of this framework, their roles, the architecture as well as the request execution flow in Spring MVC application.
So please enjoy reading!

# Spring MVC components

The Spring Web MVC framework provides Model-View-Controller (MVC) architecture and a lot of ready components that can be used to develop Web applications.
In this section, we will focus mainly on the components:

## 1-Front controller

The front controller is responsible to perform pre-processing and post-processing of incoming requests.<br />
For example: <br />
* **pre-processing request:** capturing form data incoming from the client.
* **post-processing request:** retrieving data to client.<br />

In Spring Web  MVC based application we will use the `DispatcherServlet` as a front controller which is a pre-defined servlet provided by the Spring MVC module. <br />
>💡Java Servlet are programs that act as a middle layer between a request coming from a Web browser or HTTP client, and applications on the HTTP server.
